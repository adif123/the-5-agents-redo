# Project Documentation Scan

## Overview
Full map of every Markdown file in the `the-5-agents-redo` project. Covers root config, all Superpowers skills, Obsidian skills, and their supporting reference files. Each entry describes what the file does, who owns it, and what it relates to. The project is a multi-agent content-creation system with a CEO orchestrator agent and specialized sub-agents.

## Open Questions
- Which sub-agents will be defined in `.claude/agents/`?
- Will `.claude/commands/` get custom slash commands?
- Should the vault itself be tracked in git or kept local?
- Should Obsidian vault root be set to project root (to see `.claude/skills/`) or stay at `vault/`?

## Session Log

### 2026-05-18 — Initial full MD file scan [shipped]
- **What was done:** Scanned all 40 MD files in the project, categorized them by type and owner, created the full vault folder structure, and wrote this documentation map.
- **Decisions:** Used `vault/Meeting Notes/` as the home for this session log. Vault folders created: Meeting Notes, Content Briefs, Brand Guidelines, Publishing Log — all with `_index.md`.
- **Notes / Caveats:** Skills came from two sources — Superpowers (obra/superpowers, installed manually) and Obsidian plugin. Supporting `.md` files inside skill folders are sub-prompts or references, not standalone skills.
- **Related:** [[project-setup]]

### 2026-05-18 — Gap fix: missing skill + vault root question [shipped]
- **What was done:** Found that `using-git-worktrees/SKILL.md` was missing from `md-file-map.md`. Added it. Also identified that the user cannot see skill files in Obsidian because the vault root is `vault/` while skills live in `.claude/skills/`.
- **Decisions:** Added `using-git-worktrees` entry to `md-file-map.md`. Added open question about vault root location.
- **Notes / Caveats:** At session start, `.claude/` should always be inspected — not just the vault. Relying on the compacted summary alone caused the gap.
- **Related:** [[project-setup]]

