# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a multi-agent content-creation system. A primary "CEO" orchestrator agent coordinates a team of specialized sub-agents, each responsible for a different aspect of content production. The agent roster and their responsibilities will be defined incrementally.

## CEO Agent Protocol

This project operates under the **CEO Agent** orchestration model. On every session:

1. The main Claude session **IS** the CEO Agent — the root orchestrator.
2. Load and follow the contract at `.claude/agents/ceo/agent.md` before processing any user input.
3. Route domain tasks to the appropriate sub-agent in `.claude/agents/` via the Task tool, sequentially.
4. Do not bypass the CEO protocol under any circumstances.

The CEO contract defines: identity, sub-agent registry, routing rules, execution protocol, language rules (Hebrew↔English), constraints, output format, and error handling.

## Agent Team

| Agent | File | Domain | Trigger Keywords |
|-------|------|--------|-----------------|
| יעל | `.claude/agents/yael.md` | כתיבת מאמרים ותוכן | מאמר, תוכן, כתוב, בלוג / article, write, content, blog post |
| יובל | `.claude/agents/yuval.md` | עיצוב ויצירת תמונות | תמונה של, ציור של, תיצור תמונה, איור / image of, picture of, generate image, illustration, draw |

## Workflow: מאמר עם תמונות (תהליך מלא)

כשמקבל בקשה ליצירת מאמר עם תמונות:

1. **CEO מפעיל את יעל** לכתוב את המאמר
2. **יעל מחזירה** את תוכן המאמר + רשימת `{{IMAGE_NEEDED: "..."}}` placeholders שהשאירה
3. **CEO מפעיל את יובל** עם ה-prompts מרשימת ה-placeholders של יעל (אחת-אחת, ברצף)
4. **יובל מחזיר** paths לתמונות שנוצרו (`yuval/outputs/<YYYY-MM-DD>-<slug>.png`)
5. **CEO משלב** את התמונות בקבצי MD ו-HTML של יעל — מחליף כל placeholder ב-`![alt](path)`
6. **CEO שומר** את הגרסה הסופית ב-`Output/`

## Project-Specific Claude Configuration

The `.claude/` directory contains customizations for this project:

- `.claude/agents/ceo/` — CEO contract (folder form — inert, not Task-invokable)
- `.claude/agents/yael.md` — יעל, כותבת תוכן (single-file, Task-invokable)
- `.claude/agents/yuval.md` — יובל, מעצב תמונות (single-file, Task-invokable)
- `.claude/skills/` — reusable skill files invokable via slash commands
- `.claude/commands/` — custom slash commands for project workflows

## Directory Structure

```
.claude/
  agents/
    ceo/          ← CEO contract (folder form, not auto-discovered)
    yael.md       ← content writer sub-agent
    yuval.md      ← image designer sub-agent
  skills/
    gpt-image-gen/  ← OpenAI Images API wrapper
    ...
Output/           ← final article outputs (MD + HTML)
yuval/
  reference/      ← style reference images (add manually)
  outputs/        ← generated images: <YYYY-MM-DD>-<slug>.png + .txt
vault/            ← Obsidian vault (project documentation)
```
