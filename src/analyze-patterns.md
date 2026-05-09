---
name: analyze-patterns
description: 分析已收集 Skill 的设计范式
trigger: /analyze-patterns
---

## 目标

分析 `data/collected/` 目录下的 Skill，提炼设计模式和最佳实践。

## 输入

- 前置条件：已执行 `collect-skills`，有 Skill 待分析
- 可选：指定分析范围（特定 Skill 或特定类别）

## 执行步骤

1. **读取 Skill 文件**
   - 遍历 `data/collected/` 目录
   - 解析每个 Skill 的结构和内容

2. **结构分析**
   - Skill 文件组织方式（frontmatter、章节划分）
   - 命名规范（文件名、变量名）
   - 触发方式定义

3. **内容分析**
   - 目标描述方式
   - 执行步骤设计（粒度、顺序）
   - 输入输出定义
   - 异常处理方式

4. **范式提炼**
   - 识别共性设计模式
   - 标记创新点
   - 总结优劣

5. **输出报告**
   - 按范式类型分类总结
   - 提供具体 Skill 案例支撑
   - 给出改进建议

## 输出

- `data/analyzed/pattern-summary.md`：范式总结报告
- `data/analyzed/{skill名称}-analysis.md`：单个 Skill 详细分析（可选）
- 更新 `docs/design-principles.md`（如有新发现）

## 注意事项

- 避免主观偏见，基于实际案例分析
- 关注"为什么"而非仅"是什么"
- 模式命名简洁且易理解