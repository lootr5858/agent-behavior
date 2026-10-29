# Mutation

How writes happen across the brain.

## Write scope

| Target | Writer | Scope |
|---|---|---|
| `engine/**` | task agent or maintainer | changes the user explicitly approved |
| `agents/**` | task agent or maintainer | changes the user explicitly approved |
| user data | task agent or user-facing app | current task plus `user/README.md` routing and privacy rules |
| secrets in shared content | nobody | never store; use runtime-native secret tooling |

Never infer permission for unrelated paths, external systems, messages, or destructive cleanup.

## Proposals

Use a proposal for an unsolicited durable suggestion, deferred consolidation, or cross-agent coordination.

## Don't overwrite the user

Read every target fresh before editing and preserve the user's changes. Surface conflicts instead of resolving them silently.

## Git

- Keep repository changes reviewable and grouped by purpose.
- Commit, push, merge, or publish only when the live task requests it.
- Git is the applied history; no central changelog duplicates it.
