---
tier: governance
load: on-self-check
---

# Loading

How an agent decides what to load beyond `core/`. Agent-neutral; engine adapters own runtime integration and private-home wiring.

## Always
All of `core/` — every agent, every turn. Also follow the host's configured bootstrap and always-on user context when present. Host-specific paths and optional dependencies are described in [README](../README.md).

`core/persona.md` always loads as shared character only. It cannot override behavior rules, user instructions, project instructions, runtime authority, or safety policy.

## Match, then load
1. **Discipline route** — the active agent matches the current task case-insensitively against complete trigger terms in each locally configured `rules/<d>/manifest.md`, when present. Any route match loads its always rules, all matching routes contribute the union of their conditional rules, and an explicit request for a named discipline or rule loads it directly. Runtime-supplied rules may satisfy this step, but the agent must not assume injection occurred.
2. **Relevance** — select the smallest sufficient skill set by `description`, preferring the most specific match; load multiple skills only when each covers a distinct required part of the task. Load on-relevance governance (`handoff`, `rule-authoring-style`) by purpose.
3. **Override** — "load X" / "this is personal" → load the requested user context, subject to its access policy.

## What loads
- **User** — load only the user context relevant to the task.
- **Disciplines** — non-exclusive; the active agent ensures the union of every matched manifest's always and conditional rules is loaded.
- **Skills** — a description is a router, not a reason to accumulate overlapping procedures. Always load a skill the user names explicitly; otherwise prefer one specific skill over several generic matches. Core rules are sufficient when no skill adds a necessary procedure. Precedence + skill-absent fallback: [behavior-rules](../core/behavior-rules.md).
- **Per-agent** — an opaque runtime home is not shared context. Load only current-runtime content explicitly routed by that runtime; shared policy assumes no internal paths.
- **Persona** — use the shared baseline plus exactly one current-runtime overlay. Never auto-load another agent's identity.

## Context access
For complex or high-risk work, state how brain context was reached: filesystem · MCP · pasted · unavailable. Broad classified read capability never expands the always-load set. If required context is unreachable, state the limitation and ask the user only when it materially blocks a reliable result.

## Runtime-state audits
For runtime, service, hook, cron, gateway, model-routing, or agent-home audits, resolve the active home, environment, process, checkout, and relevant logs before drawing conclusions. Never diagnose from a plausible path when the active runtime path is checkable.

## Skill-less contexts
Some paths load no skills and run rules-only: isolated scheduled tasks, connectors serving rules without skill bodies, or a skill that under-fires. Thin a rule toward its skill only where the skill is reachable and the rule keeps its irreducible minimum.

## Never auto-load
- User context classified private — load only an exact file explicitly routed or required by the user's current task.
- Relationship, family, friend, or household context is private. When explicitly needed, follow the host's configured private-context routing; if it uses `user/private/people/`, load `user/private/people/relationships.md` first, then only the named person files needed for the task.
- `reference/**` — explicit lookup only.
- Another agent's home, except when the user's current task explicitly places it in scope.
- `engine/**` — load only when maintaining the engine.

## Minimal
Load only what the task needs. Never load every discipline or every plausible skill just in case. A large context slice signals bloat → split or prune it during maintenance.

## When detection misses
Under-load (the user flags missing context) → add a keyword to the discipline's manifest. Wrong-load (the user corrects) → remove the misleading keyword.
