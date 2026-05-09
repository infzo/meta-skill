---
name: collect-skills
description: 收集网络上流行的 Skill
trigger: /collect-skills
---

## 目标

从网络上收集当前流行、使用量高的 Skill，存储到项目中供后续分析。

## 输入

- 无特定前置条件
- 可选：用户指定收集范围（如特定领域、特定平台）

## 执行步骤

1. **确定收集渠道**
   - GitHub 仓库（搜索 skill-related 项目）
   - 官方文档/社区（Claude Code Skills、OpenAI Codex Skills 等）
   - 社交媒体/技术博客（讨论热度高的 Skill）

2. **筛选标准**
   - 使用量/下载量
   - 社区讨论热度
   - 实际应用案例数量
   - 设计质量（可复用性、通用性）

3. **收集内容**
   - Skill 定义文件（原始文本）
   - 元信息（来源、作者、使用量等）
   - 相关讨论/评价

4. **存储格式**
   - 每个 Skill 存为一个 Markdown 文件
   - 文件命名：`{来源}-{skill名称}.md`
   - 存放位置：`data/collected/`
   - 包含元信息 frontmatter

## 输出

- `data/collected/*.md`：收集的 Skill 文件
- `data/collected/index.md`：收集清单索引

## 注意事项

- 尊重原作者版权，保留来源信息
- 收集数量适中，避免信息过载（建议每次 10-20 个）
- 优先收集有实际应用验证的 Skill