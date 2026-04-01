# AI Systems

A collection of structured, skill-based reasoning systems built for Claude Code. Each system runs your input through a defined chain of skills and produces specific, decision-quality outputs.

Built by Kate Jie Yu.

---

## Structure

```
ai-systems/
  README.md

  portfolio-ai-system/
    README.md
    portfolio-ai-system.md
    portfolio-audit-workflow.md
    workflows/
      portfolio-site-scan-workflow.md
    skills/
      hiring-simulation-skill.md
      homepage-rewrite-skill.md
      mobile-qa-skill.md
      portfolio-consistency-skill.md
      portfolio-content-strategy-skill.md
      portfolio-execution-skill.md
      site-execution-skill.md

  product-ai-system/
    README.md
    product-ai-system.md
    VERSION.md
    system-orchestrator.md
    system-memory.md
    exit-criteria.md
    skills/
      self-inquiry-skill.md
      self-hypothesis-skill.md
      self-test-loop-skill.md
      gap-detection-skill.md
      self-healing-execution-skill.md
      self-study-skill.md
      execution-readiness-skill.md
      learning-capture-skill.md
      persona-journey-refresh-skill.md
      readme-sync-skill.md
    workflows/
      product-full-cycle-workflow.md
      product-self-evolution-workflow.md
      feature-change-loop-workflow.md
      learning-loop-workflow.md

  archive/
    product-ai-system-v1/
    product-ai-system-v2/
```

---

## Systems

### 1. Product AI System (`/product-ai-system`)

A self-evolving product development system for designers, PMs, and engineers.

Moves product work from raw problem to execution-ready output through a 16-phase cycle. Does not agree with your framing. Challenges assumptions, generates competing hypotheses, stress-tests solutions, detects gaps, heals itself, learns from user input, and repeats until all critical gaps are resolved.

Also includes a **self-evolution mode** — the system can turn inward, detect its own drift, and fix gaps without a full rebuild.

Also includes a **self-learning mode** — after every run, the system detects what it got wrong, asks the user targeted questions, and converts answers into permanent improvements.

**Current version:** v3.0
**Skill file:** `product-ai-system/product-ai-system.md`
**Install:** `cp product-ai-system/product-ai-system.md ~/.claude/commands/product-ai-system.md`
**Invoke:** `/product-ai-system run [problem or idea]`

**Commands:**

| Command | Use |
|---|---|
| `/product-ai-system run [problem]` | Full 16-phase cycle — problem to execution plan |
| `/product-ai-system evolve` | Self-evolution loop — challenge, test, detect, fix |
| `/product-ai-system learn [feedback]` | Learning loop — convert user input into system improvements |
| `/product-ai-system feature-update [feature]` | Re-align system after a feature changes |

**The 16-Phase Core Loop:**

| # | Phase | What It Does |
|---|---|---|
| 1 | Define Issue | Finds the real problem — separates symptoms from root causes |
| 2 | Diagnose Problem | Identifies structural causes, workflow gaps, dependencies |
| 3 | Define Goal | Turns the problem into measurable outcomes with metrics |
| 4 | Self Inquiry | Challenges framing and assumptions before solution generation |
| 5 | Self Hypothesis | Generates 3 competing directions, selects primary + fallback |
| 6 | Generate Solution | Builds a grounded V1 solution from the selected hypothesis |
| 7 | Challenge Solution | Critiques the solution — weak points, hidden risks, edge cases |
| 8 | Self Test Loop | Simulates main flow, 5+ edge cases, failure paths |
| 9 | Gap Detection | Identifies all logic, flow, UX, scope, and ownership gaps |
| 10 | Self Healing Execution | Fixes all Critical and Moderate gaps directly |
| 11 | Self Study | Reviews all prior phases as one artifact — detects drift and recurring weaknesses |
| 12 | Test (4 perspectives) | Simulates review from User, PM, Designer, Engineer — verdict per perspective |
| 13 | Execution Readiness | Epics, tasks, acceptance criteria, readiness score 0–100 |
| 14 | Persona & Journey Refresh | Updates persona and journey to reflect latest product state |
| 15 | README Sync | Updates documentation to reflect current state |
| 16 | Exit Criteria Check | Determines if cycle is complete or must continue |

**Skills** (`/skills`):

| File | What It Does |
|---|---|
| `self-inquiry-skill.md` | Challenges assumptions and framing risks before solution generation |
| `self-hypothesis-skill.md` | Generates 3 competing hypotheses, compares, selects direction + fallback |
| `self-test-loop-skill.md` | Simulates main flow, edge cases, failure paths, 3-perspective review |
| `gap-detection-skill.md` | Identifies logic, flow, UX, scope, and ownership gaps with prioritized register |
| `self-healing-execution-skill.md` | Applies fixes to Critical/Moderate gaps, produces updated product state |
| `self-study-skill.md` | Reviews all prior phases as one artifact, finds drift and recurring weaknesses |
| `execution-readiness-skill.md` | Epics, tasks, acceptance criteria, dependencies, readiness score 0–100 |
| `learning-capture-skill.md` | Classifies user input, extracts signal, produces exact file changes |
| `persona-journey-refresh-skill.md` | Refreshes persona and journey with before/after comparison |
| `readme-sync-skill.md` | Detects stale content, updates changed sections, produces accurate README |

---

### 2. Portfolio AI System (`/portfolio-ai-system`)

A portfolio strategy, audit, and rewrite system for job applications at Staff / Principal level.

