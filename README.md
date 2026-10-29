---
session:
  - core/*.md
  - skills/minimum-work/SKILL.md
  - skills/scanline/SKILL.md
subagent:
  - skills/minimum-work/SKILL.md
  - skills/scanline/SKILL.md
---

# Agent store

Shared agent behavior for personal and work environments. Resolve paths from this file. The host platform's instruction hierarchy stays authoritative; nothing here grants tool permissions.

## Always loaded

This file's frontmatter is the manifest (stripped from injected copies). Each session gets this README, the `session` files, and the user store's README; each subagent gets the `subagent` files. The engine's `brain-context` hook injects them. If they are not in context, read them. Patterns are globs relative to this file, so a new file under a listed pattern loads with no other change.

## Load on purpose

| When | Read |
|---|---|
| Selecting context or checking loading | [Loading](governance/loading.md) |
| Planning or performing writes | [Mutation](governance/mutation.md) |
| Transferring a task | [Handoff](governance/handoff.md) |
| Authoring or revising agent instructions | [Rule-authoring style](governance/rule-authoring-style.md) |

Load nothing else from this store by default. References to the brain's engine, user store, skills, or plugins describe local integration: use them when configured and relevant. If a task needs an unavailable resource, report the limitation; never search for or create a missing store.

## Maintaining this store

Edit in the checkout the agents use. Run `git pull --ff-only` before editing and resolve divergence deliberately. `.gitignore` is an exact-file allowlist and `git add -f` bypasses it, so review the staged file list before every public commit. Keep credentials in local Git configuration, never in these files.
