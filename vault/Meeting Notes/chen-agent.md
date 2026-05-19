# חן — חוקרת הרשת

## Overview
חן (AGT-03) היא סוכנת מחקר רשת. קובץ הסוכן: `.claude/agents/chen.md` (single-file, Task-invokable). חן מקבלת בקשת מחקר מ-CEO, מחפשת ברשת (`WebSearch` + `WebFetch`), מסננת לפי קריטריוני איכות, ומניחה את המקור הטוב ביותר כקובץ ב-`Content/<YYYY-MM-DD>-<slug>.md` עם YAML header (source/fetched/author/published). מנהלת זיכרון חיפושים ב-`chen/Memory/searches.md` ובודקת deduplication ב-`Grep` לפני כל חיפוש. כלים: `WebSearch, WebFetch, Read, Write, Edit, Glob, Grep` — בלי Bash, בלי יצירת תמונות, בלי הפעלת sub-agents. CEO הוא היחיד שמתזמן את השרשרת חן → יעל → יובל.

## Open Questions
- איך חן תתמודד עם paywalls? (Bloomberg, NYT, FT)
- מה ה-rate limit של `WebSearch` ב-Claude Code? (לא מתועד באופן ברור)
- האם נדרש fallback אם `WebFetch` נחסם ע"י robots.txt? (כרגע מדווח כשלון ל-CEO)
- האם להוסיף TTL אוטומטי ל-cache (30 ימים)? כרגע ה-30 יום הוא heuristic ש-חן בודקת ידנית

## Session Log

### 2026-05-19 — יצירת סוכנת חן (AGT-03) [shipped]
- **What was done:** נוצר `.claude/agents/chen.md` עם workflow 8 שלבים: קבלת בקשה, בדיקת זיכרון (Grep), חיפוש (2-3 שאילתות), סינון איכות (5-star rubric), חילוץ (WebFetch), שמירה ב-`Content/` עם YAML header, עדכון memory log, דיווח מובנה ל-CEO. נוצרה תיקייה `chen/Memory/` עם `searches.md` ריק (header בלבד). עודכן CEO agent.md: AGT-03 נרשם, routing rules הוספו כולל composite flows. CLAUDE.md עודכן: agent team table, workflow "מציאת תוכן באינטרנט", directory structure.
- **Decisions:** חן לא יוצרת תמונות ולא משכתבת בסגנון — תפקידה בלבד מחקר ומציאה. CEO הוא המתזמן היחיד — חן לא קוראת ליעל ישירות. ה-handoff: חן → Content/ → CEO → יעל (אם המשתמש ביקש שכתוב). פורמט slug: `<YYYY-MM-DD>-<3-5 מילים kebab-case>`. דדופליקציה ב-Grep על memory log לפני כל חיפוש — priority #1.
- **Notes / Caveats:** ה-tri-agent pipeline (חן → יעל → יובל) מוסדר עכשיו אבל מותנה ב-CEO לזיהוי intent מהבקשה המקורית (יעל לא מבקשת תמונות).
- **Related:** [[project-overview]], [[ceo-agent]], [[yael-agent]], [[yuval-agent]]
