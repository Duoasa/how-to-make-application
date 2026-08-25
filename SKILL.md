---
name: how-to-make-application
description: Guides a solo developer to plan, build, evolve, diagnose, verify, release, and resume an application using a lightweight specification-driven system. Use when turning an app idea into an executable plan, establishing project truth and constraints, implementing a substantial feature or refactor, preparing a release, or creating a reliable handoff. Do not use for isolated factual questions or trivial edits unless the user asks for the full workflow.
---

# How to Make Application

Build the smallest coherent product that can be understood, verified, released, and resumed by one person. Treat documentation as a control system for decisions and evidence, not as ceremony.

## Core operating rules

1. Preserve the user's product intent and explicit scope. A specification describes work; it does not authorize unrelated changes, external publishing, paid services, destructive migration, or access to secrets.
2. Establish reality before planning. Inspect the repository, running behavior when available, configuration, tests, release state, and existing instructions. Do not let an old plan override current production facts.
3. Separate durable rules, planned intent, current work, release facts, and human acceptance. Never record a proposal as implemented, a candidate as released, or an unobserved visual result as passed.
4. Define goals, non-goals, invariants, and failure semantics before choosing architecture. Missing, stale, unavailable, and failed states must not silently become valid zero values or success states.
5. Implement in independently verifiable vertical slices. Introduce no more than one new high-risk boundary in a phase when practical, preserve existing behavior through compatibility layers or migrations, and keep every phase releasable or reversible.
6. Verification must produce evidence proportional to risk. Review code and state transitions, run relevant tests, build the real deliverable, inspect its contents, and exercise the artifact. Reserve visual, experiential, or product acceptance for the user unless they explicitly delegate it and a reliable observation path exists.
7. Keep temporary debug behavior explicit, isolated, visibly labeled, searchable, and impossible to ship. Remove it and verify its absence before commit, push, or release.
8. Update handoff and version facts in the same task that changes them. A future session should be able to determine the production baseline, current workspace, completed evidence, open risks, and exact next step without reconstructing history.
9. Keep host-agent mechanics separate from the workflow. Use only tools, permissions, and invocation mechanisms actually exposed by the current agent; an adapter never grants broader authority.

## Choose the working mode

Identify the mode from the request and current repository:

- **Shape**: turn an idea into a product brief, constraints, risks, and a smallest testable release.
- **Bootstrap**: establish the application skeleton, minimum document system, development loop, and first vertical slice.
- **Build**: implement an approved feature from a focused execution specification.
- **Evolve**: change architecture or behavior while preserving explicit invariants and compatibility.
- **Diagnose**: establish symptoms, evidence, layered causes, rejected hypotheses, and a verification plan before proposing a fix.
- **Release**: prove a particular artifact, publish only when authorized, and synchronize release facts.
- **Resume**: reconstruct the current baseline from code, handoff, and verified release records, then continue the next unblocked slice.

Do not force the entire lifecycle onto a narrow request. Apply only the sections needed, while maintaining the source-of-truth and evidence rules.

## Start every substantial task

1. Read repository-level instructions and inspect the working tree without disturbing unrelated user changes.
2. Locate the documents that claim to describe stable constraints, current work, feature design, implementation evidence, releases, and acceptance.
3. Resolve contradictions with this default priority:
   - current user instruction;
   - current production code, configuration, and observable behavior;
   - verified release artifacts and release metadata;
   - current handoff or work-state record;
   - approved specifications and acceptance records;
   - external references and general conventions.
4. State the baseline, the requested outcome, the assumptions that materially affect the solution, and any decision that truly requires the user.
5. Choose the smallest set of documents and checks that make the work safe and resumable.

For a new project, or when the repository lacks a coherent truth system, read [references/document-system.md](references/document-system.md). Use [references/templates.md](references/templates.md) only for the artifacts actually needed.

## Specify before changing a substantial system

A useful execution specification answers:

- What user problem and observable outcome define success?
- What is explicitly outside this iteration?
- Which existing behaviors, data meanings, privacy boundaries, and compatibility promises cannot change?
- What is the verified baseline, including known defects and unknowns?
- Which components own each responsibility, and what is the dependency or data-flow direction?
- What states and transitions exist, including loading, missing, stale, partial, error, disabled, cancellation, and recovery?
- What are the security, privacy, performance, size, accessibility, localization, and platform budgets?
- How is the work divided into independently testable phases, and what are each phase's entry, exit, rollback, and stop conditions?
- Which automated checks and human acceptance scenarios prove the result?

Prefer stable identifiers for requirements, decisions, states, metrics, and document sections when later work will cite them. Record why plausible alternatives were rejected when that knowledge prevents regression.

For implementation and evolution work, read [references/execution-playbook.md](references/execution-playbook.md).

## Execute against the specification

- Start from a behavior and resource baseline before refactoring.
- Build one end-to-end slice through the real architecture before broadening the abstraction.
- Keep domain meaning independent from UI labels and transport quirks.
- Isolate side effects behind explicit capability and authorization boundaries.
- Make disabled features converge to no background work.
- Bound retries, concurrency, time, memory, storage, subprocesses, and output where relevant.
- Migrate persisted data and settings explicitly; do not reinterpret old data silently.
- Keep compatibility and new functionality in separate phases when combining them would obscure regressions.
- Stop when a required assumption, official capability, identity boundary, migration path, or verification method is missing. Report the evidence and the decision needed; do not hide the gap with a mock or undocumented fallback.

When investigation reveals that the specification is wrong, update the specification and explain the change before continuing. Do not make code and documentation disagree on purpose.

## Verify and close the loop

Use [references/quality-and-release.md](references/quality-and-release.md) for release work, risky changes, or any task requiring a durable verification matrix.

At minimum:

1. Review the diff and affected state transitions against goals, non-goals, and invariants.
2. Run the narrowest relevant tests, then the project's standard suite.
3. Build the actual target configuration and inspect versions, architectures, resources, dependencies, permissions, and packaging appropriate to the platform.
4. Exercise a clean artifact or realistic integration path when build success alone cannot prove runtime behavior.
5. Search for temporary mocks, debug entry points, secrets, local paths, unbounded retries, and prohibited operations.
6. Distinguish `verified`, `failed`, `not run`, `blocked`, and `waiting for owner acceptance`; never collapse them into a vague “done.”
7. Record commands, results, artifact identity, known gaps, and the next action in the handoff.
8. Update version history only for release facts that actually happened. Preserve withdrawn releases with their failure reason and replacement rather than erasing the lesson.

## Definition of done

The work is done only when the requested outcome exists, relevant invariants still hold, verification evidence is recorded, temporary scaffolding is gone, documentation matches reality, and any remaining human acceptance is labeled precisely. A release is done only when the exact published artifact has been verified and the public pointers, notes, version record, and handoff agree.
