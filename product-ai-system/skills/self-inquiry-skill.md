---
name: self-inquiry-skill
description: Challenges assumptions, identifies framing risks, and surfaces hidden contradictions before any solution is generated. Forces the system to question its own framing before trusting it.
invoke: /self-inquiry-skill [idea, current state, or draft]
---

# Skill — Self Inquiry

## Purpose

Challenge the current framing before the system trusts it. Prevent the system from generating solutions to the wrong problem.

## Input

- Raw problem statement
- Product idea
- Existing draft or prior cycle summary
- Current assumptions

## Process

### Step 1 — Restate the Problem
Rewrite the input into one precise sentence that names:
- the user
- the struggle
- the likely cause
- the consequence

If the input cannot be rewritten into this form, the problem is not yet defined — stop and request clarification.

### Step 2 — Challenge Assumptions
List all active assumptions by category:

| Category | Assumption | Source | Still valid? | What would prove it false? |
|---|---|---|---|---|
| User | | | | |
| Business | | | | |
| Product | | | | |
| Technical | | | | |

For each: ask "Is this still true? What would prove it false?"

### Step 3 — Generate Critical Questions
Generate 5–8 high-value questions that expose:
- what is unclear
- what is assumed but unvalidated
- what is being optimized too early
- what might be the wrong scope
- what could be a symptom being mistaken for a root problem

Rules:
- questions must be hard
- do not ask questions you already know the answer to
- each question must point to something that would change the solution if answered differently

### Step 4 — Identify Framing Risks
Find:
- symptoms being treated as root problems
- missing constraints not yet named
- contradictions between stated goals and stated constraints
- success definitions that are too shallow to be meaningful
- scope that is defined too narrowly or too broadly

## Output

### Restated Problem
[one sentence]

### Assumptions Table
[from Step 2]

### Critical Questions
[5–8 questions, numbered]

### Framing Risks
[list — each with: risk + why it matters + what to do about it]

### Recommendation
- **Proceed** — framing is sound, continue to hypothesis
- **Revise Framing** — restate the problem before generating solutions
- **Request More Input** — missing information that cannot be assumed

## Rules

- Do not generate solutions here
- Do not soften weak framing — name it directly
- Assumptions must be explicit and labeled as assumptions
- If framing is wrong, say so and stop — do not proceed to hypothesis on a wrong problem
