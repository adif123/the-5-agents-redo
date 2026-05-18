# Skills Vault Documentation

## Overview
תיעוד של כל 17 הסקילים הזמינים בפרויקט בתיקיית `vault/Skills/`. כל סקיל קיבל קובץ עצמאי עם תיאור מה הוא עושה, מתי מפעילים אותו, וסקילים קשורים. הקבצים משתמשים ב-wikilinks לניווט בין הסקילים.

## Open Questions
- האם לארגן את תיקיית Skills לתת-תיקיות (Process/Quality/Agents/Obsidian) או להשאיר שטוח?
- none

## Session Log

### 2026-05-18 — יצירת תיעוד Skills [shipped]
- **What was done:** קריאת כל 17 קבצי `SKILL.md` מ-`.claude/skills/`, יצירת `vault/Skills/` עם קובץ לכל סקיל ו-`_index.md` המרכז את כולם. עדכון `vault/Meeting Notes/_index.md`.
- **Decisions:** קבצי Skills מתארים רק מה הסקיל עושה ומתי מפעילים אותו — לא פירוט טכני פנימי. קבצי עזר פנימיים של הסקילים (implementer-prompt.md, visual-companion.md) לא נכללו.
- **Notes / Caveats:** ה-index מחולק ל-4 קטגוריות: תהליך פיתוח, איכות קוד, agents, Obsidian. מבנה זה ניתן לשינוי.
- **Related:** [[project-documentation-scan]]
