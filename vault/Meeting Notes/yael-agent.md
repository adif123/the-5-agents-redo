# יעל — כותבת התוכן

## Overview
יעל (AGT-01) היא סוכנת כתיבת תוכן של המערכת. קובץ הסוכן: `.claude/agents/yael.md` (single-file, Task-invokable). יעל כותבת מאמרים ותוכן ארוך-טווח בעברית ובאנגלית, שומרת פלט ב-`Output/<slug>.md` + `.html`, ומשאירה `{{IMAGE_NEEDED: "..."}}` placeholders בכל מקום שתמונה מוסיפה ערך. בסיום היא מחזירה ל-CEO סיכום + רשימת placeholders מובנית לניתוב ליובל.

## Open Questions
- סגנון כתיבה ברירת מחדל: טרם הוגדר (פורמלי / שיחתי / לפי הקשר)
- האם יעל אמורה לקרוא Brand Guidelines לפני כתיבה כשיש כאלה?

## Session Log

### 2026-05-19 — יצירת סוכן יעל [shipped]
- **What was done:** נוצר `.claude/agents/yael.md` עם workflow מלא: הבנת בקשה, כתיבה ב-Markdown, הוספת `{{IMAGE_NEEDED: "..."}}` placeholders, יצירת HTML, ודיווח מובנה ל-CEO. נוצרה תיקיית `Output/` (implicit — יעל יוצרת בעצמה).
- **Decisions:** פורמט ה-placeholder `{{IMAGE_NEEDED: "..."}}` נבחר כדי להיות parse-friendly ל-CEO (regex פשוט) ומפורט מספיק ליובל (תיאור מלא בתוך ה-string). יעל שומרת פלט לפני שהתמונות מוכנות — CEO מבצע ה-replacement לאחר מכן.
- **Notes / Caveats:** יעל לא קיימת קודם לכן — זוהי יצירה ראשונה, לא עדכון.
- **Related:** [[project-overview]], [[ceo-agent]], [[yuval-agent]]
