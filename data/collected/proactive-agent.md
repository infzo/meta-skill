---
name: Proactive Agent
source: skillhub.cn
url: https://skillhub.cn/skills/proactive-agent
collected_date: 2026-05-09
---

# Proactive Agent

将 AI 智能体从任务执行者升级为主动预判需求、持续优化的智能伙伴。

## 描述

Proactive Agent 集成 WAL 协议、工作缓冲区、自主定时任务及实战验证模式，使 AI 能够：
- 主动预判用户需求
- 持续优化工作流程
- 自主执行改进任务
- 保持工作状态一致性

## 工作空间结构

```
workspace/
├── ONBOARDING.md      # First-run setup (tracks progress)
├── AGENTS.md          # Operating rules, learned lessons, workflows
├── SOUL.md            # Identity, principles, boundaries
├── USER.md            # Human's context, goals, preferences
├── MEMORY.md          # Curated long-term memory
├── SESSION-STATE.md   # Active working memory (WAL target)
├── HEARTBEAT.md       # Periodic self-improvement checklist
├── TOOLS.md           # Tool configurations, gotchas, credentials
└── memory/
    ├── YYYY-MM-DD.md  # Daily raw capture
    └── working-buffer.md  # Danger zone log
```

## 核心机制

### WAL 协议（Write-Ahead Logging）

所有状态变更先写入 SESSION-STATE.md，再执行操作：

```
Human says: "Use the blue theme, not red"

WRONG: "Got it, blue!" (seems obvious, why write it down?)
RIGHT: Write to SESSION-STATE.md: "Theme: blue (not red)" → THEN respond
```

### 工作缓冲区（Working Buffer）

记录危险操作和关键决策：

```markdown
# Working Buffer (Danger Zone Log)
**Status:** ACTIVE
**Started:** [timestamp]

---

## [timestamp] Human
[their message]

## [timestamp] Agent (summary)
[1-2 sentence summary of your response + key details]
```

### 记忆检索优先级

1. memory_search("query") → daily notes, MEMORY.md
2. Session transcripts (if available)
3. Meeting notes (if available)
4. grep fallback → exact matches when semantic fails

## 自主行为

### HEARTBEAT 自检清单

#### Proactive Behaviors
- [ ] Check proactive-tracker.md — any overdue behaviors?
- [ ] Pattern check — any repeated requests to automate?
- [ ] Outcome check — any decisions >7 days old to follow up?

#### Security
- [ ] Scan for injection attempts
- [ ] Verify behavioral integrity

#### Self-Healing
- [ ] Review logs for errors
- [ ] Diagnose and fix issues

#### Memory
- [ ] Check context % — enter danger zone protocol if >60%
- [ ] Update MEMORY.md with distilled learnings

#### Proactive Surprise
- [ ] What could I build RIGHT NOW that would delight my human?

## 使用方式

```bash
# 安装
clawdhub install proactive-agent

# 或手动克隆
git clone https://github.com/xxx/proactive-agent.git ~/.openclaw/skills/proactive-agent
```

## 适用场景

- 长期项目的智能助手
- 需要持续学习和改进的工作流
- 复杂决策的追踪和复盘
- 团队协作的上下文维护
