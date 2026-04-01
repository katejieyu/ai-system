# System Orchestrator

## Purpose

Route commands into the correct workflow, enforce execution order, trigger loops, and decide when to re-run, stop, or escalate.

---

## Modes

### Mode: Run
**Use when:** Starting from a new product idea, vague problem, or early concept.
**Workflow:** `workflows/product-full-cycle-workflow.md`
**Follow-on:** Route to Learning Loop if unresolved gaps remain after cycle.

### Mode: Evolve
**Use when:** A draft solution exists and needs more rigor, or critical gaps were found.
**Workflow:** `workflows/product-self-evolution-workflow.md`
**Follow-on:** Route to Learning Loop after completion.

### Mode: Learn
**Use when:** User answers, corrections, or feedback are available.
**Workflow:** `workflows/learning-loop-workflow.md`
**Follow-on:** Re-run if Critical gaps remain. Stop when exit criteria are met.

### Mode: Feature Update
**Use when:** A new feature request changes scope, behavior, or user flow.
**Workflow:** `workflows/feature-change-loop-workflow.md`
**Follow-on:** Route to Evolve, then Learning Loop.

---

## Routing Logic

1. Input is a new idea or unstructured problem → **Run**
2. Input is an existing product state needing challenge → **Evolve**
3. Input includes explicit feedback, corrections, or "this is wrong/missing" → **Learn**
4. Input adds or changes a feature → **Feature Update**
5. Uncertain → **Run**

---

## Mandatory Follow-ons

| After | Always run next |
|---|---|
| Run | Learning Loop (if unresolved gaps) |
| Evolve | Learning Loop |
| Feature Update | Evolve → Learning Loop |
| Learning Loop (Critical gaps remain) | Learning Loop again |
| Learning Loop (exit criteria met) | Stop |

---

## Loop Behavior

Before each loop iteration:
1. Read `system-memory.md` — check Stored Patterns and Known Fixes for the current domain
2. Apply any matching known fixes before running the skill chain
3. Check `exit-criteria.md` — if met, stop
4. If neither: continue with remaining gaps as input

**Maximum loop depth:** 3 iterations without new progress. At that point, document all remaining open gaps with explicit owners and halt.

---

## Memory Integration

**Before every mode execution:**
- Read `system-memory.md` — check Stored Patterns and Known Fixes
- Apply matching known fixes before running the skill chain
- Skip reasoning steps that would only reproduce a known result

**After every Learning Loop completion:**
- Write Cycle Log to `system-memory.md`
- Log: gaps found, fixes applied, patterns observed, recurring issues flagged

---

## Execution Sequence — Full Run

```
[/product-ai-system run [problem]]

1. Read system-memory.md → apply known fixes for this problem type
2. Execute product-full-cycle-workflow.md (Phases 1–16)
3. Produce: Cycle Summary + Unresolved Gaps + Readiness Score
4. If unresolved gaps remain → route to learning-loop-workflow.md
5. Write to system-memory.md
6. Check exit-criteria.md → if met: finalize output and stop
7. If not met: loop Learning Loop with remaining gaps (max 3 iterations)
8. Final output: Cycle Summary + Change Log + Memory Update
```

---

## Execution Sequence — Feature Update

```
[/product-ai-system feature-update [feature]]

1. Execute feature-change-loop-workflow.md
   → identify what changed, what is now wrong
2. Route to product-self-evolution-workflow.md
   → fix internal logic gaps caused by the feature change
3. Route to learning-loop-workflow.md
   → ask user targeted questions about the new feature
   → apply improvements, write to system-memory.md
4. Check exit-criteria.md → if met: stop. If not: loop.
```

---

## Orchestrator Decision Output

After routing, state:

```
ORCHESTRATOR DECISION
─────────────────────────────
Trigger: [what was received]
Selected mode: [Run / Evolve / Learn / Feature Update]
Reason: [one sentence]
Workflow: [filename]
Memory check: [patterns or fixes applied / none]
Next follow-on: [what runs after]
─────────────────────────────
```
