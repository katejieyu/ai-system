# Workflow — Feature Change Loop

## Purpose

Handle new feature requests without breaking the existing product definition. Every new feature must be interpreted, impact-assessed, integrated, re-tested, and documented before it is considered complete.

## When to Use

Invoked by: `/product-ai-system feature-update [feature description]`

## Rule

Every new feature must trigger re-testing and re-evaluation. No feature is considered integrated until updated flows, gaps, persona, and docs are refreshed.

## Steps

### Step 1 — Interpret the Feature Request
Define:
- What the feature does
- Who it affects (users, flows, logic)
- What changes from the current state
- What is ambiguous and needs clarification before proceeding

If ambiguous: stop and ask one clarifying question before Step 2.

### Step 2 — Identify Impact
Assess effect on:
- **Scope** — what is added, removed, or changed in V1 scope
- **Logic** — which rules, decisions, or constraints are now wrong
- **User Flows** — which steps change, break, or branch
- **Acceptance Criteria** — which criteria are invalidated by this change
- **Persona and Journey** — which user behaviors or goals shift
- **System Memory** — which prior decisions are now stale

Output:
- **Impact Register** — table: area + change type + severity (Critical / Moderate / Minor)

### Step 3 — Update Product Definition
Rewrite only the areas identified in the Impact Register.
- Update scope
- Update logic and decision rules
- Update user flows
- Update acceptance criteria
- Log every change in a Change Log

Do not change areas outside the impact register.

### Step 4 — Run Product Self Evolution
Execute `workflows/product-self-evolution-workflow.md` on the updated areas only.
Do not re-run phases that were not affected by the feature change.

### Step 5 — Refresh Persona & Journey
Run `skills/persona-journey-refresh-skill.md`.
Update persona and journey to reflect the new feature reality.

### Step 6 — Sync README
Run `skills/readme-sync-skill.md`.
Update documentation: new feature, changed commands, updated capabilities.

### Step 7 — Exit Criteria Check
Check `exit-criteria.md`.
- If met: stop.
- If not met: loop back to Step 4 with remaining gaps.

## Output

```
FEATURE UPDATE SUMMARY
─────────────────────────────
Feature: [name and description]
Impact areas: [list from Step 2]
Changes applied: [Change Log summary]
Persona updated: [Yes / No]
README synced: [Yes / No]
Gaps remaining: [list with owners]
Exit check: [Continue / Stop — reason]
─────────────────────────────
```
