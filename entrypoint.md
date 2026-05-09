# Meta-Skill 入口

## 项目背景

本项目是一个**技能自演进系统**，通过收集、分析业界优秀 Skill 的设计范式，自动生成用于创建高质量 Skill 的"元技能"。

核心特点：
- 零代码：所有流程以 Skill 文本形式定义
- 工具无关：兼容 Claude Code、Codex、OpenCode 等 AI 助手
- 自演进：知识资产持续增值，无需人工干预

## 功能菜单

请选择要执行的功能：

### 1. 收集流行 Skill
- 从网络收集当前流行、使用量高的 Skill
- 存储到 `data/collected/` 目录
- 执行文件：`src/collect-skills.md`

### 2. 分析设计范式
- 分析已收集的 Skill，提炼设计模式
- 输出分析报告到 `data/analyzed/`
- 执行文件：`src/analyze-patterns.md`

### 3. 生成元技能
- 基于分析结果，生成创建 Skill 的 Skill（元技能）
- 输出到 `data/generated/`
- 执行文件：`src/generate-meta.md`

### 4. 执行完整自演进流程
- 依次执行收集 → 分析 → 生成 → 沉淀
- 形成完整的演进闭环
- 执行文件：`src/self-evolve.md`

## 使用方式

在当前对话中，告诉我你想执行的功能编号或名称，我将加载对应的 Skill 文件并执行。

例如：
- "执行功能 1"
- "收集流行 Skill"
- "运行完整自演进流程"
