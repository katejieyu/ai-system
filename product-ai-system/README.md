# Product AI System

**Version:** 3.0
**Type:** Self-evolving AI-native product development system

Takes a product problem — vague idea, named feature, or existing draft — and moves it through a 16-phase cycle to execution-ready output. Does not agree with your framing. Challenges assumptions, generates competing hypotheses, stress-tests solutions, detects gaps, heals itself, learns from user input, and repeats until all critical gaps are resolved.

---

## Commands

| Command | Use |
|---|---|
| `/product-ai-system run [problem]` | Full 16-phase cycle from idea to execution plan |
| `/product-ai-system evolve` | Self-evolution loop — challenge, test, detect, fix |
| `/product-ai-system learn [feedback]` | Learning loop — convert user input into system improvements |
| `/product-ai-system feature-update [feature]` | Re-align system after a feature changes scope or flow |

---

## Core System Loop

```
Phase 1  — Define Issue
Phase 2  — Diagnose Problem
Phase 3  — Define Goal
Phase 4  — Self Inquiry
Phase 5  — Self Hypothesis
Phase 6  — Generate Solution
Phase 7  — Challenge Solution
Phase 8  — Self Test Loop
Phase 9  — Gap Detection
Phase 10 — Self Healing Execution
Phase 11 — Self Study
Phase 12 — Test (4 perspectives: User, PM, Designer, Engineer)
Phase 13 — Execution Readiness
Phase 14 — Persona & Journey Refresh
Phase 15 — README Sync
Phase 16 — Exit Criteria Check
```

If Critical gaps remain after Phase 16: routes to Self-Evolution Loop.
After any cycle: routes to Learning Loop if unresolved gaps remain.

---

## Workflows

| File | Purpose |
|---|---|
| `workflows/product-full-cycle-workflow.md` | Full 16-phase execution from idea to output |
| `workflows/product-self-evolution-workflow.md` | Iterative loop: inquire → hypothesize → test → detect → fix → re-test |
| `workflows/feature-change-loop-workflow.md` | Interpret → impact-assess → update → re-evolve → refresh persona → sync README |
| `workflows/learning-loop-workflow.md` | Detect gaps → ask user → capture input → generate improvements → apply → re-run |

---

## Skills

All skills are production-level. Each has: Purpose, Input, Process (step-by-step), Output (structured), Rules.

| Skill File | What It Does |
|---|---|
| `skills/self-inquiry-skill.md` | Challenges assumptions and framing risks before any solution is generated |
| `skills/self-hypothesis-skill.md` | Generates 3 competing hypotheses, compares them, selects working direction + fallback |
| `skills/self-test-loop-skill.md` | Simulates main flow, 5+ edge cases, failure paths, 3-perspective reviewer simulation |
| `skills/gap-detection-skill.md` | Identifies logic, flow, UX, scope, and ownership gaps; produces prioritized gap register |
| `skills/self-healing-execution-skill.md` | Applies fixes to Critical and Moderate gaps; produces updated product state and flow |
| `skills/self-study-skill.md` | Reviews all prior phases as one artifact; finds drift, recurring weaknesses, and blind spots |
| `skills/execution-readiness-skill.md` | Breaks into epics, tasks, acceptance criteria, dependencies, readiness score 0–100 |
| `skills/learning-capture-skill.md` | Classifies user input, extracts signal, produces exact file changes with before/after |
| `skills/persona-journey-refresh-skill.md` | Refreshes persona and user journey to reflect latest product state with before/after comparison |
| `skills/readme-sync-skill.md` | Detects stale content, updates all changed sections, produces production-ready README |

---

## System Control

### system-orchestrator.md
Routes commands to workflows. Enforces follow-on rules. Controls loop depth (max 3 iterations without progress). Reads system-memory before every run.

Routing:
| After | Always runs next |
|---|---|
| `run` | Learning Loop (if gaps remain) |
| `evolve` | Learning Loop |
| `feature-update` | Evolve → Learning Loop |
| Learning Loop (gaps remain) | Learning Loop again |
| Learning Loop (exit criteria met) | Stop |

