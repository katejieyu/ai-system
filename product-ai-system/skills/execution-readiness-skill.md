---
name: execution-readiness-skill
description: Breaks the refined product definition into epics, tasks, acceptance criteria, dependencies, and a 0–100 readiness score. Produces output specific enough to hand to an engineering team without a kickoff meeting.
invoke: /execution-readiness-skill [refined product definition from Phase 10]
---

# Skill — Execution Readiness

## Purpose

Prepare the product for implementation. Produce execution-ready output: every task has one owner, one outcome, and is specific enough to start without a meeting.

## Input

- Refined product definition (from Self Healing Execution)
- Updated user flow
- Updated open decisions
- Gap register (remaining open items)
- Success metrics (from Define Goal)

## Process

### Step 1 — Break into Epics
Define work streams. Each epic is a distinct, independently schedulable body of work.

For each epic:
- Name (action-oriented, e.g., "Build authentication flow")
- Description — what it covers and why it exists
- Owner — one role, not a committee
- Dependencies — what must be complete before this epic can start

### Step 2 — Break Epics into Tasks
For each epic, define discrete, assignable tasks.

Each task must:
- Have exactly one owner
- Produce exactly one observable outcome
- Be specific enough to start without asking clarifying questions

Task format:
| Task | Owner | Depends on | Estimate (S/M/L) | Status |
|---|---|---|---|---|

### Step 3 — Define Acceptance Criteria
For each epic, define acceptance criteria that are:
- Observable — someone can verify them without interpretation
- Testable — they can be confirmed or denied with a specific check
- Not intentions — "users should be able to X" is not acceptable; "user completes X flow without error in under 30 seconds" is

| Epic | Criterion | How to Verify |
|---|---|---|

### Step 4 — Map Dependencies
Identify all external dependencies (teams, systems, APIs, decisions):

| Dependency | Type (Internal / External / Decision) | Status | Owner | Blocker? |
|---|---|---|---|---|

### Step 5 — Produce Readiness Score
Score from 0–100 based on:
- Are all Critical gaps closed? (40 points)
- Are all open decisions logged with owners? (20 points)
- Are all acceptance criteria observable and testable? (20 points)
- Are all external dependencies identified with owners? (10 points)
- Is the persona and journey current? (10 points)

Score thresholds:
- **90–100**: Ready to build — hand off to engineering
- **70–89**: Nearly ready — low risk to begin; named conditions must be met
- **50–69**: Key items unresolved — begin only with explicit risk acceptance from owner
- **Below 50**: Return to Phase 10 (Self Healing) or Phase 12 (Test)

### Step 6 — What Is Needed Before Build
List every remaining item that must be resolved before engineering begins:

```
PRE-BUILD CHECKLIST
─────────────────────────────
[ ] [item] — Owner: [role] — Urgency: [Critical / High / Medium]
[ ] [item] — Owner: [role] — Urgency: [Critical / High / Medium]
─────────────────────────────
```

## Output

### Epics
| Epic | Description | Owner | Dependencies |
|---|---|---|---|

### Tasks (per epic)
| Task | Owner | Depends on | Estimate | Status |
|---|---|---|---|---|

### Acceptance Criteria
| Epic | Criterion | How to Verify |
|---|---|---|

### Dependencies
| Dependency | Type | Status | Owner | Blocker? |
|---|---|---|---|---|

### Risks
| Risk | Owner | Likelihood | Severity | Mitigation |
|---|---|---|---|---|

### Readiness Score
**[0–100]** — [one sentence explaining the score and what is holding it back]

### Pre-Build Checklist
[from Step 6]

## Rules

- No unnamed owners — every task and decision has exactly one owner
- No unmeasurable acceptance criteria — rewrite any criterion that cannot be verified
- No vague tasks — if a task requires a meeting to clarify, it is not specific enough
- Every open decision from prior phases must appear in this output — resolved or assigned
- If Readiness Score is below 50: do not proceed — return to Self Healing Execution
