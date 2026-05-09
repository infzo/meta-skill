---
name: collect-skills
description: 从 skillhub.cn 收集热门 Skill 定义，存储到项目中供后续分析
trigger: /collect-skills
---

## 目标

从 skillhub.cn（中国用户优化的 Skills 社区）收集当前热门、使用量高的 Skill，存储到项目中供后续分析和学习。

## 输入

- 无特定前置条件
- 可选：用户指定收集数量（默认 10 个）

## 执行步骤

### 1. 导航到 skillhub.cn

使用 MCP agent-browser 工具导航到目标网站：

```
调用: mcp__agent-browser__browser_navigate
参数: url = "https://skillhub.cn"
等待: waitUntil = "networkidle"
```

确认页面加载完成，验证 URL 正确。

### 2. 获取 Skill 列表

使用快照工具获取页面结构：

```
调用: mcp__agent-browser__browser_snapshot
参数: interactive = true (仅获取可交互元素)
```

解析页面结构，定位：
- Skill 列表容器
- 单个 Skill 条目的选择器
- 排序/筛选控件（如"按使用量排序"）

### 3. 按"使用量"排序

如果存在排序选项：

```
调用: mcp__agent-browser__browser_click
参数: ref = 排序按钮的 ref (如 @e5)
```

选择"按使用量排序"或"最热门"选项。

### 4. 遍历 Skill 列表

获取前 10 个 Skill 的链接：

```
调用: mcp__agent-browser__browser_evaluate
参数: code = "Array.from(document.querySelectorAll('Skill条目选择器')).slice(0, 10).map(el => el.href)"
```

将结果存储到变量 `skill_urls` 列表中。

### 5. 逐个访问 Skill 详情页

对于每个 URL，循环执行：

**5.1 导航到详情页**
```
调用: mcp__agent-browser__browser_navigate
参数: url = skill_urls[i]
```

**5.2 获取 Skill 详情**
```
调用: mcp__agent-browser__browser_snapshot
参数: compact = true (精简输出)
```

**5.3 提取关键信息**
- Skill 名称
- 作者信息
- 使用次数/热度
- Skill 原始定义（触发词、描述、执行步骤等）
- 标签/分类

使用 `browser_get` 工具提取特定字段：
```
调用: mcp__agent-browser__browser_get
参数: property = "text", ref = 内容区域 ref
```

**5.4 返回列表页**
```
调用: mcp__agent-browser__browser_back
```

### 6. 存储 Skill 文件

每个 Skill 存储为独立的 Markdown 文件。

**文件路径：** `data/collected/{sanitized_name}.md`

**文件格式：**
```markdown
---
name: {skill_name}
source: skillhub.cn
url: {original_url}
collected_date: {YYYY-MM-DD}
usage_count: {使用次数}
---

{Skill 原始定义内容}

---

## 收集说明

- 收集时间：{完整时间戳}
- 数据来源：skillhub.cn 详情页
- 原作者：{作者信息}
```

### 7. 更新收集索引

创建/更新 `data/collected/index.md`：

```markdown
---
title: 已收集 Skills 索引
updated: {YYYY-MM-DD}
---

| 名称 | 来源 | 使用量 | 收集日期 | 文件 |
|------|------|--------|----------|------|
| {name} | skillhub.cn | {count} | {date} | [{name}.md]({name}.md) |
...
```

## 输出

- `data/collected/*.md`：收集的 Skill 文件（最多 10 个）
- `data/collected/index.md`：收集清单索引

## 错误处理

### 网站访问失败

如果导航失败：
1. 重试最多 3 次，每次间隔 2 秒
2. 如果仍失败，记录错误并跳过当前 Skill
3. 继续处理下一个 Skill

### 页面结构变化

如果无法定位元素：
1. 使用 `browser_screenshot` 截图当前页面
2. 保存截图到 `logs/collect-skills-errors/`
3. 记录错误信息到 `logs/collect-skills-errors/error.log`
4. 尝试使用备用选择器或手动提示用户

### 内容提取失败

如果 Skill 定义内容为空：
1. 尝试使用不同的提取策略（CSS 选择器、正则表达式等）
2. 如果内容仍为空，记录为 "内容获取失败" 并继续
3. 在索引中标记为 "不完整"

### 浏览器崩溃

如果浏览器无响应：
1. 调用 `browser_close` 关闭当前会话
2. 重新初始化浏览器
3. 从中断点继续（使用已收集的 URL 列表）

## 限制条件

- **数量限制：** 最多收集前 10 个热门 Skill（按使用量排序）
- **时间限制：** 每个 Skill 详情页停留不超过 30 秒
- **并发限制：** 顺序访问，不并发打开多个页面
- **存储限制：** 跳过已收集的 Skill（通过 URL 比对）

## 注意事项

- 尊重 skillhub.cn 的 robots.txt 和访问频率限制
- 每次请求间隔 1-2 秒，避免对服务器造成压力
- 保留原始内容的完整性，不修改 Skill 定义
- 标注来源 URL，便于后续追溯和验证
- 收集后人工复核，确认内容准确性
