# Writing Plans

## מה הסקיל עושה
כותב תכנית מימוש מפורטת — משימה אחרי משימה, כל שלב עם קוד מלא, פקודות מדויקות, ואין placeholders.

## מתי מפעילים
כשיש spec או דרישות למשימה מרובת שלבים, לפני נגיעה בקוד.

## תבנית חובה בראש כל תכנית
```
# [Feature Name] Implementation Plan
Goal: [משפט אחד]
Architecture: [2-3 משפטים]
Tech Stack: [טכנולוגיות מרכזיות]
```

## כללי ברזל
- **אין placeholders** — "TBD", "implement later", "handle edge cases" = כשל
- **קוד מלא בכל שלב** — לא "write code that does X", אלא הקוד עצמו
- **paths מדויקים** — לא "create a file", אלא `src/exact/path/file.ts`
- **פקודות עם output צפוי** — `npm test` + `Expected: PASS`

## סדר הגרנולריות
כל step = פעולה אחת (2-5 דקות): כתוב טסט → הרץ → ממש → הרץ → commit

## לאחר כתיבה
- self-review: spec coverage, placeholders, type consistency
- שאל משתמש לבחור ביצוע: Subagent-Driven או Inline

## שמירה ב
`docs/superpowers/plans/YYYY-MM-DD-<feature-name>.md`

## סקילים קשורים
- [[brainstorming]] — הסקיל שקודם לזה
- [[subagent-driven-development]] — ביצוע מומלץ
- [[executing-plans]] — ביצוע אלטרנטיבי
