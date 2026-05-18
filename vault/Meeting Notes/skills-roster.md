# Skills Roster

## Overview
הפרויקט כולל 16 skills מותקנות תחת `.claude/skills/`, כולן הגיעו מ-Superpowers install. כל skill מופעלת כ-slash command. הסקילים מכסים: workflow (brainstorming, plans, execution), code quality (TDD, debugging, review), Obsidian (markdown, bases, vault-workflow), ו-meta skills (using-superpowers, writing-skills). בנוסף הותקן plugin חיצוני: `skill-creator@claude-plugins-official` לכתיבת skills חדשים.

## Open Questions
- האם יתווספו skills מותאמות-פרויקט לאחר שה-agents יוגדרו?
- האם ה-skill `skill-creator` ישמש ליצירת skills ייעודיות לסוכני התוכן?

## Session Log

### 2026-05-19 — תיעוד רשימת skills ראשונית [shipped]
- **What was done:** נסרקו כל 16 ה-skills. תועדו לפי קטגוריות. תועד ה-plugin skill-creator שהותקן בסשן זה.
- **Decisions:** לא הוסרו או שונו skills — הרשימה הנוכחית מתאימה לשלב ה-scaffolding.
- **Notes / Caveats:** ל-`brainstorming` יש scripts (server.cjs, HTML template) — skill כבדה יחסית. `systematic-debugging` כולל קבצי reference נוספים.
- **Related:** [[claude-configuration]], [[project-overview]]

---

## רשימת Skills מלאה

| Skill | תיאור |
|---|---|
| `brainstorming` | חקירת intent ודרישות לפני כל עבודה יצירתית |
| `dispatching-parallel-agents` | הרצת 2+ tasks עצמאיים במקביל |
| `executing-plans` | הרצת plan קיים ב-session נפרד עם checkpoints |
| `finishing-a-development-branch` | סגירת branch — merge/PR/cleanup |
| `obsidian-bases` | יצירת .base files ב-Obsidian |
| `obsidian-markdown` | כתיבת Obsidian Flavored Markdown |
| `obsidian-vault-workflow` | פרוטוקול חובה לקריאה/כתיבה ב-vault |
| `receiving-code-review` | טיפול בפידבק code review |
| `requesting-code-review` | בקשת code review לפני merge |
| `subagent-driven-development` | הרצת implementation plans עם sub-agents |
| `systematic-debugging` | דיבאג מובנה לכל באג או כישלון |
| `test-driven-development` | כתיבת טסטים לפני implementation |
| `using-git-worktrees` | בידוד עבודה ב-git worktree |
| `using-superpowers` | כיצד למצא ולהשתמש ב-skills |
| `verification-before-completion` | אימות לפני הצהרת הצלחה |
| `writing-plans` | כתיבת implementation plan לפני קוד |
| `writing-skills` | יצירת ועריכת skills חדשות |
