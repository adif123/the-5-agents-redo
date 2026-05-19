# יובל — מעצב התמונות

## Overview
יובל (AGT-02) הוא סוכן יצירת תמונות של המערכת. קובץ הסוכן: `.claude/agents/yuval.md` (single-file, Task-invokable). יובל קורא ל-OpenAI Images API (מודל `gpt-image-2`) דרך skill `gpt-image-gen`. לפני כל יצירה הוא סורק `yuval/reference/` לזיהוי סגנון ועקביות ויזואלית, ושומר פלט ב-`yuval/outputs/<YYYY-MM-DD>-<slug>.png` עם sidecar `.txt` של ה-prompt.

## Open Questions
- `yuval/reference/` ריק כרגע — מתי ומה יתווסף?
- האם יובל יקבל feedback על תמונות ויאטרייט, או שכל קריאה היא one-shot?

## Session Log

### 2026-05-19 — יצירת סוכן יובל + skill gpt-image-gen [shipped]
- **What was done:** נוצר `.claude/agents/yuval.md` עם workflow מלא (7 שלבים: סריקת reference, ניסוח prompt, קריאת API, decode, שמירה, אימות, דיווח). נוצר `.claude/skills/gpt-image-gen/SKILL.md` עם curl command + Python fallback לבסיס64. נוצרו `yuval/reference/` ו-`yuval/outputs/`.
- **Decisions:** מודל `gpt-image-2` — לא לשנות. שמירת sidecar `.txt` לכל תמונה — חובה לאיטרציה. אימות size > 0 לפני דיווח ל-CEO — מניעת silent failures.
- **Notes / Caveats:** `gpt-image-2` יצא אפריל 2026, ייתכן שלא ידוע לידע הפנימי של המודל — זה תקין, המודל קיים.
- **Related:** [[project-overview]], [[ceo-agent]], [[yael-agent]]
