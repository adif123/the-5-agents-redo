# יעל — כותבת התוכן

## Overview
יעל (AGT-01) היא סוכנת **שכתוב ועריכה** של המערכת. קובץ הסוכן: `.claude/agents/yael.md` (single-file, Task-invokable). יעל לוקחת מאמרי גלם מ-`Content/`, קוראת את `yael/style-guide.md` ואת `yael/reference/`, ומשכתבת בסגנון הבית. מסירה קישורים/CTAs של המחבר המקורי; שומרת מותגים שמוזכרים בתוך הסיפור. שומרת פלט כ-`Output/<name>.md` + `Output/<name>.html`. כלים מצומצמים: `Read, Write, Edit, Glob, Grep` בלבד — בלי Bash, בלי API, בלי הפעלת sub-agents, בלי יצירת תמונות.

## Open Questions
- `yael/style-guide.md` ריק — המשתמש יצטרך למלא אותו (placeholder עם TODO נוצר)
- `yael/reference/` ריק — איזה דוגמאות יתווספו?
- תרגום: באיזה מצב יעל מתרגמת מאנגלית לעברית? אוטומטית לפי שפת בקשת המשתמש, או רק אם מבקשים במפורש?

## Session Log

### 2026-05-19 — יצירת סוכן יעל [shipped]
- **What was done:** נוצר `.claude/agents/yael.md` עם workflow מלא: הבנת בקשה, כתיבה ב-Markdown, הוספת `{{IMAGE_NEEDED: "..."}}` placeholders, יצירת HTML, ודיווח מובנה ל-CEO. נוצרה תיקיית `Output/` (implicit — יעל יוצרת בעצמה).
- **Decisions:** פורמט ה-placeholder `{{IMAGE_NEEDED: "..."}}` נבחר כדי להיות parse-friendly ל-CEO (regex פשוט) ומפורט מספיק ליובל (תיאור מלא בתוך ה-string). יעל שומרת פלט לפני שהתמונות מוכנות — CEO מבצע ה-replacement לאחר מכן.
- **Notes / Caveats:** יעל לא קיימת קודם לכן — זוהי יצירה ראשונה, לא עדכון.
- **Related:** [[project-overview]], [[ceo-agent]], [[yuval-agent]]

### 2026-05-19 — pivot ליעל: משכתבת בלבד [shipped]
- **What was done:** שונה ה-scope של יעל מ"כותבת מאפס עם image placeholders" ל"משכתבת מאמרי גלם מ-`Content/`". `.claude/agents/yael.md` נכתב מחדש: כלים צומצמו (Read/Write/Edit/Glob/Grep — בלי Bash); נוסף שלב טעינת style-guide + reference; נוספו כללים להסרת קישורים/CTAs ושמירת מותגים שבתוך הסיפור. נוצרו `yael/style-guide.md` (placeholder), `yael/reference/.gitkeep`, `Content/.gitkeep`, `Output/.gitkeep`. CLAUDE.md עודכן: trigger keywords חדשים, workflow "שכתוב מאמר" החליף את "מאמר עם תמונות". CEO routing rules עודכנו בהתאם.
- **Decisions:** ה-handoff יעל→יובל לא קיים יותר — יעל בלי גישה ל-sub-agents. אם משתמש מבקש "מאמר עם תמונות", CEO מנתב לשתיהן בנפרד ומציג שני outputs. ה-style-guide נשאר ריק לכוונה — המשתמש ימלא אותו.
- **Notes / Caveats:** ה-pivot שינה לחלוטין את תפיסת התפקיד של יעל. ה-trigger keywords חופפים חלקית לקודמים (`מאמר`, `תוכן`) אבל הסמנטיקה שונה: יעל לא יוצרת תוכן חדש מאפס.
- **Related:** [[project-overview]], [[ceo-agent]], [[yuval-agent]]
