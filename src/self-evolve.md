---
name: self-evolve
description: 执行完整的自演进流程
trigger: /self-evolve
---

## 目标

依次执行收集 → 分析 → 生成 → 沉淀，形成完整的演进闭环。

## 输入

- 无特定前置条件
- 可选：指定演进轮次编号

## 执行步骤

1. **收集阶段**
   - 加载并执行 `src/collect-skills.md`
   - 等待收集完成，确认输出

2. **分析阶段**
   - 加载并执行 `src/analyze-patterns.md`
   - 等待分析完成，确认输出

3. **生成阶段**
   - 加载并执行 `src/generate-meta.md`
   - 等待生成完成，确认输出

4. **沉淀阶段**
   - 更新 `docs/design-principles.md`（整合新发现）
   - 更新 `docs/trend-analysis.md`（如有趋势变化）
   - 在 `memory/` 中记录本轮演进摘要

5. **汇报总结**
   - 输出本轮演进的关键发现
   - 说明新增/更新的知识资产
   - 标记待改进点

## 输出

- 所有阶段的中间输出（见各 Skill 定义）
- `memory/evolution-log-{日期}.md`：本轮演进日志
- 更新的 `docs/` 文档

## 注意事项

- 每个阶段完成后确认输出再继续下一阶段
- 记录遇到的异常或特殊情况
- 保持演进日志简洁但有价值
- 演进后可继续下一轮，形成持续循环