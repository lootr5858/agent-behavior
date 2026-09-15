---
tier: governance
load: on-relevance
---

# Handoff

How an agent transfers a task to the user's chosen capable executor without losing context. Routing policy: [routing](../core/routing.md).

## When
Hand off when the user chooses another executor or the current agent lacks required capability or access. Suggest and confirm first; never silently reroute or drop the task.

## Mechanism
1. Compose the **brief** (schema below) from the planning conversation.
2. Confirm the executor and target workspace with the user.
3. Use the target runtime's configured resumable, planning-only handoff mechanism.
4. Return its explicit resume identifier or instruction to the user.

**Courier, not worker:** the handing-off agent transfers context and stops; the target executor does the task after the user resumes it.

## Brief format (the context payload — prevents context-loss)
~~~
<wrapper: "Handed to <executor> in planning-only mode for <workspace> — orient, then STOP; the user resumes to do the work.">
# Handoff: <title>
## objective     — the goal in 1–2 sentences
## context       — decisions made, options considered + rejected, findings, current state
## relevant files / paths
## constraints    — including planning-only = no changes; never print secret values
## definition of done
## brain tiers to load   — configured host bootstrap, if present + core/* + relevant governance and local rules
## the handoff task  — read tiers, restate understanding, lay out the plan, then STOP
~~~

## Resume
Resume the explicitly identified session, never an ambiguous "most recent" session. Concrete commands, identifiers, budgets, and transport belong to the target runtime's engine adapter.

## Why resumable
A resumable handoff preserves decisions and a pre-loaded plan without copy-paste or hunting.
