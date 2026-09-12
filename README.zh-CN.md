<h1 align="center">How to Make Application</h1>

<p align="center">
  用一套轻量、规格驱动的方法，独立完成软件的规划、开发、验证与发布。
</p>

<p align="center">
  <img alt="可移植 Agent Skill" src="https://img.shields.io/badge/Agent%20Skill-Portable-6F42C1">
  <img alt="规格驱动开发" src="https://img.shields.io/badge/Workflow-Spec--Driven-0969DA">
  <img alt="兼容 Codex" src="https://img.shields.io/badge/Codex-Compatible-111111">
  <img alt="兼容 Claude Code" src="https://img.shields.io/badge/Claude%20Code-Compatible-D97757">
  <img alt="兼容 DeepSeek Harness" src="https://img.shields.io/badge/DeepSeek%20Harness-Compatible-4D6BFE">
</p>

<p align="center">
  <a href="#快速开始"><strong>快速开始</strong></a>
  ·
  <a href="#agent-兼容性">兼容性</a>
  ·
  <a href="#工作方法">工作方法</a>
  ·
  <a href="#真实项目验证quotaview">落地案例</a>
</p>

<p align="center">
  <a href="README.md">English</a> · <strong>简体中文</strong>
</p>

`How to Make Application` 是一套可移植的 Agent Skill，用来把一个 App 想法或现有代码库，变成一个人也能理解、实现、验证、发布并持续接手的产品。

它把文档当作约束决策、保存证据的控制系统，而不是为了流程而写的材料。面对复杂软件工作时，它会建立必要的结构；面对单一问答或微小修改时，它不会强行套用完整流程。

## 按任务加载与完成

按请求选择上下文和完成标准：局部修复直接定位所属代码或规格；文档整理
查阅文档体系；发布才读取发布门禁。这些是条件路由，不要求每次走完整生命周期。
已授权实施的任务持续完成实现和必要验证，不因先写了规格再重复请求实施确认。
公开稳定产物与开发最新版单独定位；验证随改动风险选择，人工验收和外部发布
保留各自的真实授权边界。

## 为什么需要这套 Skill

| | |
| --- | --- |
| **确定正确的首发范围** | 把想法收敛为聚焦的产品简报、明确约束，以及值得测试的最小完整版本。 |
| **保护产品事实** | 将计划意图、当前实现、人工验收和公开发布事实保存在职责清晰的不同记录中。 |
| **用安全切片推进** | 把重要功能和重构拆成可回滚、可独立验证的纵向切片。 |
| **用证据诊断问题** | 保存症状、观察、排除项、分层原因和系统不变量，而不是直接猜测修复方案。 |
| **验证真正交付的产物** | 检查生产产物和发布身份，不把“编译成功”误认为“已经具备发布质量”。 |
| **让后续工作直接继续** | 留下准确基线、未解决风险和下一步，使未来会话不必重新考古。 |

## 快速开始

根据使用的 Agent，把仓库克隆到对应的个人 Skill 目录：

```bash
# Codex
mkdir -p ~/.codex/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.codex/skills/how-to-make-application

# Claude Code
mkdir -p ~/.claude/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.claude/skills/how-to-make-application

# DeepSeek Harness
mkdir -p ~/.dsh/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.dsh/skills/how-to-make-application
```

然后用真实任务显式调用：

```text
Codex:            使用 $how-to-make-application，把这个 App 想法整理为聚焦的首发版本。
Claude Code:      /how-to-make-application 把这个 App 想法整理为聚焦的首发版本。
DeepSeek Harness: /how-to-make-application 把这个 App 想法整理为聚焦的首发版本。
```

仓库根目录就是 Skill 根目录。所有已支持 Agent 都读取同一份权威 [`SKILL.md`](SKILL.md) 和同一组按需参考文件。

## Agent 兼容性

| Agent | 支持状态 | 个人发现路径 | 显式调用 | 详细说明 |
| --- | --- | --- | --- | --- |
| Codex | 原生 | `~/.codex/skills/how-to-make-application/` | `$how-to-make-application` | [`agents/openai.yaml`](agents/openai.yaml) |
| Claude Code | 原生 Agent Skill | `~/.claude/skills/how-to-make-application/` | `/how-to-make-application` | [适配说明](adapters/claude-code.md) |
| DeepSeek Harness | 原生 Skill，开发者预览 | `~/.dsh/skills/how-to-make-application/` | `/how-to-make-application` | [适配说明](adapters/deepseek-harness.md) |

如果希望让 Skill 随项目仓库共同维护，可以安装到 `.claude/skills/` 或 `.dsh/skills/`。DeepSeek Harness 也会扫描个人和项目的 `.agents/skills/` 目录。对应适配说明包含项目安装、更新、调用和验证细节。

Agent 专属元数据不会替代权威工作流。适配层只改变发现和调用方式，不会自动获得额外工具、权限、发布授权、付费服务访问权或秘密信息访问权。

## 工作方法

