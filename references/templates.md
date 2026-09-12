# Reusable SDD Templates

Use an existing suitable document first. Copy only the needed template, keeping outcome, scope, invariants, and completion evidence. Remove irrelevant sections rather than filling them with boilerplate; phase headings and templates do not introduce approval stops.

## Product brief

```markdown
# <Application Name> Product Brief

Status: Proposed | Approved
Owner: <name>
Updated: <date>

## Product promise
<One sentence: user + problem + outcome.>

## Primary user and job
<Who, context, and job to be done.>

## First coherent release
- <workflow/outcome>
- <workflow/outcome>

## Non-goals
- <explicitly excluded scope>

## Constraints
- Platform/distribution:
- Privacy/security:
- Time/cost/operations:
- Compatibility/accessibility/localization:

## Success evidence
- <observable adoption, reliability, or task outcome>

## Owner decisions still needed
- <decision and why it changes the product>
```

## Focused execution specification

```markdown
# <Feature or Change> Execution Specification

ID: <stable-id>
Spec status: Proposed | Accepted | Superseded
Implementation authorization: <existing user request, or decision still needed>
Delivery: Planned | Implementing | Verifying | Complete | Released
Baseline: <version/build/commit>
Updated: <date>
Governing rules: <links>

## Decision
<Outcome-first summary.>

## Requested outcome and completion evidence
- Result to deliver:
- Checks that prove it:
- Review or stopping boundary, only if needed:

## Non-goals
- ...

## Invariants
- ...

## Current evidence
| Observation | Evidence | Implication |
|---|---|---|

## Target responsibilities and data flow
<Small diagram or responsibility table.>

## State and failure semantics
| State/event | User result | System behavior | Recovery |
|---|---|---|---|

## Privacy, security, and side effects
- Data read/stored:
- Data forbidden:
- Permission and authorization boundary:
- Retention/redaction:

## Performance and resource budgets
| Measure | Baseline | Gate | Measurement method |
|---|---:|---:|---|

## Phases
### Phase <n>: <name>
- Entry criteria:
- Work:
- Exit evidence:
- Rollback:
- Intentionally absent:

## Verification and acceptance
| Layer/scenario | Expected evidence | Owner |
|---|---|---|

## Decisions and rejected alternatives
| ID | Decision | Reason | Consequence |
|---|---|---|---|

## Stop conditions and deferred decisions
- ...
```

## Architecture decision record

```markdown
# ADR-<number>: <Decision>

Status: Proposed | Accepted | Superseded
Date: <date>

## Context
<Forces, constraints, and evidence.>

## Decision
<What was chosen.>

## Alternatives considered
- <alternative>: <why not>

## Consequences
- Positive:
- Negative/tradeoff:
- Follow-up:

## Evidence and links
- <spec, implementation, tests, release>
```

## Implementation report

```markdown
# <Change> Implementation Report

Specification: <link>
Implemented identity: <version/build/commit>
Date: <date>

## Scope delivered
- ...

## Code and architecture mapping
| Responsibility | File/module/symbol |
|---|---|

## Deviations from specification
| Deviation | Evidence/reason | Spec update |
|---|---|---|

## Verification evidence
| Check | Result | Evidence |
|---|---|---|

## Waiting for owner acceptance
- ...

## Known limitations and next phase
- ...
```

## Current handoff

```markdown
# <Application> Handoff

Updated: <date/time zone>
Workspace: <path; verify branch and HEAD live on resume>
Production baseline: <version/build/tag/commit>
Current development identity: <source/workspace and unpublished work; may share stable version configuration>
Current objective: <one sentence>

## Release entry
<Direct link to current release record.>

## Current state
- Implemented:
- In progress:
- Not started:

## Verification
| Check | Result | Evidence/date |
|---|---|---|

## Waiting for owner acceptance
- ...

## Workspace boundaries
- User-owned/unrelated changes:
- Files intentionally in scope:

## Risks and blockers
- ...

## Exact next action
1. ...
```

## Version record

```markdown
## <Marketing Version> (Build <n>)

Status: Released | Withdrawn
Date/time zone: <date>
Tag/store identity: <id>
Release commit: <hash>
Release URL: <url>
Artifact: <name>
Size/hash: <values if applicable>
Signing/store validation: <result>

### User-visible changes
- ...

### Verification
- ...

### Known issues / withdrawal reason / replacement
- ...
```

## Verification matrix row

```markdown
| Dimension | Scenario | Expected result | Status | Evidence | Owner |
|---|---|---|---|---|---|
| Data | Missing value | Explicit unavailable state; no fabricated zero | Passed | <test/log> | Automation |
| Visual | Dark mode | Hierarchy and contrast remain correct | Waiting for owner acceptance | — | Product owner |
```
