---
name: self-hypothesis-skill
description: Generates multiple solution directions grounded in the clarified problem, compares them, and selects a working hypothesis and fallback before any solution is built.
invoke: /self-hypothesis-skill [restated problem, assumptions, constraints, target outcomes]
---

# Skill — Self Hypothesis

## Purpose

Generate alternative solution directions before committing to one. Prevent the system from solving a problem in the first way it thinks of.

## Input

- Restated problem (from Self Inquiry)
- Validated assumptions
- Constraints
- Target outcomes (from Define Goal)

## Process

### Step 1 — Generate 3 Hypotheses
Produce exactly 3 distinct hypotheses. They must be genuinely different — not variations of the same idea.

For each hypothesis define:
- **Core idea** — the fundamental approach, in one sentence
- **User behavior enabled** — what the user can do that they couldn't before
- **Trade-off** — what this approach gives up
- **Why it might work** — grounded rationale, not wishful thinking
- **Why it might fail** — specific failure condition

Rules:
- One hypothesis must be conservative — minimal change, low risk
- One hypothesis must be more ambitious — higher user value, higher risk
- One hypothesis may be a novel framing — different problem model entirely

### Step 2 — Compare
Evaluate each hypothesis on:

| Hypothesis | Simplicity | Feasibility | User Value | Risk | Speed to Validate |
|---|---|---|---|---|---|

Rate each dimension: High / Medium / Low.

### Step 3 — Select Working Hypothesis
Choose one primary hypothesis and one fallback based on the comparison.

State:
- Why primary was chosen over the others
- Under what conditions you would switch to the fallback
- What must be tested first to validate the primary hypothesis

## Output

### Hypothesis Table
| # | Hypothesis | Core Idea | User Value | Risk | Feasibility |
|---|---|---|---|---|---|

### Selected Direction
- **Primary:** [hypothesis name + one-sentence summary]
- **Fallback:** [hypothesis name + one-sentence summary]
- **Reason for selection:** [specific rationale]
- **Switch condition:** [what would cause fallback to be chosen instead]

### Testing Priorities
1. [highest-risk assumption — what must be tested first]
2. [second priority]
3. [third priority]

## Rules

- Minimum 3 hypotheses — never select without comparison
- One must be conservative, one more ambitious
- Selection must be explained — not just named
- Do not merge hypotheses — keep them distinct
- Do not generate the solution here — only the direction
