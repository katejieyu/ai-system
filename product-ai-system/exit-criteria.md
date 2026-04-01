# Exit Criteria

Defines when the system stops looping. Applied at the end of every Evolve, Learn, and Feature Update cycle.

Check in order. Stop as soon as the conditions for the applicable tier are met.

---

## Tier 1 — Hard Stop

The loop MUST stop when ALL of the following are true:

- [ ] No Critical gaps remain — every Critical gap is Closed or has an explicit owner and documented resolution path
- [ ] No contradictory logic — no two rules, instructions, or outputs produce opposing results for the same input
- [ ] All outputs are executable — every task has an owner, every decision is logged, every acceptance criterion is observable and testable
- [ ] No blocked fixes — every gap is resolved or escalated to the user with a specific question
- [ ] Persona and journey reflect the latest scope
- [ ] README reflects the latest system state

---

## Tier 2 — Soft Stop (marginal improvement check)

If Tier 1 conditions are met but you are considering running another iteration, check:

- Are the remaining open items Minor severity only?
- Did the last iteration close fewer gaps than the previous one?
- Have the same gaps appeared in 2+ consecutive iterations without being closed?
- Has the system run 3+ iterations without new progress?

If 2 or more are true: stop. Document remaining gaps in `system-memory.md` and halt.

---

## Do Not Stop If

- A core decision is still implicit — not logged, not owned
- A key workflow breaks in testing
- The solution depends on unvalidated assumptions
- A new feature was added without re-testing
- User feedback has been captured but not integrated
- A new Critical gap was introduced by the most recent change

---

## Override Conditions

The loop continues regardless of exit criteria if:
- A new Critical gap was introduced by the most recent change (a fix created a new problem)
- The user explicitly requests another iteration
- A change applied in the last iteration contradicts an existing system rule not in scope for that iteration

In these cases: state the override reason, run one more iteration targeted at the override condition only, then re-check exit criteria.

---

## Finalization Steps

When the exit condition is reached:

1. Write Cycle Log to `system-memory.md`
2. Produce final output:
   - Final problem definition (one sentence)
   - Final goal (user outcome + business outcome)
   - Final V1 solution (one paragraph)
   - Top risks (likelihood + owner per risk)
   - Readiness Score (0–100 with reason)
   - Open gaps deferred (each with owner and resolution path)
3. State exit reason — which tier was reached and which conditions were met

---

## Exit Check Output

```
EXIT CHECK
─────────────────────────────
Critical gaps remaining: [n — list them]
Contradictions remaining: [n — list them]
Core flow status: [Testable end-to-end / Not yet]
All outputs executable: [Yes / No]
Persona/journey updated: [Yes / No]
README synced: [Yes / No]
Blocked fixes: [n — list them]
Tier 1 met: [Yes / No]
Tier 2 applicable: [Yes / No]
Final decision: [Continue / Stop]
─────────────────────────────
```

---

## Exit Is Not Failure

A system that exits cleanly after 2 iterations with all Critical gaps closed is performing correctly. A system that loops 5 times without reaching exit criteria has a deeper structural problem that should be escalated to the user — not looped again.
