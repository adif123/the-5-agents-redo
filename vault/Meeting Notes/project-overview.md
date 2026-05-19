# Project Overview

## Overview
מערכת יצירת תוכן מרובת-סוכנים (multi-agent content-creation system). סוכן CEO ראשי מתפקד כאורכסטרטור ומתאם צוות של sub-agents מתמחים. נכון ל-2026-05-19: AGT-01 יעל (כתיבת תוכן) ו-AGT-02 יובל (עיצוב תמונות) פעילים. תהליך מלא ליצירת מאמר עם תמונות מוגדר ועובד. המערכת משתמשת ב-Anthropic API (Claude) לאורכסטרציה וכתיבה, ו-OpenAI API (gpt-image-2) ליצירת תמונות.

## Open Questions
- AGT-03 ו-AGT-04: שמות ותחומים טרם הוגדרו
- מנגנון memory persistence בין סשנים: PRD סעיף 7 פתוח

## Session Log

### 2026-05-19 — סריקה ראשונית של הפרויקט [wip]
- **What was done:** נסרקו קבצי הפרויקט הקיימים: CLAUDE.md, .env.example, .claude/ (agents/commands/skills). ה-vault אורגן לראשונה.
- **Decisions:** הפרויקט הוגדר כ-multi-agent system עם CEO orchestrator. אין קוד עסקי עדיין — רק תשתית Claude Code (skills, config).
- **Notes / Caveats:** `.claude/agents/` ריק כרגע (רק .gitkeep). כל ה-skills הגיעו מ-Superpowers install.
- **Related:** [[claude-configuration]], [[skills-roster]]

### 2026-05-19 — יעל + יובל + gpt-image-gen + workflow מלא [shipped]
- **What was done:** נוצרו AGT-01 יעל (`.claude/agents/yael.md`) ו-AGT-02 יובל (`.claude/agents/yuval.md`). נוסף skill `gpt-image-gen` עם curl + Python fallback לקריאת OpenAI Images API (מודל `gpt-image-2`). נוצרה תיקיית עבודה `yuval/reference/` + `yuval/outputs/`. עודכן `CLAUDE.md` עם טבלת צוות, workflow מאמר+תמונות, ו-directory structure. עודכן CEO agent.md: AGT-01/AGT-02 רשומים, routing rules מוגדרות.
- **Decisions:** יעל כותבת מאמר ומשאירה `{{IMAGE_NEEDED: "..."}}` placeholders; CEO מפעיל יובל לכל placeholder; CEO משלב את התמונות בקבצי יעל ושומר ב-`Output/`. פרוטוקול בין-סוכני מבוסס על structured text output (לא API נפרד).
- **Notes / Caveats:** יעל לא קיימת עדיין — נוצרה ב-session זה (לא "עודכנה"). `.env` כבר הכיל `OPENAI_API_KEY`. גרסת gpt-image-2 יצאה אפריל 2026, לא ידועה לידע הפנימי — המודל קיים ונכון.
- **Related:** [[ceo-agent]], [[yael-agent]], [[yuval-agent]]

### 2026-05-19 — CEO Agent contract עוגן בפרויקט [shipped]
- **What was done:** נוצר `agents/ceo/agent.md` (ה-contract המלא, 10 סעיפים לפי PRD סעיף 5.2) + `agents/ceo/_index.md`. עודכן `CLAUDE.md` עם בלוק `## CEO Agent Protocol` שמחייב טעינת ה-contract בכל סשן.
- **Decisions:** ה-CEO הוא ה-main Claude session ולא sub-agent נפרד — דפוס supervisor סטנדרטי. ה-contract בקובץ נפרד (לא inline ב-CLAUDE.md) כדי לאפשר עדכון עצמאי. רישום AGT-01..AGT-04 נשאר `[TBD]` בכוונה.
- **Notes / Caveats:** ה-contract באנגלית, אך Language Rules מחייבות תשובות בעברית מלאה כשה-input בעברית. `.claude/agents/` עדיין ריק — sub-agents ייווצרו אינקרמנטלית.
- **Related:** [[ceo-agent]], [[claude-configuration]]