Evaluates portfolios as products competing for hiring decisions. Runs a 7-step workflow: intent definition, issue diagnosis, goal alignment, hiring simulation, UX/QA check, rewrite, and execution plan. Includes consistency tools for keeping new pages aligned with the existing site, and an execution skill that applies all fixes directly to files.

**Skill file:** `portfolio-ai-system/portfolio-ai-system.md`
**Install:** `cp portfolio-ai-system/portfolio-ai-system.md ~/.claude/commands/portfolio-ai-system.md`
**Invoke:** `/portfolio-ai-system audit [portfolio]`

**Modes:**

| Command | Use |
|---|---|
| `/portfolio-ai-system audit [portfolio]` | Full 7-step audit |
| `/portfolio-ai-system rewrite [section]` | Rewrite a specific section |
| `/portfolio-ai-system qa [site/folder]` | Links, logic, structure check |
| `/portfolio-ai-system mobile [page]` | Responsive and overflow check |
| `/portfolio-ai-system hiring [portfolio]` | Hiring simulation only |
| `/portfolio-ai-system learn-site [existing pages]` | Extract consistency guide from current site |
| `/portfolio-ai-system consistency-check [new page]` | Check a new page against the site's established patterns |
| `/portfolio-ai-system content-strategy [portfolio]` | Define content strategy — pillars, signal hierarchy, tone, what to remove |
| `/portfolio-ai-system strategy-check [site/folder]` | Validate site against its content strategy — alignment score, drift, gaps, top fixes |
| `/portfolio-ai-system scan-site [site]` | Full-site audit across all pages — cross-page consistency, system-level issues, top 10 fixes |
| `/portfolio-ai-system scan-site + execution [site]` | Full-site audit + page-by-page fix generation |
| `/portfolio-execution-skill [audit output or page]` | Execute all fixes directly to files — produces change log |
| `/site-execution-skill [scan-site report]` | Apply scan-site findings as page-by-page exact changes — produces change log |

**Modular Skills** (install and invoke independently):

| File | Command | What It Does |
|---|---|---|
| `portfolio-audit-workflow.md` | `/portfolio-audit-workflow` | Full 7-step structured audit (standalone workflow) |
| `skills/hiring-simulation-skill.md` | `/hiring-simulation-skill` | 4-perspective hiring simulation with interview verdicts |
| `skills/homepage-rewrite-skill.md` | `/homepage-rewrite-skill` | Headline, subtext, CTA, and section label rewrites |
| `skills/mobile-qa-skill.md` | `/mobile-qa-skill` | 375px mobile QA checklist |
| `skills/portfolio-consistency-skill.md` | `/portfolio-consistency-skill` | Extract positioning, tone, and structure patterns for cross-page consistency |
| `skills/portfolio-content-strategy-skill.md` | `/portfolio-content-strategy-skill` | Define content strategy — what to say, signal hierarchy, tone, and what to remove |
| `skills/portfolio-execution-skill.md` | `/portfolio-execution-skill` | Execute audit findings and rewrites directly to portfolio files |
| `skills/site-execution-skill.md` | `/site-execution-skill` | Apply scan-site findings page-by-page — canonical decisions, exact replacements, change log |
| `workflows/portfolio-site-scan-workflow.md` | `/portfolio-site-scan-workflow` | Full-site audit — scans all pages, cross-page consistency, top 10 fixes |

---

## Installation

```bash
# Product AI System
cp product-ai-system/product-ai-system.md ~/.claude/commands/product-ai-system.md

# Portfolio AI System — all at once
cp portfolio-ai-system/portfolio-ai-system.md ~/.claude/commands/portfolio-ai-system.md && \
cp portfolio-ai-system/portfolio-audit-workflow.md ~/.claude/commands/portfolio-audit-workflow.md && \
cp portfolio-ai-system/skills/*.md ~/.claude/commands/ && \
cp portfolio-ai-system/workflows/*.md ~/.claude/commands/
```

Or install individual portfolio skills:

```bash
cp portfolio-ai-system/skills/hiring-simulation-skill.md ~/.claude/commands/hiring-simulation-skill.md
cp portfolio-ai-system/skills/homepage-rewrite-skill.md ~/.claude/commands/homepage-rewrite-skill.md
cp portfolio-ai-system/skills/mobile-qa-skill.md ~/.claude/commands/mobile-qa-skill.md
cp portfolio-ai-system/skills/portfolio-consistency-skill.md ~/.claude/commands/portfolio-consistency-skill.md
cp portfolio-ai-system/skills/portfolio-content-strategy-skill.md ~/.claude/commands/portfolio-content-strategy-skill.md
cp portfolio-ai-system/skills/portfolio-execution-skill.md ~/.claude/commands/portfolio-execution-skill.md
cp portfolio-ai-system/skills/site-execution-skill.md ~/.claude/commands/site-execution-skill.md
cp portfolio-ai-system/workflows/portfolio-site-scan-workflow.md ~/.claude/commands/portfolio-site-scan-workflow.md
```

Then invoke in any Claude Code session:

```
/product-ai-system run [your problem]
/product-ai-system evolve
/portfolio-ai-system audit [your portfolio]
/portfolio-ai-system scan-site [your site]
```

---

## Output Quality Rules (Both Systems)

- No generic language — no "seamless," "intuitive," "holistic," "best-in-class"
- Every metric has a number and a measurement method
- Every task and open decision has exactly one named owner
- Assumptions are labeled as assumptions, never stated as facts
- Every output ends with: Confidence level + Unresolved Gaps + Next Recommendation
