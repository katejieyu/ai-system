# Workflow — Product Self Evolution

## Purpose

Continuously improve an existing product definition by questioning, testing, detecting, and fixing weak areas. Operates on an existing draft — not used to start from scratch.

## When to Use

- Invoked by: `/product-ai-system evolve`
- Auto-triggered after: `run` when Critical gaps remain
- Auto-triggered after: `feature-update`

## Steps

### Step 1 — Self Inquiry
Run `skills/self-inquiry-skill.md`.
Challenge current assumptions. Identify framing risks and contradictions. Generate 5–8 critical questions about the current state.

### Step 2 — Self Hypothesis
Run `skills/self-hypothesis-skill.md`.
Generate 3 alternative directions for resolving identified gaps. Select working hypothesis and fallback.

### Step 3 — Self Test Loop
Run `skills/self-test-loop-skill.md`.
Simulate main flow, edge cases, and failure paths against the updated hypothesis. Produce test verdict.

### Step 4 — Gap Detection
Run `skills/gap-detection-skill.md`.
Identify all logic gaps, UX gaps, scope gaps, and ownership gaps. Produce prioritized gap register.

### Step 5 — Self Healing Execution
Run `skills/self-healing-execution-skill.md`.
Fix all Critical and Moderate gaps. Produce updated product state, updated flow, and remaining open questions.

### Step 6 — Re-Test
Re-run `skills/self-test-loop-skill.md` on modified areas only.
Confirm that fixes closed the gaps they were designed to close.
Check that no new gaps were introduced by the changes.

### Step 7 — Exit Check
Check `exit-criteria.md`.
- If Tier 1 met: route to Learning Loop, then stop.
- If Critical gaps remain: loop back to Step 1 with remaining gaps as input.
- Maximum 3 iterations. If 3 iterations complete without meeting exit criteria: document all open gaps with owners and escalate to user.

## Repeat Rule

Repeat Steps 1–7 until:
- No Critical gaps remain, **OR**
- All unresolved issues have explicit owners and documented resolution paths

## Output Per Iteration

```
EVOLUTION ITERATION [n]
─────────────────────────────
Gaps entering this iteration: [list]
Self Inquiry findings: [key assumption challenges]
Hypothesis selected: [primary + fallback]
Test verdict: [Pass / Conditional / Fail]
Gaps resolved: [list]
Gaps remaining: [list with owners]
Files modified: [list]
Exit check: [Continue / Stop — reason]
─────────────────────────────
```
