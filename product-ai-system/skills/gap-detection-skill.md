---
name: gap-detection-skill
description: Identifies logic gaps, UX gaps, scope gaps, and ownership gaps in the current product state. Produces a prioritized gap register with recommended fix order.
invoke: /gap-detection-skill [test results, current flow, or product state]
---

# Skill — Gap Detection

## Purpose

Convert weak areas into a prioritized, actionable list of gaps. Every gap must be specific enough to act on.

## Input

- Test findings (from Self Test Loop)
- Unresolved questions from any prior phase
- User feedback or corrections
- Current product definition and flow

## Process

### Step 1 — Extract Gaps
Identify gaps across five types:

| Gap Type | Definition | What to look for |
|---|---|---|
| **Logic gap** | A rule, constraint, or decision that is missing or contradictory | Two rules that conflict; a condition with no defined behavior |
| **Flow gap** | A step in the user journey that is undefined, unreachable, or broken | Missing steps; steps that can't complete; undefined next actions |
| **UX clarity gap** | The user cannot understand what to do or what happened | No feedback state; ambiguous labels; unexplained errors |
| **Scope gap** | Something is in scope but not defined, or assumed out of scope but needed | Features referenced but not designed; edge cases ignored |
| **Ownership gap** | A decision or task has no owner | Open decisions with no assignee; acceptance criteria with no verifier |

### Step 2 — Classify Each Gap
For each gap identified:

| Gap | Type | Severity | Affected Area | Impact if Ignored | Owner Needed |
|---|---|---|---|---|---|

Severity definitions:
- **Critical** — blocks core user flow or makes acceptance criteria untestable
- **Moderate** — degrades quality or creates ambiguity that will become a blocker in engineering
- **Minor** — polish or edge case that does not block the core flow

### Step 3 — Prioritize
Rank all gaps by:
1. Criticality (Critical first)
2. User harm (what breaks from the user's perspective)
3. Implementation dependency (what other work is blocked by this gap)
4. Product risk (what could fail silently)

### Step 4 — Recommend Fix Order
Categorize all gaps into fix tiers:
- **Immediate** — must be resolved before the next phase proceeds
- **Short-term** — must be resolved before engineering begins
- **Structural** — requires a new skill, workflow, or system change

## Output

### Gap Register
| # | Gap | Type | Severity | Affected Area | Impact | Owner Needed |
|---|---|---|---|---|---|---|

### Top Priorities
1. [Critical gap #1 — what it is and why it is highest priority]
2. [Critical gap #2]
3. [Highest-impact Moderate gap]

### Recommended Fix Order
**Immediate:** [list]
**Short-term:** [list]
**Structural:** [list]

### Gap Summary
- Total gaps: [n]
- Critical: [n]
- Moderate: [n]
- Minor: [n]

## Rules

- Every Critical gap must have an explicit next action — not just a label
- Do not mix symptom and root gap in one row — separate them
- If a gap cannot be fixed without user input, state the exact question needed
- Do not list "could be improved" items as gaps — only items that are missing or broken
