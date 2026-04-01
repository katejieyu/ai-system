---
name: learning-loop-workflow
description: Self-learning loop that detects gaps after a cycle, asks the user targeted questions, captures answers as structured data, converts them into permanent system improvements, applies changes, and re-runs evolution. This is system evolution, not feedback collection.
invoke: /product-ai-system learn [cycle output or feedback]
---

# Workflow — Learning Loop

## Purpose

Turn what the system got wrong, missed, or left vague into permanent system improvements. Runs after every full cycle or on demand.

## When to Use

- Auto-triggered after `run` when unresolved gaps remain at Phase 16
- Auto-triggered after `evolve`
- Invoked manually: `/product-ai-system learn [feedback or output]`

## Default Trigger Prompt

At the end of Phase 16, if Unresolved Gaps remain, the system asks:
> "Run learning mode to convert unresolved gaps into system improvements? (yes / skip)"

If yes: run this workflow.
If skip: log gaps to `system-memory.md` and stop.

## Steps

### Step 1 — Gap Detection
Read the most recent cycle output as a complete artifact.

Identify:
- Phases that produced vague, incomplete, or low-confidence output
- Sections where assumptions were not resolved
- Outputs flagged as Unresolved Gaps
- Decisions deferred without an owner or resolution path
- Areas that would not survive scrutiny from an engineer or PM

Output:
```
DETECTED GAPS
─────────────────────────────
| Gap | Phase/Section | Type (Logic/Coverage/Assumption/Output Quality) | Severity (Critical/Moderate/Minor) |
Focus Areas: [top 3 — Critical first, then highest-impact Moderate]
Gap Count: Critical [n] / Moderate [n] / Minor [n]
─────────────────────────────
```

### Step 2 — Question Generation
For each Focus Area, generate 1–2 targeted questions for the user.

Rules:
- Questions must be specific to the gap — not generic
- Each question must produce an answer that directly closes or narrows the gap
- No more than 5 questions total per cycle
- If a gap can be resolved by the system without user input, resolve it in Step 5 instead
- Questions must be answerable in 1–3 sentences

Output format:
```
QUESTION [n]
─────────────────────────────
Question: [question text]
Gap it addresses: [gap name from Step 1]
What a good answer looks like: [short description of useful vs. useless answer]
─────────────────────────────
```

### Step 3 — User Input Capture
Present questions to the user. Wait for responses.

For each response, capture:
```
INPUT RECORD
─────────────────────────────
Question: [question text]
User Answer: [verbatim answer]
Gap Addressed: [gap name]
Input Type: [Gap / Bug / Improvement / Feature / Context]
Signal Quality: [High / Medium / Low — one-sentence reason]
Actionable: [Yes / No — if No, state what would make it actionable]
─────────────────────────────
```

If user says "skip": log as unresolved, carry forward to next cycle in `system-memory.md`.

### Step 4 — System Reflection
Read all Input Records as a batch.

Determine:
- Which gaps are now Closed (answer actionable and sufficient)
- Which gaps are Partial (answer narrows gap but more is needed)
- Which gaps remain Open (no useful input received)
- Whether any answer reveals a secondary gap not detected in Step 1

Output:
```
REFLECTION
─────────────────────────────
| Gap | Status (Closed/Partial/Open) | What changed |
Secondary Gaps Found: [list — add to next cycle queue]
Reflection Summary: [one paragraph — what the system now knows that it didn't before]
─────────────────────────────
```

### Step 5 — Improvement Generation
For every Closed or Partial gap, generate a concrete improvement.

Each improvement must be one of:
- **Logic fix** — a rule, constraint, or instruction that was missing or wrong
- **Output format fix** — a section or field that was absent or unclear
- **Scope update** — something in/out of scope that wasn't defined
- **New skill** — a reasoning step that needs to exist as a standalone skill
- **New workflow** — a sequence of steps that needs to be named and reusable

Output per improvement:
```
IMPROVEMENT [n]
─────────────────────────────
Type: [Logic fix / Output format fix / Scope update / New skill / New workflow]
Gap it closes: [gap name]
What changes: [exact description]
Where it applies: [file + section]
Implementation: [the actual new text, rule, or structure — ready to apply]
─────────────────────────────
```

Do not generate improvements for Open gaps. Log them for next cycle.

### Step 6 — Apply Changes
Apply every improvement from Step 5.

For each:
1. State the file being modified
2. State what was there before (or "new section")
3. Apply the change with exact new content
4. Confirm consistency with the rest of the system

Log every change:
```
CHANGE LOG
─────────────────────────────
File: [filename]
Section: [section name]
Change type: [Added / Modified / Removed]
Summary: [one sentence — what changed and why]
─────────────────────────────
```

If a change requires user confirmation before applying, state it explicitly and wait.

### Step 7 — Re-Run Local Evolution
After changes are applied, run a compressed self-evolution check on updated areas only:
1. Re-read modified sections
2. Check for contradictions with unchanged sections
3. Confirm changes close the gaps they were designed to close
4. Check that no new gaps were introduced

Output:
- **Consistency Check** — Pass / Fail per modified section
- **Gap Closure Confirmation** — table: gap + closed? + evidence
- **New Gaps Introduced** — if any, add to next cycle queue

### Step 8 — Learning Cycle Log
Produce a permanent record of this learning cycle. Write to `system-memory.md`.

```
LEARNING CYCLE LOG
─────────────────────────────
Cycle date: [date]
Triggered by: [cycle output / manual / scheduled]
Gaps detected: [n] — Critical: [n] / Moderate: [n] / Minor: [n]
Questions asked: [n]
User responses received: [n]
Gaps closed: [n]
Improvements applied: [n]
Files modified: [list]
Open gaps carried forward: [list with owners]
─────────────────────────────
```

## Exit Rule

The learning loop terminates when:
- All Critical and Moderate gaps are Closed or documented with an explicit owner and resolution path
- No new Critical gaps were introduced by the changes applied

If open Critical gaps remain after Step 7, loop back to Step 2 with those gaps as the focus.
Reference `exit-criteria.md` at end of each loop iteration.
