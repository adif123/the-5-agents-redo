# גיא — שומר הסף האחרון (QA)

## Overview
גיא (AGT-04) הוא הסוכן ה-5 והאחרון בשרשרת — בלעדיו אין סגירת לולאה. קובץ הסוכן: `.claude/agents/guy.md` (single-file, Task-invokable). אחרי שיעל מחזירה תוצר סופי (עם תמונות אם נדרשו), CEO מפעיל את גיא **אוטומטית** — גם בלי trigger מפורש מהמשתמש. גיא קורא את התוצר ב-`Output/`, מאמת מול הבריף + `yael/style-guide.md` + 5 קטגוריות (רלוונטיות, סגנון, מבנה, תמונות, שלמות טכנית), ומפיק דוח QA מובנה ב-`guy/QA_Reports/<YYYY-MM-DD-HHMM>-<slug>.md`. מחזיר ל-CEO ✅ מאושר או ❌ דורש תיקון. כלים: `Read, Glob, Grep, Write` בלבד — read-mostly, **בלי Edit על התוצרים, בלי Bash, בלי Web, בלי API**. גיא הוא הסוכן היחיד שמורשה לדחות תוצר — ללא אישורו, שום דבר לא יוצא למשתמש. הלולאה רצה עד 3 סבבים: ❌ → CEO מפעיל את יעל מחדש עם תקציר ההערות → סבב הבא. בסבב 3 אם גיא דוחה — CEO מציג למשתמש לקבלת החלטה ידנית.

## Open Questions
- האם להוסיף trigger אוטומטי גם לזרמי `chen-only` (כשהמשתמש מבקש "מצא לי מאמר על X")? כרגע גיא רץ רק כשיש `Output/` file
- מה לעשות אם `yael/style-guide.md` חלקי (יש תוכן אבל לא מלא)? כרגע הכלל: ריק → דלג; אחרת → בדיקה מלאה
- האם להוסיף קטגוריית בדיקה 6 — "מקוריות" (anti-plagiarism, anti-paraphrase-too-close-to-source)?
- מה ה-policy אם CEO רוצה לדלג על QA במכוון (למשל debug session)? כרגע non-skippable

## Session Log

### 2026-05-19 — יצירת סוכן גיא (AGT-04) [shipped]
- **What was done:** נוצר `.claude/agents/guy.md` עם workflow 7 שלבים (קריאת תוצר, סגנון, מקור, צ'קליסט, דוח, דיווח, סיום). 5 קטגוריות בדיקה: רלוונטיות לבריף, סגנון ומיתוג, שלמות מבנית, תמונות (אם נבקשו), שלמות טכנית. כלים: `Read, Glob, Grep, Write` — read-mostly, בלי Edit על תוצרים. נוצרה תיקיית `guy/` עם `agent.md` (pointer) ו-`QA_Reports/.gitkeep`. עודכן `.claude/agents/ceo/agent.md`: AGT-04 בטבלת Sub-Agents, routing rule חדש + auto-trigger ב-composite flows, סעיף חדש "QA Loop Protocol" (3 סבבים), שתי constraints חדשות. עודכן `CLAUDE.md`: שורת גיא בטבלת Agent Team, סעיף "Workflow: QA Loop", `guy/` ב-Directory Structure.
- **Decisions:** גיא = read-mostly. בלי Edit על תוצרים — רק כתיבת דוחות. הלולאה מקסימום 3 סבבים. אם `yael/style-guide.md` ריק → גיא **לא נכשל**, אלא מסמן את הקטגוריה כדולגת עם הערה. הטמעת תמונות: base64 וקישור יחסי שניהם תקפים — גיא לא אוכף פורמט הטמעה ספציפי. גיא הוא הסוכן היחיד שמורשה לדחות תוצר. גיא לא יכול להפעיל סוכנים אחרים — CEO הוא המתזמן היחיד; הוא מקבל את הדוח מגיא ומפעיל את יעל מחדש אם נדרש.
- **Notes / Caveats:** הצ'קליסט המקורי בבקשת המשתמש כלל בדיקת `{{IMAGE_NEEDED: ...}}` placeholders — הוסר בארכיטקטורה הנוכחית (יעל לא משאירה placeholders, CEO מזהה כוונת תמונה מהבקשה המקורית). הוחלף בבדיקות קיום + הטמעה + alt text. ה-QA הראשון בפועל יוכל לרוץ על `Output/2026-05-19-ai-news.md` (התוצר מהסשן הזה).
- **Related:** [[project-overview]], [[ceo-agent]], [[yael-agent]], [[yuval-agent]], [[chen-agent]]
