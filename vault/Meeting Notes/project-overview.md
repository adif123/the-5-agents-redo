# Project Overview

## Overview
מערכת יצירת תוכן מרובת-סוכנים (multi-agent content-creation system). סוכן "CEO" ראשי מתפקד כאורכסטרטור ומתאם צוות של sub-agents מתמחים, כל אחד אחראי על היבט שונה של ייצור תוכן. רשימת הסוכנים ותחומי אחריותם מוגדרים בצורה מצטברת. הפרויקט נמצא בשלב ראשוני — תשתית קיימת אך סוכנים טרם הוגדרו.

## Open Questions
- אילו sub-agents ייכללו בצוות ומה תחום אחריותו של כל אחד?
- מה פרוטוקול התקשורת בין ה-CEO לבין ה-sub-agents?
- האם המערכת תתבסס על Anthropic API בלבד, או גם על OpenAI (שניהם מופיעים ב-.env.example)?

## Session Log

### 2026-05-19 — סריקה ראשונית של הפרויקט [wip]
- **What was done:** נסרקו קבצי הפרויקט הקיימים: CLAUDE.md, .env.example, .claude/ (agents/commands/skills). ה-vault אורגן לראשונה.
- **Decisions:** הפרויקט הוגדר כ-multi-agent system עם CEO orchestrator. אין קוד עסקי עדיין — רק תשתית Claude Code (skills, config).
- **Notes / Caveats:** `.claude/agents/` ריק כרגע (רק .gitkeep). כל ה-skills הגיעו מ-Superpowers install.
- **Related:** [[claude-configuration]], [[skills-roster]]

### 2026-05-19 — CEO Agent contract עוגן בפרויקט [shipped]
- **What was done:** נוצר `agents/ceo/agent.md` (ה-contract המלא, 10 סעיפים לפי PRD סעיף 5.2) + `agents/ceo/_index.md`. עודכן `CLAUDE.md` עם בלוק `## CEO Agent Protocol` שמחייב טעינת ה-contract בכל סשן.
- **Decisions:** ה-CEO הוא ה-main Claude session ולא sub-agent נפרד — דפוס supervisor סטנדרטי. ה-contract בקובץ נפרד (לא inline ב-CLAUDE.md) כדי לאפשר עדכון עצמאי. רישום AGT-01..AGT-04 נשאר `[TBD]` בכוונה.
- **Notes / Caveats:** ה-contract באנגלית, אך Language Rules מחייבות תשובות בעברית מלאה כשה-input בעברית. `.claude/agents/` עדיין ריק — sub-agents ייווצרו אינקרמנטלית.
- **Related:** [[ceo-agent]], [[claude-configuration]]
