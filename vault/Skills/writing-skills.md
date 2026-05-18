# Writing Skills

## מה הסקיל עושה
יוצר וערוך סקילים חדשים בשיטת TDD — בודק baseline ללא הסקיל, כותב, בודק שוב, וסוגר פרצות.

## מתי מפעילים
כשיוצרים סקיל חדש, עורכים קיים, או בודקים לפני deployment.

## Iron Law
**אין סקיל ללא failing test קודם.** אותו עיקרון כמו TDD לקוד.

## מחזור RED-GREEN-REFACTOR לסקילים
- **RED:** הרץ pressure scenario עם subagent **ללא** הסקיל — תעד אילו rationalization הוא משתמש
- **GREEN:** כתוב סקיל שמתמודד בדיוק עם אותם rationalizations
- **REFACTOR:** מצא rationalizations חדשים → סגור → בדוק שוב

## מבנה SKILL.md
```yaml
---
name: skill-name-with-hyphens
description: Use when [triggering conditions — NOT workflow summary]
---
```
- `description` = מתי להפעיל, לא מה הסקיל עושה
- שמות: אותיות, מספרים, מקפים בלבד

## סקילים קשורים
- [[test-driven-development]] — אותו עיקרון, מותאם לתיעוד
