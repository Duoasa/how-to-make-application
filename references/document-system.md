# Lightweight SDD Document System

Use this system to help one developer and future AI sessions maintain a reliable model of the application. Create only the artifacts that change decisions or preserve evidence.

## Source-of-truth hierarchy

Use this default order when sources conflict:

1. The user's current explicit instruction.
2. Current production code, configuration, database schema, and observable behavior.
3. Verified release artifacts, tags, store records, and published metadata.
4. The current handoff or work-state record.
5. Approved product, feature, architecture, and QA specifications.
6. External references, prototypes, and general conventions.

The hierarchy does not make code automatically correct. It means code is the strongest evidence of current behavior. If current behavior violates the newly confirmed intent, describe the discrepancy and change both implementation and its authoritative documentation in the same task.

## Minimum document set

### Stable project rules

Use `AGENTS.md`, `PROJECT_RULES.md`, or the repository's existing equivalent for durable constraints:

- product identity and principles;
- supported platforms and compatibility policy;
- security, privacy, data, and side-effect boundaries;
- implementation and dependency preferences;
- accessibility and localization expectations;
- required verification and release gates;
- ownership and approval boundaries.

Do not place transient progress, candidate version claims, or a chronological work log here.

### Product brief

Use a short product brief when the product direction is not yet stable. Capture the user, problem, promise, primary workflows, business or distribution model, platform choice, success signal, constraints, and first-release non-goals.

### Focused specification

Create one for a substantial feature, refactor, migration, integration, or difficult bug. It owns planned behavior and execution decisions, not completion claims. Include status, baseline, goals, non-goals, invariants, current evidence, target architecture, states, failure handling, phased work, tests, acceptance, stop conditions, and unresolved decisions.

Use a separate specialized specification when a subsystem has enough distinct protocol, security, lifecycle, or platform detail that keeping it in the core document would make most tasks load irrelevant context. State which document wins if they conflict.

### Architecture decision record

Use an ADR for a consequential choice that future maintainers may otherwise reverse without understanding the tradeoff. Record context, decision, alternatives, consequences, status, and links to implementation evidence. Do not use ADRs for routine local choices.

### Implementation report

Use after a large phase or migration when “what actually landed” differs meaningfully from the plan. Record implemented scope, code mapping, automated evidence, artifact or performance comparisons, deviations, and owner acceptance still pending. The report describes facts; it does not replace the governing specification.

### Handoff

Maintain one compact current-state entry point:

- update date and workspace/branch;
- production baseline and current development identity;
- current objective and status;
- implemented but unreleased work;
- verification completed with exact results;
- verification not run or waiting for owner acceptance;
- working-tree boundaries and unrelated user-owned files;
- blockers, risks, and the exact next action;
- direct links to the current release record and active specifications.

Rewrite stale status instead of appending an endless diary. Preserve important history in version records, ADRs, issue history, or implementation reports.

### Version history

Create this after the first real release. It is the release ledger, not the roadmap. For each release record version/build, date, status, tag or store identity, release commit, artifact name, size/hash when applicable, signing/notarization/store status, verification, release URL, core changes, known issues, and replacement for a withdrawn release.

Never list an internal build or candidate as publicly released. Never reuse a released version identity or silently delete a withdrawn release from history.

### Acceptance record

Use a QA matrix or issue record when visual, interaction, hardware, accessibility, localization, or domain acceptance requires a person. Separate automated evidence from human observation. Only the person who observed the result, or an authorized reliable tool run, may mark it passed.

## Status vocabulary

Use explicit states:

- `proposed`: not approved or started;
- `approved`: direction accepted, implementation not implied;
- `in progress`: active work, not releasable by default;
- `implemented`: code exists, verification may be incomplete;
- `verified`: stated automated or observable checks passed;
- `waiting for owner acceptance`: machine checks passed but human product judgment remains;
- `released`: exact published artifact and metadata were verified;
- `withdrawn`: release removed or superseded for a recorded defect;
- `blocked`: a named missing decision, capability, credential, or external condition prevents progress.

Avoid ambiguous phrases such as “basically done,” “should work,” or “release ready” without defining the remaining gates.

## Linking and synchronization

- The handoff links directly to the current release entry.
- The version history links back to the handoff.
- Focused specs link to governing rules and superseded specs.
- Implementation reports link to their specification and code/release identity.
- Public downloads, store metadata, release notes, version records, and handoff identify the same current release.
- A release, withdrawal, tag change, or change to the public “latest” pointer updates all affected records in the same task.

## Documentation hygiene

- Prefer tables for exact mappings and evidence; prose for rationale and boundaries.
- Give long-lived requirements stable identifiers when they will be referenced from code, tests, or later specs.
- Separate confirmed facts, assumptions, proposals, and deferred decisions.
- Date external claims and record the version or commit of borrowed designs.
- Borrow proven engineering patterns, not another product's scope, branding, or accidental complexity.
- Do not duplicate the same fact across many documents unless there is a synchronization rule and clear ownership.
