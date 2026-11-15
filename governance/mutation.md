# Mutation

Rules for writes, Git operations, and credentials in Brain.

## Authorization

Any agent may write where its tools permit, subject to explicit user approval under `core/behavior-rules.md`. Approval covers only the proposed changes.

## Execution

- Read targets fresh before editing; preserve unrelated changes and surface conflicts.
- Never store secrets in shared files; use runtime-native secret tooling.
- Propose unsolicited durable changes before applying them.

## Git

- Keep changes reviewable and grouped by purpose.
- Brain write tools may auto-commit approved edits.
- Resolve the intended repository root before Git operations. For checkout-based edits, sync before writing and review staged changes before committing.
- Push, merge, or publish only with explicit approval.

## Public repository boundaries

- `engine/` and `agents/` publish only public-shareable files explicitly allowed by their repository-root `.gitignore`. Their directories may also contain private local material that must remain untracked.
- Treat both root `.gitignore` files as authoritative exact-file allowlists. Change either only with Evan's explicit approval of that exact edit. Add files individually, without whole-directory exceptions. Approval to edit other files does not approve changing an allowlist.
- Never bypass an allowlist through force-adds, nested ignore overrides, or other staging methods. Keep secrets, credentials, private user data, and independent nested repositories excluded from the root repos.
- Before committing or pushing either root repo, check tracked paths against its allowlist and review staged or outgoing content for private material. Stop and report violations, including already-tracked files excluded by the allowlist; obtain approval before correcting them.
- Keep every first-party independent repo within either root separate, with its own Git metadata, history, and remotes. Keep it ignored by the containing root repo; do not absorb its files or register it as a submodule. This includes independent repos under `agents/skills/` and `agents/plugins/`.

## GitHub credentials

- Give `engine/`, `agents/`, and every first-party independent repo within either its own distinct fine-grained GitHub token, restricted to that GitHub repo and the permissions needed for the approved work.
- Keep credential configuration in each repo's local Git config and its token in a dedicated private, untracked credential store. Reset inherited credential helpers, enable `credential.useHttpPath`, and configure only that repo's credential store.
- Never share tokens between repos, including parents and nested repos. Keep tokens out of tracked files, remote URLs, global configuration, and shared credential stores or environments. Do not fall back to another repo's or a global credential.
- Before authenticated GitHub operations, verify that the selected credentials belong to the intended repo and meet these restrictions. If credentials are missing or their scope cannot be verified, stop and report the required setup or verification.
