---
name: self-study-skill
description: Reviews all prior phases as a single body of work. Finds recurring weaknesses, drift between goals and solution, and what the cycle got right vs. what still needs work. Produces meta-findings that inform the test phase.
invoke: /self-study-skill [full cycle output from Phases 1–10]
---

# Skill — Self Study

## Purpose

Step back from individual phases and read the entire cycle output as one artifact. Find patterns, drift, and blind spots that are invisible when looking at phases in isolation.

## Input

- All phase outputs from the current cycle (Phases 1–10)
- Gap register
- Fix log

## Process

### Step 1 — Read as a Single Body of Work
Read all outputs from Phases 1–10 without phase boundaries. Look for:
- The same ambiguity appearing in multiple phases
- Goals stated in Phase 3 that are not traceable to the solution in Phase 6
- Assumptions from Phase 1 that were never resolved
- Decisions deferred in Phase 6 that were already deferred in Phase 4
- Fixes in Phase 10 that address symptoms rather than root causes

### Step 2 — Detect Drift
Compare Phase 3 goals directly against Phase 6 solution:

| Goal | Metric | Traceable in Solution? | Drift found? |
|---|---|---|---|

If a goal has no traceable element in the solution: flag as drift.
If the solution contains elements not traceable to any goal: flag as scope creep.

### Step 3 — Find Recurring Weaknesses
Identify problems that appeared in more than one phase:

| Problem | Phases affected | How many times | Root pattern |
|---|---|---|---|

A "root pattern" is the underlying reason the problem keeps appearing (e.g., "goal was defined too vaguely to produce specific requirements").

### Step 4 — Assess What the Cycle Got Right
State specifically:
- What the problem definition got right
- What the solution got right
- What the challenge phase caught that would have been missed otherwise
- What the gap detection found that the challenge missed

### Step 5 — Assess What Still Needs Work
State specifically:
- What is still ambiguous after 10 phases
- What decisions are still unmade
- What the test phase should focus on (not "test everything" — identify the riskiest areas)

## Output

### Observed Patterns
[list — recurring themes across phases]

### Repeated Problems
| Problem | Phases Affected | Times Appeared | Root Pattern |
|---|---|---|---|

### Drift Findings
| Goal | Drift type | Where it appeared | Impact |
|---|---|---|---|

### What the Cycle Got Right
[specific list — not generic praise]

### What Still Needs Work
[specific list — not generic concerns]

### Test Focus Recommendations
[for Phase 12 — the 3 riskiest areas that need hardest scrutiny]

### Improvement Opportunities
[things the system itself should do differently next time — feed into Learning Loop]

## Rules

- Do not repeat phase outputs verbatim — synthesize
- "Drift" means the solution does not address a stated goal — name the specific goal and where it is missing
- "Scope creep" means the solution contains something not in the goals — name the specific element
- Test Focus Recommendations must be specific — not "test the whole solution"