<p align="center">
  <strong>现实 → 规格 → 切片 → 证据 → 发布 → 交接</strong>
</p>

Skill 会根据当前任务选择足够且最小的工作模式：

| 模式 | 产出 |
| --- | --- |
| **Shape** | 产品简报、约束、风险和第一个可测试版本 |
| **Bootstrap** | App 骨架、最小文档系统、开发闭环和首个纵向切片 |
| **Build** | 按聚焦的执行规格实现已确认功能 |
| **Evolve** | 在保持明确不变量的前提下演进架构或行为 |
| **Diagnose** | 症状、证据、分层原因、排除项和可验证的修复路径 |
| **Release** | 验证特定产物，并且只在明确授权后发布 |
| **Resume** | 恢复真实基线并继续下一个未阻塞切片 |

### 核心原则

1. 先确认现实，再做计划。
2. 分开长期规则、计划意图、当前工作、发布事实和人工验收。
3. 先定义不变量和失败语义，再选择架构。
4. 用可回滚、可独立验证的切片实现软件。
5. 根据风险提供相称的验证证据。
6. 不把提案写成已实现，不把候选包写成已发布，不把未观察结果写成已通过。

## 文档系统

每份文档只负责一种事实：

| 文档 | 负责 | 不得声称 |
| --- | --- | --- |
| **长期项目规则** | 产品、工程、隐私和发布的长期约束 | 临时进度 |
| **产品或执行规格** | 计划、边界、决策、阶段和验收设计 | 已经实现或发布 |
| **实施报告** | 实际落地内容和验证证据 | 把未来范围写成已完成 |
| **Handoff** | 当前工作区、证据、风险和准确下一步 | 无止境的项目流水账 |
| **版本历史** | 已验证的公开版本身份和撤回记录 | 把候选包或内部 Build 写成正式发布 |
| **验收记录** | 人工观察的产品、视觉、交互、硬件或辅助功能结果 | 把未观察结果写成通过 |

发生冲突时，默认优先级为：用户当前指令、当前生产事实、已验证发布产物、当前 Handoff、已确认规格，最后才是外部参考和通用惯例。

## 使用示例

### 开始一个新 App

```text
使用 how-to-make-application Skill，把这个想法整理成产品简报，定义最小完整
版本，并找出第一个可以端到端验证的纵向切片。
```

### 演进现有代码库

```text
使用 how-to-make-application Skill，检查这个仓库，确认真实基线，并为下一项
功能编写执行规格。
```

### 准备发布但暂不推送

```text
使用 how-to-make-application Skill，验证这个发布候选包、记录证据并准备准确的
Handoff，暂时不要发布。
```

## 真实项目验证：QuotaView

这套 Skill 提炼自 [QuotaView](https://github.com/Duoasa/QuotaView) 实际采用的 SDD 系统。QuotaView 是一款原生 macOS 应用，经历了产品、架构、UI 稳定性、打包和正式发布的连续迭代。

| 公开文档 | 验证内容 |
| --- | --- |
| [长期项目规则](https://github.com/Duoasa/QuotaView/blob/main/AGENTS.md) | 长期产品、设计、实现、隐私和发布约束 |
| [核心架构执行规格](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-architecture-evolution.md) | 目标、非目标、不变量、目标架构、阶段、质量门禁、ADR 和停止条件 |
| [WidgetKit 专项规格](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-widgetkit-solution.md) | 子系统职责、数据流、隐私边界、失败模式、预算和验收范围 |
| [实施报告](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-refactor-0.2.0-report.md) | 实际交付事实和自动化证据，与等待人工验收的内容明确分开 |
| [当前 Handoff](https://github.com/Duoasa/QuotaView/blob/main/HANDOFF.md) | 生产基线、当前工作、验证、工作区边界和发布门禁 |
| [版本历史](https://github.com/Duoasa/QuotaView/blob/main/VERSION_HISTORY.md) | 公开版本身份、产物、验证和撤回历史 |

Skill 复用的是工作方法，而不是 QuotaView 的 macOS 技术栈、视觉体系、产品范围或项目专属约束。

## 仓库结构

```text
.
├── SKILL.md                    # 可移植工作流入口
├── agents/
│   └── openai.yaml            # Codex UI 元数据
├── adapters/
│   ├── claude-code.md          # Claude Code 发现与调用说明
│   └── deepseek-harness.md     # DeepSeek Harness 发现与调用说明
├── references/
│   ├── document-system.md      # 真相源模型
│   ├── execution-playbook.md   # 工作模式与执行指南
│   ├── quality-and-release.md  # 验证、发布与交接门禁
│   └── templates.md            # 可复用文档模板
├── README.md                   # English documentation
└── README.zh-CN.md             # 简体中文文档
```

入口文件保持紧凑；Agent 只会在当前任务需要时加载对应参考文件。

## 反馈与贡献

欢迎通过 [GitHub Issues](https://github.com/Duoasa/how-to-make-application/issues) 提交问题、兼容性报告、文档改进和聚焦的 Pull Request。
