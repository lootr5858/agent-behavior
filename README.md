---
session:
  - core/*.md
subagent:
  - core/working-style.md
---

# Agent store

Shared agent behavior, personal and work. Paths resolve from this file. The host's instruction hierarchy stays authoritative; nothing here grants tool permissions.

## Always loaded

Frontmatter = manifest: globs relative to this file (a new matching file loads with no other change), stripped from injected copies. `brain hook` injects session → this README + `session` files + user store README; subagent → `subagent` files. Not in context → read them.

## Load on purpose

| When | Read |
|---|---|
| Choosing what to load | [Loading](governance/loading.md) |
| Planning or making writes, incl. to this store | [Mutation](governance/mutation.md) |
| Choosing an executor or handing off | [Handoff](governance/handoff.md) |
| Writing agent instructions | [Rule-authoring style](governance/rule-authoring-style.md) |

Nothing else loads by default. Engine, user store, skills, plugins: use when configured and relevant. Needed but unavailable → report it; never search for or create a missing store.
