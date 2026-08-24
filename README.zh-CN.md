# How to Make Application

[English](README.md)

一套面向个人独立开发者、供 Codex 使用的轻量级规格驱动开发（SDD）Skill。

它帮助开发者把一个想法或现有代码库，逐步变成由一个人也能理解、实现、验证、发布并持续接手的产品。文档在这里是约束决策和保存证据的控制系统，而不是为了流程而写的材料。

## 这套 Skill 解决什么问题

- 把 App 想法收敛为明确的产品简报和最小完整版本。
- 建立代码、规格、交接、验收和发布事实之间的真相优先级。
- 在实现前明确目标、非目标、不变量、状态、失败语义、预算和停止条件。
- 将重要功能与重构拆成可独立验证、可回滚的纵向切片。
- 通过症状、证据、分层根因和已排除假设诊断复杂问题。
- 验证用户真正拿到的生产产物，而不是把“编译成功”误认为“可以发布”。
- 精确记录当前工作、人工验收和公开版本历史，让未来会话可以直接继续。

这套 Skill 面向有一定复杂度的软件工作，不会把整套流程强加到单一知识问答或微小修改上。

## 工作模式

| 模式 | 产出 |
|---|---|
| Shape | 产品简报、约束、风险和第一个可测试版本 |
| Bootstrap | App 骨架、最小文档系统、开发闭环和首个纵向切片 |
| Build | 按聚焦的执行规格实现已确认功能 |
| Evolve | 在保持明确不变量的前提下演进架构或行为 |
| Diagnose | 症状、证据、分层根因、排除项和可验证的修复路径 |
| Release | 验证特定产物，并且只在明确授权后发布 |
| Resume | 恢复真实基线并继续下一个未阻塞切片 |

## 文档系统

这套方法按“每份文档拥有什么事实”划分职责：

| 文档 | 负责 | 不得声称 |
|---|---|---|
| 长期项目规则 | 产品、工程、隐私和发布的长期约束 | 临时进度 |
| 产品或执行规格 | 计划、边界、决策、阶段和验收设计 | 已经实现或发布 |
| 实施报告 | 实际落地内容和验证证据 | 把未来范围写成已完成 |
| Handoff | 当前工作区、证据、风险和准确下一步 | 无止境的流水账 |
| 版本历史 | 已验证的公开版本身份和撤回记录 | 把候选包或内部 Build 写成正式发布 |
| 验收记录 | 人工观察的产品、视觉、交互、硬件或辅助功能结果 | 把未观察结果写成通过 |

发生冲突时，默认优先级为：用户当前指令、当前生产事实、已验证发布产物、当前 Handoff、已确认规格，最后才是外部参考和通用惯例。

## 安装

可以直接让 Codex 从下面的仓库安装：

```text
https://github.com/Duoasa/how-to-make-application
```

也可以手动安装：

```bash
git clone https://github.com/Duoasa/how-to-make-application.git ~/.codex/skills/how-to-make-application
```

仓库根目录就是 Skill 根目录，`SKILL.md`、`agents/` 和 `references/` 保持 Codex 所需的结构。

## 使用

使用 `$how-to-make-application` 显式调用，例如：

```text
使用 $how-to-make-application，把这个 App 想法整理为聚焦的首发版本计划。
```

```text
使用 $how-to-make-application，检查这个现有仓库，确认真实基线，并为下一个功能编写执行规格。
```

```text
使用 $how-to-make-application，验证这个发布候选包、记录证据并准备准确的 Handoff，暂时不要发布。
```

这套 Skill 不会扩大正常授权边界。规格或发布计划不等于获得了发布、破坏性迁移、付费服务、秘密信息访问或无关外部修改的权限。

## 真实落地案例：QuotaView

这套 Skill 提炼自 [QuotaView](https://github.com/Duoasa/QuotaView) 实际采用的 SDD 系统。QuotaView 是一款原生 macOS 应用，经历了产品、架构、UI 稳定性、打包和正式发布的连续迭代。

公开项目展示了这套 Skill 使用的文档分工：

- [AGENTS.md](https://github.com/Duoasa/QuotaView/blob/main/AGENTS.md) 负责长期产品、设计、实现和发布约束。
- [核心架构执行规格](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-architecture-evolution.md) 记录目标、非目标、不变量、目标架构、分阶段实施、质量门禁、ADR 和停止条件。
- [WidgetKit 专项规格](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-widgetkit-solution.md) 展示如何为独立子系统收窄职责、数据流、隐私边界、失败模式、预算和验收范围。
- [底层重构实施报告](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-refactor-0.2.0-report.md) 将实际落地事实和自动化证据，与仍等待产品所有者完成的验收明确分开。
- [HANDOFF.md](https://github.com/Duoasa/QuotaView/blob/main/HANDOFF.md) 记录当前生产基线、开发状态、验证、工作区边界和发布门禁。
- [VERSION_HISTORY.md](https://github.com/Duoasa/QuotaView/blob/main/VERSION_HISTORY.md) 记录公开版本身份、产物、验证和撤回历史，不把内部 Build 写成发布事实。

Skill 复用的是工作方法，而不是 QuotaView 的 macOS 技术栈、视觉体系、产品范围或项目私有约束。

## 仓库结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── document-system.md
│   ├── execution-playbook.md
│   ├── quality-and-release.md
│   └── templates.md
├── README.md
└── README.zh-CN.md
```

入口文件保持紧凑；Codex 只会在当前任务需要时继续读取对应参考文档。

## 核心原则

1. 先确认现实，再做计划。
2. 分开长期规则、计划意图、当前工作、发布事实和人工验收。
3. 先定义不变量和失败语义，再选择架构。
4. 用可回滚、可独立验证的切片实现软件。
5. 根据风险提供相称的验证证据。
6. 不把提案写成已实现，不把候选包写成已发布，不把未观察结果写成已通过。
