---
name: persona-journey-refresh-skill
description: Refreshes persona and user journey whenever scope, features, flows, or assumptions change. Produces updated persona and journey that reflect the latest product reality, with explicit before/after comparison.
invoke: /persona-journey-refresh-skill [current product state]
---

# Skill — Persona & Journey Refresh

## Purpose

Keep persona and user journey aligned with the latest product reality. A persona that was accurate at Phase 1 may be wrong by Phase 10 — this skill corrects the drift.

## Input

- Current product definition (post-healing)
- Latest scope
- Latest user flow
- Feature updates (if any)
- User signals from system memory
- Prior persona (if exists)

## Process

### Step 1 — Re-read User Definition
From the current product state, clarify:
- **Target user** — who specifically is this for? Name demographics, context, role, or behavior pattern — not "users in general"
- **Primary goal** — what does this user want to accomplish?
- **Constraints** — what limits their ability to act (time, access, skill, context)?
- **Behaviors** — what do they actually do vs. what we assume they do?
- **Success condition** — what does "this worked" look like from their perspective?

### Step 2 — Update Persona
Refresh the persona to reflect current product state:

| Attribute | Previous | Updated | Changed? |
|---|---|---|---|
| Name / archetype | | | |
| Role or context | | | |
| Primary need | | | |
| Motivations | | | |
| Blockers | | | |
| Decision triggers | | | |
| Success state | | | |

Flag any attribute that changed and explain why — connect it to a specific product or scope change.

### Step 3 — Update Journey
Map the updated user journey from entry to completion:

| Step # | Step Name | User Action | System Response | Decision Point? | Failure Risk | Updated? |
|---|---|---|---|---|---|---|

For each step that changed from the prior journey: note what changed and why.

### Step 4 — Compare Against Previous Version
If a prior persona exists:
- What assumptions were dropped?
- What user behaviors changed?
- What success conditions shifted?
- Are there steps in the old journey that no longer exist?
- Are there new steps that didn't exist before?

If no prior persona: skip this step.

### Step 5 — Implications for Product Design
State 2–3 specific implications of the updated persona and journey:
- What design decisions should change given the updated persona?
- What flows need to be reconsidered given the updated journey?
- What success metrics need to be updated?

## Output

### Updated Persona
[structured persona block — all fields from Step 2]

### Updated Journey
[step table from Step 3]

### What Changed
| Attribute / Step | Before | After | Why |
|---|---|---|---|

### Implications for Product Design
1. [specific implication]
2. [specific implication]
3. [specific implication — if applicable]

## Rules

- Avoid generic personas — "busy professional" is not a persona
- Every changed attribute must connect to a specific product or scope change
- Journey must reflect actual latest flow — not the aspirational flow
- If the persona cannot be defined with current information, state what information is missing
- Refresh whenever core flow or scope changes — not only at the end of a cycle
