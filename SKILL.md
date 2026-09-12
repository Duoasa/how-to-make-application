---
name: how-to-make-application
description: Maintain lightweight SDD specs and handoffs for substantial app changes, release preparation, or document-system cleanup.
---

# How to Make Application

Make the requested app work understandable, verifiable, and resumable. Reuse the
project's documents and vocabulary. A small fix does not need a new lifecycle,
specification, or full test/build sequence.

## Start from the requested outcome

Inspect the target workspace and relevant existing changes. Establish only the
facts needed for this task. Current code is evidence of behavior, accepted specs
describe intended behavior, and release records identify published artifacts.
Development code can be newer than the stable release while sharing its version
configuration; do not replace it with the stable tag or stale handoff.

For substantial work, state the outcome, non-goals, important invariants, and
evidence that will count as complete. When implementation is already requested,
write or adjust the necessary specification and continue implementing it without
asking for the same authorization again.

## Read only what the task needs

| Need | Reference |
|---|---|
| Establish or clean up document ownership, status, or handoff | [Document system](references/document-system.md) |
| Design a substantial feature, refactor, migration, or diagnose a difficult defect | Relevant sections of [Execution playbook](references/execution-playbook.md) |
| Choose verification for risky changes, or prepare/publish a release | Relevant sections of [Quality and release](references/quality-and-release.md) |
| Create a document that does not already have a suitable structure | One matching [template](references/templates.md) |

These are alternatives, not a reading sequence. Known specs and local fixes can
be handled directly. Load host adapters only for installation or invocation help.

## Execution boundaries

- Continue through implementation, relevant checks, fixes, and necessary records
  until the requested outcome is complete. A first draft or phase exit is not a
  review stop unless the user requested that stop.
- Preserve user-owned work, real data, and product constraints. Existing task
  authorization covers scoped edits and appropriate local verification; it does
  not expand to unrelated changes, publishing, purchases, secrets, or destructive
  operations. Use only available tools and actual execution permissions.
- Resolve uncertainty through relevant evidence and reversible investigation.
  Ask only when a missing decision matters and cannot be inferred; pause only
  dependent operations and continue useful independent work.
- Keep unavailable, missing, and failed states distinct from valid zero or
  success. Keep temporary runtime injection separate from production defaults;
  preserve legitimate test fixtures and permanent isolated development tools.

## Completion

Run the checks that prove this change, including required project/CI gates.
Broaden or repeat only for a new change, failure, or unresolved risk. Documentation
work needs document validation; a production build is needed when the affected
deliverable or release requires it. Do not treat all local tests as side-effect-free.

Report the delivered result, verification and material gaps. Human acceptance
remains pending unless observed by its owner or explicitly delegated and reliably
checked; pending acceptance does not stop independent authorized work. Update only
affected specs and current-state records. Change release history only when release
facts change, and verify the exact distributed artifact before claiming release.
