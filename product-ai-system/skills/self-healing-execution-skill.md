---
name: self-healing-execution-skill
description: Applies fixes directly to product logic, scope, flow, and decision rules based on the prioritized gap register. Produces an updated product state after every fix pass. Does not analyze — acts.
invoke: /self-healing-execution-skill [gap register + selected hypothesis + current flow + constraints]
---

# Skill — Self Healing Execution

## Purpose

Resolve the highest-priority gaps without introducing new contradictions. Every fix produces a concrete change — no vague "should improve" language.

## Input

- Gap register (from Gap Detection)
- Selected hypothesis
- Current product definition and flow
- Constraints
- System memory (known fixes for similar gaps)

## Process

### Step 1 — Select Fix Scope
Fix in this order:
1. All Critical gaps — no exceptions
2. Highest-impact Moderate gaps (by user harm + implementation dependency)
3. Do not touch Minor gaps in this pass unless they are trivially co-located with a Critical fix

If a gap cannot be fixed without user input: document it with an exact question and skip — do not guess.

### Step 2 — Apply Fixes
For each gap selected in Step 1:

```
FIX [n]
─────────────────────────────
Gap: [gap name and type]
What changes: [exact description — what is being added, removed, or rewritten]
Where it changes: [file / section / rule / flow step]
Before: [current state — exact text or "undefined"]
After: [new state — exact text, ready to use]
Side effect check: [does this create new dependencies? conflict with prior decisions? expand scope unintentionally?]
─────────────────────────────
```

Rules:
- "After" content must be production-ready — not a sketch
- Do not silently expand scope during a fix
- If a fix creates a new dependency, name it explicitly

### Step 3 — Check for Side Effects
After all fixes are applied, check as a batch:
- Do any two fixes contradict each other?
- Does any fix create a new gap not present before?
- Does any fix invalidate an existing decision or acceptance criterion?

If yes: resolve the contradiction before proceeding.

### Step 4 — Produce Updated State
Generate a complete updated view of the product state after all fixes:
- Updated product definition (what changed)
- Updated user flow (revised steps where applicable)
- Updated open decisions (resolved / newly opened)
- Updated risk register (risks closed / new risks introduced)

## Output

### Fix Log
| # | Gap | Fix Applied | Area Changed | Side Effect Risk |
|---|---|---|---|---|

### Updated Product State
[revised product definition — only sections that changed, with what changed noted]

### Updated User Flow
[numbered steps — only revised steps, marked as "UPDATED" or "NEW"]

### Updated Open Decisions
| Decision | Status | Owner | Notes |
|---|---|---|---|

### Remaining Open Questions
[gaps that could not be fixed without user input — each with exact question]

## Rules

- No vague "should improve" language — every fix must produce a concrete change
- Every fix must be applied to a specific section or rule — not a general area
- Do not silently expand scope
- Every Critical gap must be addressed or escalated with an exact question
- If a fix introduces a new Critical gap, route back to Gap Detection immediately
