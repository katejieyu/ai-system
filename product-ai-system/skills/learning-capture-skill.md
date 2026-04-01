---
name: learning-capture-skill
description: Takes raw user input — answers, corrections, feedback, or requirements — and converts it into structured, implementation-ready system improvements. Classifies input, extracts actionable signal, checks for scope creep and contradictions, produces exact file changes.
invoke: /learning-capture-skill [user input or feedback]
---

# Skill — Learning Capture

## Purpose

Turn raw user interaction into implementation-ready system improvement. Input can be in any form — the output must always be a concrete change to a specific file and section.

## Input

- Direct answer to a learning loop question
- Unprompted correction
- "This output was wrong because..."
- New requirement or constraint
- Feature request
- Context addition (persona change, scope shift, constraint update)

## Process

### Phase 1 — Intake
Read the raw input exactly as given. Do not interpret it yet.

Record:
- **Raw Input** — verbatim, unchanged
- **Input Source** — Learning Loop response / Unprompted correction / Feature request / Bug report / Context addition
- **Input Length** — Short (1 sentence) / Medium (2–5 sentences) / Long (5+)
- **Clarity** — Clear / Ambiguous / Contradictory

If Clarity is Ambiguous or Contradictory: generate one clarifying question before proceeding to Phase 2. Do not guess.

### Phase 2 — Classification
Classify into exactly one primary type:

| Type | Definition | Example signal |
|---|---|---|
| **Gap** | System should do something it doesn't | "It never checks for X", "There's no step for Y" |
| **Bug** | System does something wrong | "It said X but should say Y", "This rule contradicts that one" |
| **Improvement** | System does it but could do better | "The output format is hard to read", "This step is too vague" |
| **Feature** | System doesn't do this at all | "I want it to also...", "Can it handle the case where..." |
| **Context** | Background that changes system behavior | "The target user has changed", "We no longer do X" |

Output:
- **Primary Type** — one of the above
- **Secondary Type** — if applicable
- **Classification Confidence** — High / Medium / Low + one-sentence reason

### Phase 3 — Signal Extraction
Extract the actionable core from the input. Strip opinion, preamble, and noise.

For each distinct signal:
```
SIGNAL [n]
─────────────────────────────
Raw fragment: [exact phrase or sentence the signal comes from]
Extracted signal: [the specific claim, requirement, or correction — one sentence]
Type: [Gap / Bug / Improvement / Feature / Context]
Scope: [which skill, workflow, section, or rule this applies to]
Specificity: [Specific — names exact behavior | General — describes category of issue]
─────────────────────────────
```

If a signal is General, add a Narrowing Question: one question that would make it Specific enough to act on.

### Phase 4 — Impact Assessment
For each Specific signal:

| Dimension | Answer |
|---|---|
| Files affected | [list] |
| Downstream effects | [does changing this break or conflict with anything?] |
| Reversibility | [if wrong, how hard to undo?] |
| Dependency | [does this require another change first?] |
| Conflict risk | [None / Low / High + what might conflict] |
| Implementation effort | [Immediate (single rule) / Short (section rewrite) / Structural (new skill/workflow)] |

### Phase 5 — Conversion
Convert each Specific, assessed signal into an implementation-ready change:

```
CHANGE [n]
─────────────────────────────
Signal: [extracted signal from Phase 3]
Type: [Gap / Bug / Improvement / Feature / Context]
File: [exact filename]
Section: [exact section name or "new section"]
Action: [Add / Modify / Remove / Create new file]

Before:
[current content — exact text, or "does not exist"]

After:
[new content — exact text, ready to copy into the file]

Rationale: [one sentence — why this change closes the gap or fixes the issue]
─────────────────────────────
```

Rules:
- "After" content must be production-ready — not a sketch or placeholder
- Do not change anything outside the named section
- If the change requires a new skill or workflow file, write the full file content

### Phase 6 — Integration Check
Before outputting the final change set:

1. Do any two changes in this set contradict each other?
2. Does any change contradict existing system rules NOT being changed?
3. Are all changes within the scope of what the user's input actually said, or did scope creep in?
4. Does any change introduce a new gap?

Output:
- **Contradictions found** — list, with resolution for each
- **Scope creep detected** — Yes / No — if Yes, what was removed and why
- **New gaps introduced** — Yes / No — if Yes, add to next learning cycle queue
- **Integration status** — Ready to apply / Blocked (with reason)

### Phase 7 — Output
Produce the final change set:

```
CAPTURE SUMMARY
─────────────────────────────
Input type: [primary classification]
Signals extracted: [n]
Changes generated: [n]
Files to modify: [list]
Scope creep removed: [Yes/No — what]
Contradictions resolved: [Yes/No — how]
Integration status: [Ready / Blocked]
─────────────────────────────
```

Followed by all CHANGE blocks from Phase 5.

If Integration status is Blocked: list exactly what needs to be resolved before applying.

## Rules

- Do not guess when input is ambiguous — ask one clarifying question and stop
- "After" content must be exact, production-ready text — never a placeholder
- Changes must be scoped to what the input actually said
- If a change would require rebuilding a core workflow, flag it and present the scope before applying
- Every change must produce a measurable improvement — not "make it better in general"
