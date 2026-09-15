---
tier: governance
load: on-relevance
---

# Rule-authoring style

How to write any rule, skill, or policy here. Applies whenever you author or revise agent-facing content.

## Write what to do
- State the desired behavior as a positive directive ("do X", "prefer Y"). Positive instructions steer more reliably than bare prohibitions.
- Reserve prohibitions for genuine hard boundaries (guardrails). When you must forbid, pair it with the positive alternative ("instead, do Z") — naming a thing raises its salience (the "pink elephant" effect), so the forbidden token should never be the last or only signal.
- Use emphasis (MUST / NEVER) sparingly, only on true guardrails. Stacked emphatic markers get over-weighted and crowd out the rest.

## Show, don't enumerate
- Teach with ~3–5 canonical worked examples plus a heuristic, not an exhaustive edge-case or prohibition list. Examples are among the most reliable ways to steer.
- Keep edge cases — carry them as varied examples, not as a list to memorize.
- More examples are not better: irrelevant or excessive ones degrade behavior. Select for relevance.

## Right altitude
- Write heuristics and principles — broad enough to generalize, specific enough to steer. Prefer them over brittle hardcoded step-lists.
- Keep the constitution (`core/`) broad. Put concrete, specific rules where conflicts actually need resolving; broad principles are followed least reliably in exactly those under-specified cases.

## Resolve conflicts at authoring time
- When two rules could clash, remove the clash in the text. A stated precedence ordering adds auditability, not measurable runtime obedience — so fix the conflict, don't paper it with a "X wins" line.

## Stay tight
- Every word earns its place (the `core/preferences.md` wording floor). One home per fact; link, don't restate.

---
**Basis:** Anthropic prompting best-practices (positive framing) · context-engineering (right altitude, canonical examples over edge lists) · negation + over-prompting research (salience mechanism, example cap) · IHEval (conflict is the real failure mode; runtime precedence is not a fix). Full sources are not bundled in this repository; this attribution is not independently verified here.
