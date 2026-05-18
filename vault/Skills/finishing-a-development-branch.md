# Finishing a Development Branch

## מה הסקיל עושה
מוודא שהטסטים עוברים, מזהה את מצב ה-workspace, ומציג 4 אפשרויות להשלמת העבודה.

## מתי מפעילים
כשהמימוש הסתיים וכל הטסטים עוברים — לפני merge, PR, או ניקוי.

## 4 האפשרויות
1. **Merge מקומי** — merge ל-base branch, ניקוי worktree
2. **Push + PR** — push לריפו, יצירת Pull Request
3. **שמור כמות שהוא** — הענף נשמר לטיפול מאוחר יותר
4. **מחיקה** — דורשת אישור מפורש (`discard`)

**לעולם לא מציגים את האפשרויות לפני שהטסטים עוברים.**

## סקילים קשורים
- [[executing-plans]] — קורא לסקיל זה בסיום
- [[subagent-driven-development]] — קורא לסקיל זה בסיום
- [[verification-before-completion]] — חייב לרוץ לפני
- [[requesting-code-review]] — אופציונלי לפני merge
