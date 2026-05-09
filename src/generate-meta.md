---
name: generate-meta
description: 基于分析结果生成元技能模板
trigger: /generate-meta
---

## 目标

基于 `data/analyzed/` 中的范式分析结果，生成用于创建高质量 Skill 的"元技能"模板。

## 输入

- 前置条件：已执行 `analyze-patterns`，有范式分析结果
- 数据来源：`data/analyzed/pattern-summary.md`

## 执行步骤

1. **读取分析结果**
   - 理解已提炼的设计范式
   - 识别关键最佳实践

2. **设计元技能结构**
   - 定义元技能的目标：帮助用户快速创建高质量 Skill
   - 设计交互流程：用户输入 → 元技能输出 Skill
   - 确定输出格式：符合本项目的 Skill 模板

3. **编写元技能内容**
   - 包含 Skill 创建流程指导
   - 集成设计范式作为模板选项
   - 提供质量检查清单

4. **验证元技能**
   - 模拟使用元技能创建一个测试 Skill
   - 检查生成质量

5. **输出元技能**
   - 存储为可执行的 Skill 文件

## 输出

- `data/generated/meta-skill-template.md`：元技能 Skill 文件
- `data/generated/skill-quality-checklist.md`：Skill 质量检查清单

## 注意事项

- 元技能应足够通用，不局限于特定领域
- 提供多种模板选项，而非单一固定模板
- 强调可维护性和可演进性