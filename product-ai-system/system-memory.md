# System Memory

Stores what the system has learned across all cycles. Read before every run. Write after every learning cycle.

This is not a log of what happened. It is a structured record of what the system now knows — patterns, fixes, decisions, and signals that would otherwise be re-discovered from scratch each time.

---

## How to Use

**Before any run:**
→ Read Stored Patterns and Known Fixes
→ Check if the current problem domain matches any entry
→ Apply matching known fixes before running the skill chain
→ Skip reasoning steps that would only reproduce a known result

**After every learning cycle:**
→ Write new entries to the relevant sections below
→ If an entry already exists for this pattern, update it — do not duplicate
→ If a fix was applied 3+ times, promote it to a standing rule in the main system file

---

## Section 1 — Stored Patterns

Recurring structures observed across multiple runs. Describe how a class of problem tends to behave, not a single instance.

| Pattern | Domain | Observed in | Times seen | Description |
|---|---|---|---|---|
| *(none yet)* | | | | |

**Format for new entries:**
```
Pattern: [name]
Domain: [product / execution / diagnosis / solution / challenge / etc.]
First observed: [cycle date or run description]
Times seen: [n]
Description: [what this pattern looks like when it appears]
Signal: [what in the input or output indicates this pattern is present]
Implication: [what the system should do differently when this pattern is detected]
```

---

## Section 2 — Known Fixes

Fixes that have been applied and confirmed to work. Apply immediately when the triggering condition is detected — do not re-derive them.

| Fix | Trigger condition | Applied to | Times applied | Confirmed |
|---|---|---|---|---|
| *(none yet)* | | | | |

**Format for new entries:**
```
Fix: [name]
Trigger: [the exact gap, error, or condition this fix addresses]
Applied to: [skill / workflow / section]
What it does: [exact change — what was added, removed, or rewritten]
Times applied: [n]
Confirmed: [Yes — date first confirmed / Provisional — not yet re-tested]
```

**Promotion Rule:** A Known Fix applied 3+ times → promote to the main system as a standing rule → mark entry as `Promoted to system — [date] — [file]` → remove from Known Fixes.

---

## Section 3 — Recurring Issues

Issues that have appeared in more than one cycle and have not yet been permanently resolved.

| Issue | First seen | Times recurred | Status | Owner |
|---|---|---|---|---|
| *(none yet)* | | | | |

**Format for new entries:**
```
Issue: [description]
Root cause: [known / suspected / unknown]
First seen: [cycle date or context]
Times recurred: [n]
Attempted fixes: [list — what was tried and what happened]
Status: [Open / Partially resolved / Resolved]
Resolution path: [what needs to happen to close this permanently]
```

---

## Section 4 — Known Edge Cases

Inputs or conditions that caused the system to produce wrong or incomplete output.

| Edge case | Triggered by | Failure mode | Correct behavior | Fixed |
|---|---|---|---|---|
| *(none yet)* | | | | |

**Format for new entries:**
```
Edge case: [description]
Triggered by: [what input or condition caused it]
Failure mode: [what the system did wrong]
Correct behavior: [what should happen instead]
Applied fix: [Yes — what was changed / No — still open]
```

---

## Section 5 — Product Decisions

Decisions made during product cycles. Stored so the system does not re-debate settled questions.

| Decision | Rationale | Trade-off | Owner | Cycle date |
|---|---|---|---|---|
| *(none yet)* | | | | |

**Format for new entries:**
```
Decision: [what was decided]
Options considered: [what alternatives were evaluated]
Rationale: [why this option was chosen]
Trade-off: [what was given up]
Owner: [who made the decision]
Cycle date: [when this was decided]
Still valid: [Yes / No — if No, flag for re-evaluation]
```

---

## Section 6 — User Signals

Explicit preferences, recurring requests, and persistent constraints from users.

| Signal | Source | First seen | Times seen | Applied |
|---|---|---|---|---|
| *(none yet)* | | | | |

**Format for new entries:**
```
Signal: [explicit user preference, recurring request, or persistent constraint]
Source: [Learning Loop response / direct correction / feature request]
First seen: [date or context]
Times seen: [n]
Applied: [Yes — where / No — pending]
```

---

## Cycle Log Index

A chronological index of all learning cycles. Full logs are stored in learning loop output.

| Cycle | Date | Gaps found | Gaps closed | Files changed | Open gaps carried forward |
|---|---|---|---|---|---|
| *(none yet)* | | | | | |
