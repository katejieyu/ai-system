---
name: self-test-loop-skill
description: Stress-tests product logic through main flow simulation, edge cases, failure paths, and 3-perspective reviewer simulation. Produces a test verdict that is not allowed to be all-pass.
invoke: /self-test-loop-skill [selected hypothesis or current flow]
---

# Skill — Self Test Loop

## Purpose

Stress-test proposed product logic through realistic scenarios before committing to it. Find where it breaks — not where it works.

## Input

- Selected hypothesis (from Self Hypothesis)
- Current user flow
- V1 scope
- Open decisions
- Constraints

## Process

### Step 1 — Main Flow Test
Simulate the ideal path from start to finish.

Trace every step:
- What the user does
- What the system does
- What decisions are made
- What state changes occur

Identify:
- Steps where the behavior is undefined
- Steps that depend on unresolved open decisions
- Steps where the user has no clear feedback from the system

### Step 2 — Edge Case Test
Simulate at least 5 edge cases:

| Edge Case | What happens | System response | Defined behavior? | Severity |
|---|---|---|---|---|
| Missing or incomplete input | | | | |
| Invalid input | | | | |
| Partial completion / abandonment | | | | |
| Conflicting user intent | | | | |
| Concurrent or repeated actions | | | | |
| [add case specific to this product] | | | | |

### Step 3 — Failure Path Test
Identify where the system:
- Blocks progress without explanation
- Creates user confusion (multiple valid paths with no guidance)
- Breaks internal logic (state A + state B produces invalid state C)
- Produces output the user cannot act on
- Silently fails (failure happens but user does not know)

For each failure path: name the exact breakpoint and classify severity (Critical / Moderate / Minor).

### Step 4 — Reviewer Simulation
Briefly simulate review from 3 perspectives:

**User:** Does this flow make sense without a manual? Where would I stop or give up?
**PM:** Does this deliver the stated goal? What metric would prove it worked?
**Engineer:** What would break first? What is underspecified?

## Output

### Main Flow Findings
[Step-by-step trace with undefined/unclear states flagged]

### Edge Case Findings
[Table from Step 2, completed]

### Failure Paths
| Breakpoint | Failure type | Severity | Required fix |

### Reviewer Concerns
| Perspective | Concern | Severity |

### Test Verdict
- **Pass** — main flow works, edge cases handled, no Critical failures
- **Conditional** — works with named preconditions: [list them]
- **Fail** — Critical failures found: [list them]

## Rules

- If all verdicts are Pass, testing was not rigorous enough — re-run with harder scenarios
- Name exact breakpoints — no vague "could cause issues"
- Distinguish Critical (breaks core flow) from Moderate (degrades experience) from Minor (polish issue)
- Every Critical failure requires a fix before proceeding
