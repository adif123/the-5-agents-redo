# Project Overview

## Overview
מערכת יצירת תוכן מרובת-סוכנים (multi-agent content-creation system). סוכן CEO ראשי מתפקד כאורכסטרטור ומתאם צוות של sub-agents מתמחים. נכון ל-2026-05-19: AGT-01 יעל (משכתבת מאמרים) ו-AGT-02 יובל (יצירת תמונות) פעילים. יעל לוקחת מאמרי גלם מ-`Content/`, משכתבת לפי `yael/style-guide.md`, ושומרת MD+HTML ב-`Output/`. יובל יוצר תמונות דרך OpenAI Images API (`gpt-image-2`). הסוכנים לא מתקשרים ישירות — CEO מתזמן כל אחד בנפרד.

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

### 2026-05-19 — יעל pivot למשכתבת + Content/ + Output/ נוצרו [shipped]
- **What was done:** ה-scope של יעל שונה לחלוטין: ממסכ"לית "כותבת מאפס עם image placeholders" ל"משכתבת מאמרי גלם בסגנון בית". `.claude/agents/yael.md` נכתב מחדש עם כלים מצומצמים (Read/Write/Edit/Glob/Grep — בלי Bash). נוצרה תשתית: `Content/` (מאמרי גלם), `Output/` (פלט), `yael/style-guide.md` (placeholder TODO), `yael/reference/`. CLAUDE.md עודכן: trigger keywords חדשים (שכתב/ערוך/תרגם/סכם), workflow "שכתוב מאמר" החליף את "מאמר עם תמונות". CEO routing rules עודכנו בהתאם.
- **Decisions:** יעל ויובל לא מתקשרים ישירות — CEO מתזמן בנפרד. אם יבקשו מאמר עם תמונות, CEO יפעיל את יעל ואת יובל בקריאות נפרדות ויציג שני outputs. ה-style-guide נשאר placeholder ריק — המשתמש ימלא אותו בנפרד.
- **Notes / Caveats:** ה-trigger keywords של יעל חופפים חלקית לקודמים (`מאמר`, `תוכן`) אבל הסמנטיקה שונה — יעל לא יוצרת תוכן חדש. בקשות כתיבה מאפס לא ימופו לסוכן קיים.
- **Related:** [[yael-agent]], [[ceo-agent]]