### system-memory.md
Stores what the system has learned. Read before every run. Write after every learning cycle.

Six sections:
- **Stored Patterns** — recurring structures across problem types
- **Known Fixes** — confirmed solutions, applied immediately on re-encounter
- **Recurring Issues** — gaps not yet permanently resolved
- **Known Edge Cases** — inputs that caused wrong output and correct behavior
- **Product Decisions** — decisions made during cycles, stored to prevent re-debate
- **User Signals** — explicit preferences, recurring requests, persistent constraints

Promotion Rule: A Known Fix applied 3+ times → promote to main system as standing rule.

### exit-criteria.md
Two-tier stop condition:
- **Tier 1 (Hard Stop)** — no Critical gaps, no contradictions, all outputs executable, no blocked fixes, persona updated, README synced
- **Tier 2 (Soft Stop)** — marginal improvement: only Minor gaps remain, progress stalled, 3+ iterations with no new closures

---

## Self-Learning Capability

After a full cycle, if unresolved gaps remain, the system prompts:
> "Run learning mode to convert unresolved gaps into system improvements? (yes / skip)"

The learning loop runs 8 steps:
1. **Gap Detection** — reads cycle output, identifies what was vague, missing, or low-confidence
2. **Question Generation** — produces 3–5 targeted questions (not generic feedback requests)
3. **User Input Capture** — waits for answers; classifies each by type and quality
4. **System Reflection** — determines which gaps are Closed, Partial, or Open
5. **Improvement Generation** — converts gaps into logic fixes, format fixes, scope updates, new skills, or new workflows
6. **Apply Changes** — writes changes to affected files with before/after log
7. **Re-run Local Evolution** — confirms changes closed the gaps and introduced no new ones
8. **Cycle Log** — records the session in system-memory

User input is not stored as notes. It is processed through `learning-capture-skill`, which extracts specific actionable signals and produces exact file changes. Every improvement is a concrete edit to a specific file and section.

---

## Versioning Model

- **Latest version:** always in `product-ai-system/`
- **Prior versions:** immutable, stored in `archive/product-ai-system-vN/`
- **Major changes** → archive current version, create new, update `VERSION.md`
- **Minor improvements** → update files in place, no new version
- Full version history in `VERSION.md`

---

## Install

```bash
cp product-ai-system/product-ai-system.md ~/.claude/commands/product-ai-system.md
```

Then invoke with:
```
/product-ai-system run [your problem or idea]
```

---

## End Deliverable

From a full cycle run:
- Cycle Summary: final problem definition, goal, V1 solution, top risks
- Epics, tasks, and acceptance criteria
- Readiness score 0–100 with reason
- Pre-build checklist with owners
- Every output ends with: Confidence level + Unresolved Gaps + Next Step

---

## File Structure

```
product-ai-system/
├── product-ai-system.md          # Main system file — install this
├── system-orchestrator.md        # Routing rules, execution sequences, loop behavior
├── system-memory.md              # Persistent learning — patterns, fixes, decisions, signals
├── exit-criteria.md              # Stop conditions — Tier 1 and Tier 2
├── VERSION.md                    # Version history and versioning rules
├── README.md                     # This file
├── workflows/
│   ├── product-full-cycle-workflow.md
│   ├── product-self-evolution-workflow.md
│   ├── feature-change-loop-workflow.md
│   └── learning-loop-workflow.md
└── skills/
    ├── self-inquiry-skill.md
    ├── self-hypothesis-skill.md
    ├── self-test-loop-skill.md
    ├── gap-detection-skill.md
    ├── self-healing-execution-skill.md
    ├── self-study-skill.md
    ├── execution-readiness-skill.md
    ├── learning-capture-skill.md
    ├── persona-journey-refresh-skill.md
    └── readme-sync-skill.md

archive/
├── product-ai-system-v1/         # Original structured system
└── product-ai-system-v2/         # Production-level execution system
```
