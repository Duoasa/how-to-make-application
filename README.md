# How to Make Application

[简体中文](README.zh-CN.md)

A portable specification-driven development skill for solo application developers using Codex, Claude Code, or DeepSeek Harness.

It helps turn an idea or an existing codebase into a product that can be understood, implemented, verified, released, and resumed by one person. Documentation is treated as a control system for decisions and evidence—not as paperwork.

## What this skill covers

- Shape an app idea into a focused product brief and smallest coherent release.
- Establish a source-of-truth hierarchy for code, specifications, handoff, acceptance, and release facts.
- Specify goals, non-goals, invariants, states, failure behavior, budgets, and stop conditions.
- Implement substantial features and refactors as independently verifiable vertical slices.
- Diagnose difficult bugs by preserving evidence, rejected hypotheses, and system invariants.
- Verify production artifacts instead of treating compilation as proof of release quality.
- Keep current work, human acceptance, and published version history precise and resumable.

The skill is intended for substantial application work. It deliberately avoids imposing the full workflow on isolated questions or trivial edits.

## Agent compatibility

The repository keeps one canonical `SKILL.md`. Each supported agent reads that same file and the same on-demand references; only discovery paths and explicit invocation syntax differ.

| Agent | Compatibility | Personal discovery path | Explicit invocation |
|---|---|---|---|
| Codex | Native | `~/.codex/skills/how-to-make-application/` | `$how-to-make-application` |
| Claude Code | Native Agent Skill | `~/.claude/skills/how-to-make-application/` | `/how-to-make-application` |
| DeepSeek Harness | Native Skill, developer preview | `~/.dsh/skills/how-to-make-application/` | `/how-to-make-application` |

See the focused [Claude Code adapter](adapters/claude-code.md) and [DeepSeek Harness adapter](adapters/deepseek-harness.md) for personal, project, update, invocation, and verification details. `agents/openai.yaml` supplies Codex UI metadata; Claude Code and DeepSeek Harness ignore it and load the portable `SKILL.md` directly.

## Working modes

| Mode | Outcome |
|---|---|
| Shape | Product brief, constraints, risks, and first testable release |
| Bootstrap | App skeleton, minimum document system, development loop, and first vertical slice |
| Build | An approved feature implemented against a focused execution specification |
| Evolve | Architecture or behavior changed while preserving explicit invariants |
| Diagnose | Symptoms, evidence, layered causes, rejected hypotheses, and a verified fix path |
| Release | A particular artifact verified and published only with explicit authorization |
| Resume | Current baseline reconstructed and the next unblocked slice continued |

## The document system

The workflow separates documents by the kind of truth they own:

| Artifact | Owns | Must not claim |
|---|---|---|
| Stable project rules | Long-lived product, engineering, privacy, and release constraints | Transient progress |
| Product or execution specification | Planned intent, boundaries, decisions, phases, and acceptance design | Implementation or release completion |
| Implementation report | What actually landed and how it was verified | Future scope as completed |
| Handoff | Current workspace, evidence, open risks, and exact next action | A chronological project diary |
| Version history | Verified public release identity and withdrawn-release history | Candidates or internal builds as released |
| Acceptance record | Human-observed product, visual, interaction, hardware, or accessibility results | Unobserved results as passed |

When sources conflict, the default priority is: current user instruction, current production reality, verified release artifacts, current handoff, approved specifications, then external references and conventions.

## Install

Choose the discovery root for the agent you use. The repository root is the skill root in every case.

### Codex

Ask Codex to install the skill from:

```text
https://github.com/Duoasa/how-to-make-application
```

Or install it manually:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.codex/skills/how-to-make-application
```

### Claude Code

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.claude/skills/how-to-make-application
```

For a repository-scoped installation tracked by the project:

```bash
mkdir -p .claude/skills
git submodule add https://github.com/Duoasa/how-to-make-application.git .claude/skills/how-to-make-application
```

### DeepSeek Harness

```bash
mkdir -p ~/.dsh/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.dsh/skills/how-to-make-application
```

For a repository-scoped installation tracked by the project:

```bash
mkdir -p .dsh/skills
git submodule add https://github.com/Duoasa/how-to-make-application.git .dsh/skills/how-to-make-application
```

DeepSeek Harness also scans compatible bundles under `~/.agents/skills/` and project `.agents/skills/`.

## Use

All three agents can select the skill automatically from its description. Explicit invocation uses the host agent's syntax:

```text
Codex:           Use $how-to-make-application to turn this app idea into a focused first-release plan.
Claude Code:     /how-to-make-application Turn this app idea into a focused first-release plan.
DeepSeek Harness: /how-to-make-application Turn this app idea into a focused first-release plan.
```

Further examples:

```text
Use the how-to-make-application skill to inspect this existing repository, establish the real baseline, and write an execution specification for the next feature.
```

```text
Use the how-to-make-application skill to verify this release candidate, record the evidence, and prepare a precise handoff. Do not publish yet.
```

The skill preserves normal authorization boundaries. A specification or release plan does not authorize publishing, destructive migration, paid services, secret access, or unrelated external changes.

## Real-world implementation: QuotaView

This skill was distilled from the SDD system used to build and release [QuotaView](https://github.com/Duoasa/QuotaView), a native macOS application developed through repeated product, architecture, UI-stability, packaging, and release iterations.

The public project demonstrates the document separation used by this skill:

- [AGENTS.md](https://github.com/Duoasa/QuotaView/blob/main/AGENTS.md) owns durable product, design, implementation, and release constraints.
- [Core architecture execution specification](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-architecture-evolution.md) records goals, non-goals, invariants, target architecture, phased implementation, quality gates, ADRs, and stop conditions.
- [WidgetKit specialized specification](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-widgetkit-solution.md) shows how a subsystem specification narrows responsibilities, data flow, privacy, failure modes, budgets, and acceptance.
- [Implementation report](https://github.com/Duoasa/QuotaView/blob/main/docs/design/quotaview-core-refactor-0.2.0-report.md) separates delivered facts and automated evidence from product-owner acceptance still pending.
- [HANDOFF.md](https://github.com/Duoasa/QuotaView/blob/main/HANDOFF.md) records the current production baseline, active development state, verification, workspace boundaries, and release gates.
- [VERSION_HISTORY.md](https://github.com/Duoasa/QuotaView/blob/main/VERSION_HISTORY.md) records public release identities, artifacts, verification, and withdrawn-release history without turning internal builds into release facts.

The skill generalizes the working method, not QuotaView's macOS stack, visual system, product scope, or private constraints.

## Repository layout

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── adapters/
│   ├── claude-code.md
│   └── deepseek-harness.md
├── references/
│   ├── document-system.md
│   ├── execution-playbook.md
│   ├── quality-and-release.md
│   └── templates.md
├── README.md
└── README.zh-CN.md
```

The entrypoint stays compact. Each supported agent reads the focused references only when the current task needs them.

## Core principles

1. Establish reality before planning.
2. Separate durable rules, planned intent, current work, release facts, and human acceptance.
3. Define invariants and failure semantics before choosing architecture.
4. Implement in reversible, independently verifiable slices.
5. Produce evidence proportional to risk.
6. Never report a proposal as implemented, a candidate as released, or an unobserved result as passed.
