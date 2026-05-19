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
| חן | `.claude/agents/chen.md` | מחקר רשת ומציאת מקורות איכותיים | חפש, מצא, מחקר, מאמר על, חדש על, מקור על / search, find, research, article about, latest on, news on |
| יעל | `.claude/agents/yael.md` | שכתוב ועריכת מאמרים בסגנון בית | שכתב, ערוך, נסח מחדש, תרגם, סכם, מאמר, תוכן, פוסט / rewrite, edit, rephrase, translate, summarize, article, content, post |
| יובל | `.claude/agents/yuval.md` | עיצוב ויצירת תמונות | תמונה של, ציור של, תיצור תמונה, איור / image of, picture of, generate image, illustration, draw |

## Workflow: מציאת תוכן באינטרנט (תהליך מלא)

כשמקבל בקשה למצוא תוכן ולעבד אותו:

1. **CEO מפעיל את חן** למצוא מקור איכותי לפי הנושא
2. **חן בודקת זיכרון** (`chen/Memory/searches.md`) — אם חיפשה דומה לאחרונה, מציעה את הקיים
3. **חן מחפשת, מסננת, ושומרת** ב-`Content/<YYYY-MM-DD>-<slug>.md` עם YAML header של מקור (URL, fetched, author, published)
4. **חן מדווחת ל-CEO**: שם קובץ + לינק למקור
5. **CEO מחליט** לפי **הבקשה המקורית של המשתמש**:
   - "מצא לי מאמר על X" → CEO עוצר ומציג למשתמש
   - "מצא ושכתב על X" → CEO מפעיל את יעל על הקובץ
   - "מצא, שכתב ותיצור תמונות על X" → CEO מפעיל יעל, ובמקביל/אחר כך מפעיל יובל לתמונות, ומציג הכל

## Workflow: שכתוב מאמר

כשמקבל בקשה לשכתוב מאמר קיים (כבר ב-`Content/`):

1. **CEO מפעיל את יעל** עם שם הקובץ ב-`Content/`
2. **יעל קוראת** את `yael/style-guide.md` ואת `yael/reference/` (פעם אחת בסשן), משכתבת לפי הסגנון, ומסירה קישורים/CTAs של המחבר המקורי
3. **יעל שומרת** `Output/<name>.md` + `Output/<name>.html` ומדווחת ל-CEO סיכום + שינויים מרכזיים
4. **CEO מציג** את הפלט למשתמש

> **הערה ארכיטקטונית:** הסוכנים לא מפעילים זה את זה ישירות. CEO הוא המתזמן היחיד. אם המשתמש ביקש תמונות בבקשה המקורית — CEO יזכור זאת ויפעיל את יובל בנפרד אחרי יעל.

## Project-Specific Claude Configuration

The `.claude/` directory contains customizations for this project:

- `.claude/agents/ceo/` — CEO contract (folder form — inert, not Task-invokable)
- `.claude/agents/chen.md` — חן, חוקרת רשת (single-file, Task-invokable)
- `.claude/agents/yael.md` — יעל, משכתבת תוכן (single-file, Task-invokable)
- `.claude/agents/yuval.md` — יובל, מעצב תמונות (single-file, Task-invokable)
- `.claude/skills/` — reusable skill files invokable via slash commands
- `.claude/commands/` — custom slash commands for project workflows

## Directory Structure

```
.claude/
  agents/
    ceo/          ← CEO contract (folder form, not auto-discovered)
    chen.md       ← web research sub-agent
    yael.md       ← content rewriter sub-agent
    yuval.md      ← image designer sub-agent
  skills/
    gpt-image-gen/  ← OpenAI Images API wrapper
    ...
Content/          ← raw articles awaiting rewrite (input for יעל, populated by חן or manually)
Output/           ← rewritten articles (MD + HTML, output from יעל)
chen/
  Memory/
    searches.md   ← search log + dedup ledger
yael/
  style-guide.md  ← house style guide (יעל reads at session start)
  reference/      ← example texts in our style
yuval/
  reference/      ← style reference images (add manually)
  outputs/        ← generated images: <YYYY-MM-DD>-<slug>.png + .txt
vault/            ← Obsidian vault (project documentation)
```
