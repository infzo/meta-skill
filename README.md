# Meta-Skill

## 项目定位

Meta-Skill 是一个**技能自演进系统**，旨在通过分析和学习业界优秀 Skill 的设计范式，自动生成用于创建高质量 Skill 的"元技能"。

核心理念：**以 Skill 造 Skill，以经验生经验**。

## 项目使命

```
收集流行 Skill → 分析设计范式 → 提炼最佳实践 → 输出元技能 → 持续演进
```

## 项目特点

### 1. 零代码项目
- 所有经验、流程、知识均以**文本形式固化**（Skill 文件、Markdown 等）
- 无需编写 Agent 代码
- 直接使用 Claude Code、Codex、OpenCode 等现有 AI 工具加载 Skill 执行
- 知识资产可读、可追溯、可版本控制

### 2. AI 工具驱动
- 通过 Claude Code / Codex / OpenCode 等工具加载项目中的 Skill 文件执行任务
- 无 Agent 代码开发成本，只需维护 Skill 文本定义
- 利用现有 AI 工具的能力，专注知识沉淀而非工程实现
- 不绑定特定工具，兼容多种 AI 助手

### 3. 趋势分析输出
- 追踪业界 Skill 的流行度与使用量
- 分析 Skill 设计范式的演变趋势
- 输出行业洞察报告

### 4. 自演进能力
- 从 Skill 分析 → 元技能输出形成闭环
- 每轮迭代提升元技能质量
- **全流程无人为干预**，知识资产持续增值

## 项目结构

```
meta-skill/
├── README.md              # 项目说明 + 启动指引
├── entrypoint.md          # 统一入口 + 引导菜单
├── src/                   # 执行"代码"（Skill 文件）
│   ├── collect-skills.md
│   ├── analyze-patterns.md
│   ├── generate-meta.md
│   └── self-evolve.md
├── data/                  # 数据存储
│   ├── collected/         # 收集的 Skill 源文件
│   ├── analyzed/          # 分析结果
│   └── generated/         # 生成的元技能
├── docs/                  # 文档
│   ├── design-principles.md
│   └── trend-analysis.md
└── memory/                # 知识记忆库
```

## 快速开始

在项目根目录下，向 AI 助手发送以下指令：

```
请阅读 entrypoint.md 文件，了解项目背景后，按照其中的引导选择并执行相应的 Skill
```

## 核心产出

1. **Skill 设计范式库**：沉淀优秀 Skill 的设计模式
2. **元技能模板**：用于快速创建高质量 Skill 的 Skill 文件
3. **趋势报告**：定期发布 Skill 发展趋势分析
4. **自演进系统**：可持续自我优化的知识生产流水线

## 适用场景

- 希望学习如何设计优秀 Skill 的开发者
- 需要批量创建标准化 Skill 的团队
- 关注 AI Agent 技能发展的研究者
- 追求知识资产自动化沉淀的组织

## 许可证

MIT License

---

> "The skill to create skills is the ultimate skill."
