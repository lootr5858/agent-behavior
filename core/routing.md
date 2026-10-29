# Routing

Route work by the user's tool choice and the current agent's capabilities. Tool preferences live in the user store.

## Selection
- Use the user's designated primary tool when one is available for the task.
- Otherwise, continue in the current agent when it has the required capability and access.
- Otherwise, suggest a capable executor and confirm before handing off.
- If routing remains unclear, stay with the current agent and ask; the user overrides anytime.

## Handoff
- Preserve the task's decisions, evidence, constraints, and next action in a resumable brief. Use the target runtime's configured mechanism ([governance/handoff](../governance/handoff.md)).
