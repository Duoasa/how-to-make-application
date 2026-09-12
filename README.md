<h1 align="center">How to Make Application</h1>

<p align="center">
  Build software as a solo developer with a lightweight, specification-driven system.
</p>

<p align="center">
  <img alt="Portable Agent Skill" src="https://img.shields.io/badge/Agent%20Skill-Portable-6F42C1">
  <img alt="Specification-driven development" src="https://img.shields.io/badge/Workflow-Spec--Driven-0969DA">
  <img alt="Codex compatible" src="https://img.shields.io/badge/Codex-Compatible-111111">
  <img alt="Claude Code compatible" src="https://img.shields.io/badge/Claude%20Code-Compatible-D97757">
  <img alt="DeepSeek Harness compatible" src="https://img.shields.io/badge/DeepSeek%20Harness-Compatible-4D6BFE">
</p>

<p align="center">
  <a href="#quick-start"><strong>Quick start</strong></a>
  ·
  <a href="#agent-compatibility">Compatibility</a>
  ·
  <a href="#how-it-works">How it works</a>
  ·
  <a href="#real-world-proof-quotaview">Case study</a>
</p>

<p align="center">
  <strong>English</strong> · <a href="README.zh-CN.md">简体中文</a>
</p>

`How to Make Application` is a portable Agent Skill for turning an app idea—or an existing codebase—into a product that one person can understand, implement, verify, release, and resume.

It treats documentation as a control system for decisions and evidence, not as paperwork. The workflow scales up for substantial application work and stays out of the way for isolated questions or trivial edits.

## Task-sized context and completion

Use the request to choose the context and completion target. Routine fixes go
directly to the owning code or spec; document cleanup reads the document-system
reference; release work reads release gates. These are conditional routes, not a
mandatory lifecycle. Already-authorized implementation continues through relevant
verification without a second approval just because a specification was written.
The public stable artifact and the latest development workspace remain separate.
Checks scale with the change; human acceptance and external publication retain
their actual ownership and authorization boundaries.

## Why this skill

| | |
| --- | --- |
| **Shape the right release** | Turn an idea into a focused product brief, explicit constraints, and the smallest coherent version worth testing. |
| **Protect product truth** | Keep planned intent, current implementation, human acceptance, and public release facts in clearly separated records. |
| **Build in safe slices** | Deliver important features and refactors as reversible, independently verifiable vertical slices. |
| **Diagnose with evidence** | Preserve symptoms, observations, rejected hypotheses, layered causes, and invariants instead of guessing at fixes. |
| **Verify what ships** | Test the actual production artifact and release identity rather than treating compilation as proof of quality. |
| **Resume without rediscovery** | Leave a precise baseline, open risks, and next action so a future session can continue immediately. |

## Quick start

Clone the repository into the personal skill directory used by your agent:

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

Then invoke it explicitly with a real task:

```text
Codex:            Use $how-to-make-application to shape this app idea into a focused first release.
Claude Code:      /how-to-make-application Shape this app idea into a focused first release.
DeepSeek Harness: /how-to-make-application Shape this app idea into a focused first release.
```

The repository root is the skill root. Each supported agent reads the same canonical [`SKILL.md`](SKILL.md) and the same on-demand references.

## Agent compatibility

| Agent | Support | Personal discovery path | Explicit invocation | Details |
| --- | --- | --- | --- | --- |
| Codex | Native | `~/.codex/skills/how-to-make-application/` | `$how-to-make-application` | [`agents/openai.yaml`](agents/openai.yaml) |
| Claude Code | Native Agent Skill | `~/.claude/skills/how-to-make-application/` | `/how-to-make-application` | [Adapter guide](adapters/claude-code.md) |
| DeepSeek Harness | Native Skill, developer preview | `~/.dsh/skills/how-to-make-application/` | `/how-to-make-application` | [Adapter guide](adapters/deepseek-harness.md) |

For repository-scoped use, install the repository under `.claude/skills/` or `.dsh/skills/`. DeepSeek Harness also scans compatible bundles in personal and project `.agents/skills/` directories. The adapter guides include project installation, update, invocation, and verification details.

Agent-specific metadata never replaces the canonical workflow. An adapter changes discovery and invocation only; it does not grant extra tools, permissions, publishing authority, paid-service access, or secret access.

## How it works

<p align="center">
  <strong>Reality → Specification → Slice → Evidence → Release → Handoff</strong>
</p>

The skill selects the smallest working mode that fits the task:

