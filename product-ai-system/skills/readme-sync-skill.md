---
name: readme-sync-skill
description: Updates README so system documentation accurately reflects the current product state, workflows, capabilities, and commands. Detects stale content, removes it, and adds missing sections. Output is production-ready markdown.
invoke: /readme-sync-skill [current system state]
---

# Skill — README Sync

## Purpose

Ensure documentation stays aligned with the current system. A README that documents what the system used to do is worse than no README — it creates false confidence.

## Input

- Latest commands
- Latest workflows (file list + purposes)
- Latest skills (file list + purposes)
- Latest product definition (what the system does now)
- New capabilities added since last sync
- Recent changes (from Change Log if available)

## Process

### Step 1 — Detect Changes Since Last Sync
Identify:
- New files added since last README update
- Files renamed or removed
- Commands that changed
- Behaviors that changed
- Capabilities that are documented but no longer exist
- Capabilities that exist but are not documented

Output a change delta:
```
SYNC DELTA
─────────────────────────────
New files: [list]
Removed files: [list]
Changed commands: [list — old → new]
New capabilities: [list]
Stale content: [sections or items in README that are no longer accurate]
Missing content: [things that exist but are not documented]
─────────────────────────────
```

### Step 2 — Update README Sections
For each changed area, rewrite only the affected section:
- System description — reflect current purpose and capabilities
- Commands — match current command names exactly
- Workflows — match current workflow files and purposes
- Skills — match current skill files and purposes
- System structure — reflect current file structure
- Usage examples — test that they are accurate

Do not rewrite sections that are still accurate.

### Step 3 — Check Accuracy
Before finalizing:
- Do all file names referenced in the README match actual files in the system?
- Do all commands match the commands defined in `product-ai-system.md`?
- Are any capabilities claimed that are not actually implemented?
- Are there aspirational claims (things the system "will" do) that should be removed?

Remove stale content rather than leaving drift. A README with an asterisk and "coming soon" is still documentation debt.

## Output

### README Changes
| Section | What Changed | Why |
|---|---|---|

### Sync Verdict
- **In Sync** — README accurately reflects current system state
- **Updated** — [n] sections changed — list them

### Updated README Block
[Full production-ready markdown for the README — complete, not partial]

## Rules

- README must match actual files — no aspirational claims for missing capabilities
- Remove stale content rather than leaving it with a note
- File names, commands, and skill names must be exact — not paraphrased
- The README must be usable by someone who has never seen this system before
- After update, README must be scannable in under 2 minutes
