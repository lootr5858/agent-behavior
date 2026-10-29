# Agent store

Shared agent behavior for personal and work environments. Resolve paths from this file. The host platform's instruction hierarchy stays authoritative; nothing here grants tool permissions.

## Always loaded

Every Markdown file in `core/`, unless already in context. Keep one import line per core file:

@core/behavior-rules.md
@core/persona.md
@core/routing.md

## Load on purpose

| When | Read |
|---|---|
| Selecting context or checking loading | [Loading](governance/loading.md) |
| Planning or performing writes | [Mutation](governance/mutation.md) |
| Transferring a task | [Handoff](governance/handoff.md) |
| Authoring or revising agent instructions | [Rule-authoring style](governance/rule-authoring-style.md) |

Load nothing else from this store by default. References to the brain's engine, user store, rules, skills, references, agent homes, or proposal channels describe local integration: use them when configured and relevant. Never search for or create a missing store to satisfy a reference; if a task needs an unavailable resource, report the limitation.

## Maintaining this store

Edit in the checkout the agents use. Run `git pull --ff-only` before editing and resolve divergence deliberately. `.gitignore` is an exact-file allowlist and `git add -f` bypasses it, so review the staged file list before every public commit. Keep credentials in local Git configuration, never in these files.