| Mode | Outcome |
| --- | --- |
| **Shape** | Product brief, constraints, risks, and first testable release |
| **Bootstrap** | App skeleton, minimum document system, development loop, and first vertical slice |
| **Build** | An approved feature implemented against a focused execution specification |
| **Evolve** | Architecture or behavior changed while preserving explicit invariants |
| **Diagnose** | Symptoms, evidence, layered causes, rejected hypotheses, and a verified fix path |
| **Release** | A particular artifact verified and published only with explicit authorization |
| **Resume** | Current baseline reconstructed and the next unblocked slice continued |

### Core principles

1. Establish reality before planning.
2. Separate durable rules, planned intent, current work, release facts, and human acceptance.
3. Define invariants and failure semantics before choosing architecture.
4. Implement in reversible, independently verifiable slices.
5. Produce evidence proportional to risk.
6. Never report a proposal as implemented, a candidate as released, or an unobserved result as passed.

## The document system

Each document owns one kind of truth:

| Artifact | Owns | Must not claim |
| --- | --- | --- |
| **Stable project rules** | Long-lived product, engineering, privacy, and release constraints | Transient progress |
| **Product or execution specification** | Planned intent, boundaries, decisions, phases, and acceptance design | Implementation or release completion |
| **Implementation report** | What actually landed and how it was verified | Future scope as completed |
| **Handoff** | Current workspace, evidence, open risks, and exact next action | A chronological project diary |
| **Version history** | Verified public release identity and withdrawn-release history | Candidates or internal builds as released |
| **Acceptance record** | Human-observed product, visual, interaction, hardware, or accessibility results | Unobserved results as passed |

When sources conflict, the default priority is: current user instruction, current production reality, verified release artifacts, current handoff, approved specifications, then external references and conventions.

## Usage examples

### Start a new application

```text
Use the how-to-make-application skill to turn this idea into a product brief,
define the smallest coherent release, and identify the first vertical slice.
```

### Evolve an existing codebase

```text
Use the how-to-make-application skill to inspect this repository, establish the
real baseline, and write an execution specification for the next feature.
```

### Prepare a release without publishing

```text
Use the how-to-make-application skill to verify this release candidate, record
the evidence, and prepare a precise handoff. Do not publish yet.
```

## Real-world proof: QuotaView

This skill was distilled from the SDD system used to build and release [QuotaView](https://github.com/Duoasa/QuotaView), a native macOS application developed through repeated product, architecture, UI-stability, packaging, and release iterations.

| Public artifact | What it demonstrates |
| --- | --- |
| [Stable project rules](https://github.com/Duoasa/QuotaView/blob/main/AGENTS.md) | Durable product, design, implementation, privacy, and release constraints |
| [Core architecture execution specification](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-architecture-evolution.md) | Goals, non-goals, invariants, target architecture, phases, quality gates, ADRs, and stop conditions |
| [WidgetKit specialized specification](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-widgetkit-solution.md) | Narrow subsystem responsibilities, data flow, privacy, failure modes, budgets, and acceptance |
| [Implementation report](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-refactor-0.2.0-report.md) | Delivered facts and automated evidence separated from pending human acceptance |
| [Current handoff](https://github.com/Duoasa/QuotaView/blob/main/HANDOFF.md) | Production baseline, active work, verification, workspace boundaries, and release gates |
| [Version history](https://github.com/Duoasa/QuotaView/blob/main/VERSION_HISTORY.md) | Public release identities, artifacts, verification, and withdrawn-release history |

The skill generalizes the working method—not QuotaView's macOS stack, visual system, product scope, or project-specific constraints.

## Repository structure

```text
.
├── SKILL.md                    # Portable workflow entrypoint
├── agents/
│   └── openai.yaml            # Codex UI metadata
├── adapters/
│   ├── claude-code.md          # Claude Code discovery and invocation
│   └── deepseek-harness.md     # DeepSeek Harness discovery and invocation
├── references/
│   ├── document-system.md      # Source-of-truth model
│   ├── execution-playbook.md   # Working modes and execution guidance
│   ├── quality-and-release.md  # Verification, release, and handoff gates
│   └── templates.md            # Reusable document templates
├── README.md                   # English documentation
└── README.zh-CN.md             # 简体中文文档
```

The entrypoint stays compact. Agents load focused references only when the current task needs them.

## Feedback and contributions

Issues, compatibility reports, documentation improvements, and focused pull requests are welcome through [GitHub Issues](https://github.com/Duoasa/how-to-make-application/issues).
