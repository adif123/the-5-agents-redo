# Using Git Worktrees

## מה הסקיל עושה
מקים workspace מבודד לעבודה על פיצ'ר — מונע מהעבודה להשפיע על הענף הנוכחי.

## מתי מפעילים
בתחילת עבודה על פיצ'ר שדורש בידוד, או לפני ביצוע תכנית מימוש.

## תהליך בקצרה

**שלב 0 — זיהוי:** האם כבר בתוך worktree מבודד? אם כן — לא יוצרים חדש.

**שלב 1 — יצירה:**
- קודם: כלים native של הפלטפורמה (`EnterWorktree` אם קיים)
- fallback: `git worktree add` — רק אם אין כלי native

**שלב 2 — הגדרה:** התקנת dependencies לפי שפת הפרויקט

**שלב 3 — baseline:** הרצת הטסטים — אם כושלים, מדווחים ושואלים אם להמשיך

**חובה לפני יצירה ב-project-local:**
`git check-ignore` — אם התיקייה לא ב-`.gitignore`, מוסיפים אותה ועושים commit לפני.

## סקילים קשורים
- [[executing-plans]] — דורש worktree
- [[subagent-driven-development]] — דורש worktree
- [[finishing-a-development-branch]] — מנקה את ה-worktree בסיום
