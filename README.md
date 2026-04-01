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
    skills/
      self-inquiry-skill.md
      self-hypothesis-skill.md
      self-test-loop-skill.md
      gap-detection-skill.md
      self-healing-execution-skill.md
      persona-journey-refresh-skill.md
      readme-sync-skill.md
    workflows/
      product-full-cycle-workflow.md
      product-self-evolution-workflow.md
      feature-change-loop-workflow.md
```

---

## Systems

### 1. Product AI System (`/product-ai-system`)

A self-evolving product reasoning engine for designers, PMs, and engineers.

Moves product work from raw problem to execution-ready output through a 9-skill chain. Does not agree with your framing. Surfaces contradictions, flags assumptions, and forces decisions before they become blockers in engineering.

Also includes a **self-evolution mode** — the system can turn inward, detect its own drift, regenerate assumptions, and heal gaps without a full audit cycle.

**Skill file:** `product-ai-system/product-ai-system.md`
**Install:** `cp product-ai-system/product-ai-system.md ~/.claude/commands/product-ai-system.md`
**Invoke:** `/product-ai-system [problem or idea]`

**The 9-Skill Chain (Product Problem Mode):**

| # | Skill | What It Does |
|---|---|---|
| 1 | Define Issue | Finds the real problem behind the request |
| 2 | Diagnose | Identifies root causes at a system level |
| 3 | Define Goal | Turns the problem into measurable outcomes |
| 4 | Generate Solution | Creates a grounded V1 solution |
| 5 | Challenge Solution | Critiques the solution before moving forward |
| 6 | Refine Solution | Improves it using challenge findings |
| 7 | Self Study | Reviews the full body of work for patterns |
| 8 | Self Test | Simulates review from User, PM, Designer, Engineer perspectives |
| 9 | Execution Readiness | Breaks into epics, tasks, acceptance criteria, and a readiness score |

**Product Problem Mode:**

| Command | Use |
|---|---|
| `/product-ai-system [problem]` | Full 9-skill cycle |
| `/product-ai-system fast [problem]` | Compressed 5-skill cycle |
| `/product-ai-system skill [1-9] [input]` | Single skill in isolation |
| `/product-ai-system brief [problem]` | Problem brief only (Skills 1–2) |
| `/product-ai-system prd [problem]` | Full PRD (Skills 1–6) |

**Self-Evolution Mode:**

| Command | Use |
|---|---|
| `/product-ai-system evolve` | Run self-evolution loop on the system itself |
| `/product-ai-system feature-update [feature]` | Re-align system after a feature changes |
| `/product-ai-system refresh-persona` | Update persona and journey definitions |
| `/product-ai-system sync-readme` | Sync documentation to current system state |

**Self-Evolution Sub-Skills** (`/skills`):

| File | What It Does |
|---|---|
| `self-inquiry-skill.md` | Challenge current assumptions before generating anything |
| `self-hypothesis-skill.md` | Generate testable hypotheses from gaps |
| `self-test-loop-skill.md` | Simulate usage to find real failure points |
| `gap-detection-skill.md` | Find missing logic and undefined states |
| `self-healing-execution-skill.md` | Fix gaps directly — no analysis, only action |
| `persona-journey-refresh-skill.md` | Update persona and journey after context changes |
| `readme-sync-skill.md` | Align documentation with current system state |

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
/product-ai-system [your problem]
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
