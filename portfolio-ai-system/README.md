# Portfolio AI System

A portfolio strategy, audit, and rewrite system for job applications at Staff / Principal level.

Evaluates portfolios as products competing for hiring decisions. Runs a 7-step workflow: intent definition, issue diagnosis, goal alignment, hiring simulation, UX/QA check, rewrite, and execution plan.

---

## Files

| File | Description |
|---|---|
| `portfolio-ai-system.md` | Main skill file -- install this |
| `portfolio-audit-workflow.md` | Full 7-step audit workflow (standalone) |
| `workflows/portfolio-site-scan-workflow.md` | Full-site scan across all pages — cross-page consistency, system-level issues, top 10 fixes |
| `skills/hiring-simulation-skill.md` | 4-perspective hiring simulation with interview verdicts |
| `skills/homepage-rewrite-skill.md` | Headline, subtext, CTA, and section label rewrites |
| `skills/mobile-qa-skill.md` | 375px mobile responsiveness and overflow QA checklist |
| `skills/portfolio-consistency-skill.md` | Extracts positioning, tone, and structure patterns for cross-page consistency |
| `skills/portfolio-content-strategy-skill.md` | Defines content strategy — what to say, what to remove, signal hierarchy, tone, CTA, and section priorities |
| `skills/portfolio-execution-skill.md` | Executes audit findings and rewrites directly to portfolio files — produces a change log |
| `skills/site-execution-skill.md` | Turns scan-site findings into page-by-page implementation-ready changes — canonical decisions first, then exact fixes per page |

---

## Install

```bash
# Install all skills at once
cp portfolio-ai-system.md ~/.claude/commands/portfolio-ai-system.md && \
cp portfolio-audit-workflow.md ~/.claude/commands/portfolio-audit-workflow.md && \
cp skills/*.md ~/.claude/commands/ && \
cp workflows/*.md ~/.claude/commands/
```

Or install individually:

```bash
cp skills/hiring-simulation-skill.md ~/.claude/commands/hiring-simulation-skill.md
cp skills/homepage-rewrite-skill.md ~/.claude/commands/homepage-rewrite-skill.md
cp skills/mobile-qa-skill.md ~/.claude/commands/mobile-qa-skill.md
cp skills/portfolio-consistency-skill.md ~/.claude/commands/portfolio-consistency-skill.md
cp skills/portfolio-content-strategy-skill.md ~/.claude/commands/portfolio-content-strategy-skill.md
cp skills/portfolio-execution-skill.md ~/.claude/commands/portfolio-execution-skill.md
cp skills/site-execution-skill.md ~/.claude/commands/site-execution-skill.md
cp workflows/portfolio-site-scan-workflow.md ~/.claude/commands/portfolio-site-scan-workflow.md
```

---

## Usage

```
/portfolio-ai-system audit [portfolio URL or folder]
```

| Command | Use |
|---|---|
| `/portfolio-ai-system audit [portfolio]` | Full 7-step audit |
| `/portfolio-ai-system rewrite [section]` | Rewrite a specific section |
| `/portfolio-ai-system qa [site/folder]` | Links, logic, structure check |
| `/portfolio-ai-system mobile [page]` | Responsive and overflow check |
| `/portfolio-ai-system hiring [portfolio]` | Hiring simulation only |
| `/portfolio-ai-system learn-site [existing pages]` | Extract consistency guide from current site |
| `/portfolio-ai-system consistency-check [new page]` | Check a new page against the site's established patterns |
| `/portfolio-ai-system strategy-check [site/folder]` | Validate site against its content strategy — alignment score, drift, gaps, top fixes |
| `/portfolio-execution-skill [audit output or page]` | Execute all fixes directly to files — produces change log |
| `/portfolio-ai-system scan-site [site]` | Full-site audit across all pages — cross-page consistency, system-level issues, top 10 fixes |
| `/portfolio-ai-system scan-site + execution [site]` | Full-site audit + page-by-page fix generation |
| `/site-execution-skill [scan-site report]` | Apply scan-site findings as page-by-page exact changes — produces change log |
| `/portfolio-ai-system content-strategy [portfolio]` | Define content strategy — pillars, signal hierarchy, tone, what to remove |

Individual skills:

| Command | Use |
|---|---|
| `/hiring-simulation-skill [portfolio]` | 4-perspective hiring simulation |
| `/homepage-rewrite-skill [page]` | Homepage copy rewrite |
| `/mobile-qa-skill [page]` | Mobile QA checklist |
| `/portfolio-consistency-skill [portfolio]` | Extract consistency guide for new pages |
| `/portfolio-content-strategy-skill [portfolio]` | Define content strategy — pillars, signal hierarchy, tone, what to remove |
| `/portfolio-execution-skill [audit output or page]` | Execute fixes directly to portfolio files |
| `/site-execution-skill [scan-site report or site]` | Apply scan-site findings page-by-page — canonical decisions, exact replacements, change log |

---

## The 7-Step Workflow

| # | Step | What It Does |
|---|---|---|
| 1 | Define Intent | Establish what the portfolio is trying to communicate |
| 2 | Diagnose Issues | Evaluate positioning, content, structure, and storytelling |
| 3 | Goal Alignment | Define what must be communicated in 10 seconds |
| 4 | Hiring Simulation | Simulate review from Recruiter, Manager, Design Leader, AI Leader |
| 5 | UX / QA / Mobile Check | Scanning, navigation, links, mobile responsiveness |
| 6 | Rewrite & Improvement | Exact before/after rewrites for homepage, CTAs, copy |
| 7 | Execution Plan | Immediate fixes, short-term improvements, structural changes |

**Extended commands (run after the 7-step audit):**
- `content-strategy` — define what to say, what to remove, signal hierarchy
- `strategy-check` — validate site execution against the defined strategy
- `scan-site` — full cross-page audit with consistency detection

---

## Portfolio Drift Protocol

The system's internal logic doesn't drift — what drifts is its knowledge of the portfolio it's evaluating. When the portfolio changes significantly (new case studies, role change, major redesign), run this sequence:

```
Step 0 — Pre-check: identify what changed, flag stale outputs, re-run only what's affected
Step 1 — /portfolio-ai-system learn-site [updated pages]
Step 2 — /portfolio-ai-system content-strategy [portfolio]   (skip if positioning unchanged)
Step 3 — /portfolio-ai-system consistency-check [changed pages]
Step 4 — /portfolio-ai-system audit [portfolio]
```

---

## End Deliverable

Full audit report including:

- Hiring verdict per role (Yes / No / Conditional)
- Exact before/after copy rewrites
- Mobile issue list with fixes
- Prioritized execution plan (immediate / short-term / structural)
- Overall score: how competitive at Staff/Principal level
