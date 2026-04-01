# Workflow — Product Full Cycle

## Purpose

Run a complete product cycle from idea to stable, testable, execution-ready product definition.

## When to Use

Invoked by: `/product-ai-system run [idea or problem]`

## Steps

### Phase 1 — Define Issue
Extract target users, pain points, and context. Rewrite the issue in one sentence. Flag assumptions and unknowns.

### Phase 2 — Diagnose Problem
Ask "why?" per root cause. Identify structural causes, workflow gaps, dependencies, and constraints.

### Phase 3 — Define Goal
Define measurable user and business outcomes. Every goal gets a metric. Name non-goals and trade-offs.

### Phase 4 — Self Inquiry
Run `skills/self-inquiry-skill.md`.
Challenge the framing before generating any solution.

### Phase 5 — Self Hypothesis
Run `skills/self-hypothesis-skill.md`.
Generate 3 solution directions. Compare and select one working hypothesis plus a fallback.

### Phase 6 — Generate Solution
Build a grounded V1 solution from the selected hypothesis. Name specific behaviors. Keep scope to V1.

### Phase 7 — Challenge Solution
Assume the solution has problems. Find weak points, hidden risks, undefined states, and edge cases. Minimum: 3 weak points, 3 missing decisions, 4 critical questions.

### Phase 8 — Self Test Loop
Run `skills/self-test-loop-skill.md`.
Simulate main flow, edge cases, failure paths. Reviewer simulation from user, PM, engineer perspectives.

### Phase 9 — Gap Detection
Run `skills/gap-detection-skill.md`.
Identify logic gaps, UX gaps, scope gaps, and ownership gaps. Produce a prioritized gap register.

### Phase 10 — Self Healing Execution
Run `skills/self-healing-execution-skill.md`.
Fix all Critical and Moderate gaps. Produce updated product state and updated flow.

### Phase 11 — Self Study
Run `skills/self-study-skill.md`.
Review all prior phases as a single body of work. Find recurring weaknesses, drift between goals and solution, and what still needs work.

### Phase 12 — Test (4 Perspectives)
Simulate review from: User, PM, Designer, Engineer.
Hold each perspective separately. Verdict per perspective: Pass / Fail / Conditional.

### Phase 13 — Execution Readiness
Run `skills/execution-readiness-skill.md`.
Break into epics, tasks, acceptance criteria. Produce readiness score 0–100.

### Phase 14 — Persona & Journey Refresh
Run `skills/persona-journey-refresh-skill.md`.
Refresh persona and user journey to reflect the latest product state.

### Phase 15 — README Sync
Run `skills/readme-sync-skill.md`.
Update documentation to reflect current state, commands, and capabilities.

### Phase 16 — Exit Criteria Check
Check `exit-criteria.md`.
- If Tier 1 met: finalize output and stop.
- If Critical gaps remain: route to `product-self-evolution-workflow.md`.
- If unresolved gaps + user input available: route to `learning-loop-workflow.md`.

## Loop Rule

If Critical gaps remain after Phase 16, continue with `workflows/product-self-evolution-workflow.md`.
Maximum 3 iterations before escalating to user.

## Final Output

```
CYCLE SUMMARY
─────────────────────────────
Final Problem Definition: [one sentence]
Final Goal: [user outcome + business outcome]
Final V1 Solution: [one paragraph]
Top Risks:
- [risk] — Likelihood: H/M/L | Owner: [role]
Readiness Score: [0–100] — [reason]
Unresolved Gaps: [list with owners]
Recommended Next Step: [single most important action before build]
─────────────────────────────
```
