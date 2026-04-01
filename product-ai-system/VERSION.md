# VERSION.md

## Current Version

**v3.0** — Combined system (latest)
Location: `product-ai-system/`

---

## Version History

### v3.0 — Combined Production System
**Date:** 2026-04-01
**Type:** Major structural change

**What changed:**
- Combined v1 (strong structure, weak execution) and v2 (strong execution, weak structure) into a single production system
- Expanded core loop from 9 phases (v1) and unlabeled steps (v2) to 16 explicit phases
- Replaced all skill stubs (v1) with fully implemented production-level skills (v2 quality)
- Added two new skills not present in either version: `self-study-skill`, `execution-readiness-skill`
- Replaced v1's 10 per-run operating rules with 10 Always-On Rules (standing behaviors)
- Upgraded system-memory with 6th section: User Signals
- Upgraded exit-criteria with "Do Not Stop If" guardrails and explicit Exit Check output format
- Upgraded orchestrator with full Orchestrator Decision output block
- Simplified commands to 4 (run / evolve / learn / feature-update)
- Added versioning model and VERSION.md

**Archive:** `archive/product-ai-system-v1/`, `archive/product-ai-system-v2/`

---

### v2.0 — Production-Level Execution
**Date:** Prior to 2026-04-01
**Type:** Major structural change
**Location:** `archive/product-ai-system-v2/`

**What it was:**
- Production-quality skill implementations (Self Inquiry, Hypothesis, Self Test, Gap Detection, Self Healing, Learning Capture, Persona Refresh, README Sync)
- Strong Always-On Rules as standing behaviors
- Added Product Decisions to system-memory
- Added "Do Not Stop If" guardrails to exit-criteria
- Simpler command set
- Weakness: No problem definition phase, no execution readiness, no Self Study, no 4-perspective test

---

### v1.0 — Structured Product Chain
**Date:** Prior to 2026-04-01
**Type:** Original system
**Location:** `archive/product-ai-system-v1/`

**What it was:**
- 9-skill numbered chain: Define → Diagnose → Goal → Generate → Challenge → Refine → Self Study → Test → Execution Readiness
- Three modes: Product Problem, Self-Evolution, Learning
- System control layer: orchestrator, memory, exit-criteria
- Weakness: Skill files were stubs (some 1–3 lines), full logic only in main skill file

---

## Versioning Rules

1. **The latest system is always named:** `product-ai-system/`
2. **Previous versions are archived in:** `archive/product-ai-system-vN/`
3. **Archived versions are immutable** — do not modify them after archiving
4. **Major structural changes** → archive current version, create new version, update this file
5. **Minor improvements** → update files in `product-ai-system/` only, no new version
6. **When a major change occurs:** update VERSION.md before modifying any system file

---

## What Constitutes a Major Change

Major (requires new version):
- Adding or removing a phase from the core loop
- Adding a new mode (Run / Evolve / Learn / Feature Update)
- Restructuring the folder layout
- Changing the command interface
- Replacing the orchestrator routing model

Minor (update in place):
- Improving skill logic or output format
- Adding a section to system-memory
- Clarifying rules or instructions
- Fixing inconsistencies between files
- Updating README
