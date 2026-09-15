# Universal agent behavior rules

One shared rule set for personal and work environments. This repository contains four always-loaded core files and four conditionally loaded governance files.

## Loading

Configure your agent's existing instruction entry point to read this checkout. A README or frontmatter field does not activate itself. Resolve these paths from the checkout root.

| When | Read |
|---|---|
| Every turn | [Behavior](core/behavior-rules.md), [persona](core/persona.md), [preferences](core/preferences.md), [routing](core/routing.md) |
| Selecting context or checking loading | [Loading](governance/loading.md) |
| Planning or performing writes | [Mutation](governance/mutation.md) |
| Transferring a task | [Handoff](governance/handoff.md) |
| Authoring or revising agent instructions | [Rule-authoring style](governance/rule-authoring-style.md) |

Existing host instructions may load additional local core files. Domain rules, user identity, private context, skills, plugins, and runtime configuration remain owned by each environment.

## Local dependencies

“Brain” means the host's configured knowledge and instruction environment. References to its bootstrap, engine, user store, agent homes, discipline manifests, and proposal channels describe local integration, not additional files supplied by this repository.

Use those local mechanisms only when configured and relevant. The `agents/`, `engine/`, `user/`, `homes/`, `rules/`, `skills/`, and `reference/` paths describe that layout; do not search for or create missing stores merely to satisfy a reference. If the host uses another layout, follow its explicit routing. Do not guess a replacement path.

Skills and discipline manifests are optional. When available, their existing selection and routing rules still apply. If a requested task requires an unavailable resource or handoff mechanism, report the limitation rather than claim completion. Propose durable preferences to the user if no proposal channel is configured; do not silently store them.

The host platform's instruction hierarchy remains authoritative. This collection does not grant additional tool permissions or override platform requirements.

## Sync

Edit these files directly in the checkout used by the agent. Pull before editing, review the diff, commit the intended files, and push. Pull on the other machine; reload the agent's context when needed.

Use `git pull --ff-only`. If a pull fails or histories diverge, resolve the conflict deliberately before continuing. Authentication belongs in local Git configuration, never in these files.

The exact-file allowlist excludes other local contents and new files by default. `.gitignore` does not remove tracked files or old history, and `git add -f` bypasses it. Review the staged file list before every public commit.
