# Solo Application Execution Playbook

Use the relevant sections for substantial implementation, architectural evolution, integrations, migrations, or difficult defects. The headings are a reference menu, not a mandatory sequence or set of review stops.

## 1. Frame the outcome

Write a compact brief before selecting technology:

- target user and job to be done;
- observable user outcome;
- smallest coherent release;
- explicit non-goals;
- platform, distribution, privacy, budget, and time constraints;
- success and failure signals;
- decisions only the owner can make.

For an existing application, add the current production baseline and the behaviors that must survive the change.

## 2. Baseline reality

Inspect and record only relevant evidence:

- repository status and user-owned changes;
- current version/build and release identity;
- runtime behavior and known defects;
- architecture and dependency directions;
- persisted data, migrations, settings, and compatibility promises;
- automated tests, build paths, packaging, and deployment;
- performance, memory, storage, binary size, or operating-cost baselines when the change can affect them;
- current human acceptance status.

A refactor without a behavior baseline cannot prove preservation. A feature without state and failure baselines tends to encode happy-path guesses.

## 3. Write the execution specification

Use these sections as needed:

1. **Position and status**: document ID, status, date, baseline, governing rules, and superseded documents.
2. **Decision**: the short outcome-first conclusion.
3. **Goals and non-goals**: the boundary of this iteration.
4. **Invariants**: behaviors and meanings that cannot regress.
5. **Current system and confirmed problems**: evidence, not speculation.
6. **Target architecture**: responsibilities, dependency direction, data flow, storage, and side-effect boundaries.
7. **State model**: orthogonal states, transitions, cancellation, timeout, stale/partial/error behavior, and recovery.
8. **Privacy and security**: collected data, forbidden data, permissions, trust boundaries, redaction, retention, and write authorization.
9. **Performance and resource budgets**: measurable targets and limits.
10. **Phases**: work, entry criteria, exit criteria, rollback, and what intentionally remains absent.
11. **Verification**: automated tests, integration scenarios, artifact checks, human matrix, and pass ownership.
12. **Failure modes and degradation**: user result and system behavior for each important failure.
13. **Decisions and rejected alternatives**: enough rationale to prevent regression.
14. **Stop conditions and deferred decisions**: when implementation must pause.

Use diagrams only where flow, ownership, sequence, or state is materially clearer than prose.

## 4. Design phases for reversibility

A robust sequence often looks like:

1. **Contract and baseline**: characterize behavior, data semantics, and resource use without changing production logic.
2. **Reliability**: fix cancellation, timeouts, ordering, stale publication, bounded I/O, and lifecycle symmetry.
3. **Domain and compatibility**: introduce clean models or protocols behind a projection that preserves current UI/API behavior.
4. **First vertical slice**: carry one real user outcome through storage, logic, presentation, and error handling.
5. **Expansion**: add more providers, views, platforms, or automation only after the core slice is stable.
6. **Distribution**: packaging, signing, entitlements, migrations, release metadata, and clean-install verification.

Use phases only when they improve reversibility or verification. Continue between authorized phases without pausing for routine approval. Keep these principles:

- a phase has an observable result and exit criteria;
- a phase does not claim future capabilities;
- risky boundaries such as a new provider, background scheduler, extension, destructive migration, payment, or write operation are introduced separately when possible;
- compatibility migration is separated from broad new behavior;
- each phase can be tested and rolled back without guessing which change caused a regression.

## 5. Implement from semantics outward

- Define domain identifiers, units, aggregation rules, validity, and time semantics before formatting them for a screen.
- Separate availability, business risk, service health, permissions, and loading; do not overload one status.
- Keep collection/read paths physically separate from account mutation or other side effects.
- Verify the capability and authorization for the actual side effect. Reuse existing scoped authorization for ordinary implementation and local checks; reserve new approval for operations outside it.
- Use stable IDs rather than display text, array position, random IDs, or changing values.
- Make repeated requests idempotent or give them an explicit outcome-unknown state; never blindly retry a potentially destructive action.
- Treat disabled as a lifecycle state: no task, process, write, polling, or notification work should remain.
- Bound concurrent work, retries, timeouts, buffers, history, caches, and logs.
- Make persisted schemas versioned and migrations testable.
- Design extensions, widgets, plugins, or background components to consume minimized contracts rather than importing the whole application.
- Prefer platform capabilities and existing project primitives before adding dependencies; justify cost with measured benefit.

## 6. Diagnose before fixing

For complex defects, preserve the learning:

1. Describe user-visible symptoms and reproducible conditions.
2. Gather measurements that distinguish layers.
3. List and test plausible hypotheses.
4. Record rejected explanations when they are likely to recur.
5. Identify invariants the fix must preserve.
6. Model the final event or state sequence.
7. Implement the smallest change that restores the invariant.
8. Test steady state, transitions, rapid reversal, cancellation, degradation, and accessibility modes.
9. Record why previous attempts were insufficient when that insight changes future design.

Do not use animation, delays, retries, cached values, or fixed dimensions to hide an incorrect state or ordering bug.

## 7. Stop conditions

First try relevant evidence, read-only investigation, and reversible repairs within scope. If an unresolved condition below prevents a correct next step, pause only the dependent operation, while completing independent work:

- the only implementation path violates a declared privacy, security, platform, or product boundary;
- identity or ownership cannot be established for persisted data or mutations;
- a value lacks defined units or semantics and downstream behavior would have to guess;
- a disabled subsystem cannot be made to stop its work;
- a migration cannot preserve or safely reject old data;
- an extension requires importing forbidden side effects or secrets;
- a release identity, signing capability, entitlement, or distribution target is unresolved;
- verification requires production secrets, destructive writes, or unapproved external changes;
- a potentially destructive operation has no idempotency or result-reconciliation strategy;
- the work exceeds an agreed performance, size, cost, or compatibility budget without owner approval.

Report the evidence, affected scope, safest available alternatives, and the exact decision needed.
