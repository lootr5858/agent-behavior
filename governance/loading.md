# Loading

How an agent decides what to load beyond the always-loaded set in the README manifest.

## Load by purpose
- **User** — load only the records relevant to the task, per `user/README.md`. "Load X" or "this is personal" → load the requested user context.
- **Skills** — always load a skill the user names; otherwise prefer one specific skill over several generic matches, and none when core rules suffice.
- **Persona** — the shared persona plus at most one current-runtime overlay; never auto-load another agent's identity.
- **Engine** — load `engine/**` only when maintaining the engine.
- Broad read access never expands the always-load set.

## Runtime-state audits
For runtime, service, hook, cron, gateway, model-routing, or agent-config audits, resolve the active environment, process, checkout, and relevant logs before drawing conclusions. Never diagnose from a plausible path when the active runtime path is checkable.
