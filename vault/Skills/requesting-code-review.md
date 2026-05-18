# Requesting Code Review

## מה הסקיל עושה
שולח subagent מיוחד לביצוע code review עם context מדויק — ללא היסטוריית הסשן.

## מתי מפעילים
- **חובה:** אחרי כל משימה ב-subagent-driven-development, אחרי פיצ'ר גדול, לפני merge
- **אופציונלי:** כשתקועים, לפני refactoring, אחרי bug מורכב

## תהליך בקצרה
1. `git rev-parse HEAD~1` (BASE_SHA) ו-`git rev-parse HEAD` (HEAD_SHA)
2. שיגור subagent מסוג `general-purpose` עם תבנית מ-`code-reviewer.md`
3. טיפול בפידבק: Critical → מיידי, Important → לפני המשך, Minor → רשום לאחר כך

## סקילים קשורים
- [[receiving-code-review]] — כיצד לטפל בפידבק שמתקבל
- [[subagent-driven-development]] — review אחרי כל משימה
- [[finishing-a-development-branch]] — review לפני merge
