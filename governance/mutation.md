---
tier: governance
load: on-self-check
---

# Mutation

How writes happen across the brain. Loading → [loading](loading.md). Follow explicitly configured local storage and maintainer policies when present; they are not bundled here.

## Modes

- **Build/maintenance** — inspect the current state, implement the change authorized by the user's live task, verify it, and report the result.
- **Live** — each runtime manages its own opaque home. Shared-agent and user-data writes may be direct when the live task names or clearly entails them.

## Proposals

Use a proposal for an unsolicited durable suggestion, deferred consolidation, or cross-agent coordination. A proposal is optional transport, not a prerequisite for a requested write.

## Write scope

| Target | Writer | Scope |
|---|---|---|
| `engine/**` | task agent or maintainer | changes authorized by the live task |
| `agents/{core,governance,skills,rules,reference}/**` | task agent or maintainer | requested changes; unsolicited durable ideas may be proposals |
| `agents/homes/<self>/**` | owning runtime | runtime-native policy and current task |
| user data | task agent or user-facing app | current task plus the user store's routing and privacy rules |
| secrets in shared content | nobody | never store; use runtime-native secret tooling |

Authority is scoped to the current task. Do not infer permission for unrelated paths, external systems, commits, pushes, messages, or destructive cleanup.

## Plan depth

- P0: trivial, obvious, reversible — implement directly.
- P1: normal — inspect, make a short internal plan, implement, verify.
- P2/P3: complex, ambiguous, risky, rules, or architecture — surface material choices before acting only when the user must decide them.

Do not pause merely to obtain a special phrase. Ask only when missing information or authority would materially change the result.

## Don't overwrite the user

Read every target fresh before editing and preserve the user's changes. Surface conflicts instead of resolving them silently.

## Git

- Keep repository changes reviewable and grouped by purpose.
- Commit, push, merge, or publish only when the live task requests it.
- Each opaque agent home follows its runtime-specific tracking and backup policy.
- Git is the applied history; no central changelog duplicates it.
