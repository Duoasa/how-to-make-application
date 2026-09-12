# Quality, Acceptance, and Release

Use this reference to create evidence that an application change works and that a specific artifact is safe to ship.

## Verification layers

Select layers by the affected behavior and risk, honoring explicit project and CI gates.
Documentation-only work checks links, consistency, and diff hygiene; a local code
fix usually starts with focused tests. Shared contracts or uncertain impact justify
the standard suite; platform, packaging, or release changes justify actual builds
and artifact checks. Report material gaps, not every irrelevant layer as N/A.
After relevant checks pass, repeat only after new changes, failures, or unresolved
risks. Scoped temporary-fixture tests can run and be repaired without repeated
approval; verify side effects before real-account, installation, or network tests.

1. **Static review**: diff, dependency direction, API use, permissions, data semantics, localization, accessibility, and prohibited paths.
2. **Focused tests**: pure models, transformations, state machines, migrations, failure behavior, and regressions closest to the change.
3. **Integration tests**: component boundaries, real serialization, local fake services, cancellation, timeout, ordering, partial responses, and unknown fields.
4. **Standard suite**: the repository's normal tests and linters.
5. **Production build**: the configuration, optimization, targets, architectures, assets, and entitlements that users receive.
6. **Artifact inspection**: version/build, package structure, dynamic dependencies, embedded extensions/frameworks, resources, signatures, hashes, and size.
7. **Runtime exercise**: clean extraction/install, launch, upgrade/migration, critical workflow, offline/degraded path, and cleanup.
8. **Human product acceptance**: visual quality, interaction feel, device behavior, language fit, accessibility experience, and business correctness that automation cannot establish.

Build success proves compilation, not packaging, installation, migration, runtime loading, or product quality.

## State and acceptance matrix

Select dimensions affected by the change:

| Dimension | Example cases |
|---|---|
| Data | valid, missing, stale, partial, malformed, empty, maximum size |
| Request | idle, loading, success, failure, timeout, cancelled, overlapping |
| Lifecycle | first launch, resume, background, restart, shutdown, upgrade |
| Capability | enabled, disabled, unavailable, permission denied, revoked |
| Connectivity | online, offline, intermittent, server incompatible |
| Identity | signed out, one account, account changed, ambiguous account |
| Presentation | narrow/wide, light/dark, scale, reduced motion, high contrast |
| Language | default, supported translations, long strings, locale/time zone |
| Accessibility | keyboard, focus, screen reader, labels, non-color status |
| Distribution | debug, release, clean install, upgrade, downloaded artifact |

For each required cell record `passed`, `failed`, `not run`, `blocked`, or `waiting for owner acceptance`, plus evidence or an issue link. Do not mark an entire dimension passed from one happy-path check.

## Temporary behavior gate

Mocks and diagnostic entry points may be useful during development, but they must be:

- enabled only through explicit development/test injection;
- visibly labeled when they can reach a user interface;
- marked with a stable searchable token chosen for the project;
- unable to become a release default;
- removed from production runtime paths before commit, push, or release;
- covered by a final repository search whose result is recorded.

Test fixtures and permanent isolated development tools may remain when explicitly separated from production defaults. Do not delete them merely because temporary debug injection must be removed. Never use mock data to make missing production data appear valid.

Before sharing or publishing, inspect affected files for secrets, real account payloads, credentials, private keys, private paths, and unintended permissions or endpoints. Screenshots require appropriate data handling when they are part of the authorized deliverable.

## Release candidate identity

Give every externally distinguishable build a unique identity. A candidate or hotfix that keeps the marketing version should still increment its build number and use a unique artifact name or tag. Never overwrite a published tag or asset to make history appear linear.

Before publishing, reconcile:

- application version and build configuration;
- embedded targets/extensions/frameworks;
- artifact filename and package metadata;
- release notes and public download/store entry;
- handoff and version history.

## Release gate

Adapt the commands to the platform. Require evidence for:

1. clean relevant tests and static checks;
2. production build from the intended commit;
3. version/build consistency across packaged components;
4. target architectures, resources, dependency loading, and permissions;
5. signing, notarization, store validation, or platform trust requirements;
6. clean extraction/install and real launch;
7. critical workflow smoke test and data migration/upgrade path when applicable;
8. final artifact size and cryptographic hash when distributed directly;
9. release notes based on one maintained source;
10. exact release commit/tag/store submission and uploaded asset;
11. post-publication download or installation of the distributed artifact;
12. byte/hash, signature, launch, and smoke verification of what users actually receive.

Publishing requires scoped user authorization. Preparation and read-only verification do not imply it. Once the exact release operations are authorized, continue through their validation and record updates without requesting the same permission at each step; stop only for a new boundary or actual blocker.

## Release facts and withdrawal

Only mark `released` after the publication exists and the distributed artifact has been checked. If a release is withdrawn:

- keep its historical record;
- mark it withdrawn and explain the user-impacting defect;
- remove it from current download/latest pointers;
- name the safe replacement or rollback;
- verify every public pointer and handoff entry;
- never restore it as the baseline without a new explicit decision and evidence.

## Reporting the result

Lead with the outcome and state the exact scope:

- implemented behavior;
- tests/builds/artifacts verified, with counts or identities;
- checks not run and why;
- human acceptance still pending;
- release status: not requested, candidate, published, or withdrawn;
- known risks and the next concrete action.

Avoid “all good” or “fully tested” when only a subset was observed.
