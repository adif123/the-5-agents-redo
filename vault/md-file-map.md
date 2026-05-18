# MD File Map — the-5-agents-redo

Complete reference of every Markdown file in the project.

---

## Root

### `CLAUDE.md`
- **מה הוא עושה:** הגדרת הפרויקט ל-Claude Code. מסביר שמדובר במערכת multi-agent ליצירת תוכן, ומציין את תפקיד ה-CEO orchestrator ואת מיקום תיקיות ה-`.claude/`.
- **משויך ל:** Claude Code harness — נטען אוטומטית בכל סשן.
- **קבצים קשורים:** [[project-setup]], כל קבצי ה-SKILL.md

---

## Skills — Superpowers (מקור: obra/superpowers)

### `.claude/skills/brainstorming/SKILL.md`
- **מה הוא עושה:** סקיל חובה לפני כל עבודה יצירתית. בוחן את כוונת המשתמש, דרישות ועיצוב לפני יישום.
- **משויך ל:** כל פיצ'ר/קומפוננט חדש
- **קבצים קשורים:** [[spec-document-reviewer-prompt]], [[visual-companion]]

### `.claude/skills/brainstorming/spec-document-reviewer-prompt.md`
- **מה הוא עושה:** תבנית prompt לשליחת sub-agent שסוקר מסמך spec.
- **משויך ל:** `brainstorming/SKILL.md`
- **קבצים קשורים:** `.claude/skills/brainstorming/SKILL.md`

### `.claude/skills/brainstorming/visual-companion.md`
- **מה הוא עושה:** מדריך לעזר ויזואלי מבוסס דפדפן — הצגת mockups, דיאגרמות ואפשרויות.
- **משויך ל:** `brainstorming/SKILL.md`
- **קבצים קשורים:** `.claude/skills/brainstorming/SKILL.md`

### `.claude/skills/dispatching-parallel-agents/SKILL.md`
- **מה הוא עושה:** סקיל להפעלת 2+ agents במקביל על משימות עצמאיות ללא shared state.
- **משויך ל:** משימות מקביליות
- **קבצים קשורים:** `subagent-driven-development/SKILL.md`

### `.claude/skills/executing-plans/SKILL.md`
- **מה הוא עושה:** סקיל לביצוע תכנית מימוש קיימת בסשן נפרד עם נקודות review.
- **משויך ל:** `writing-plans/SKILL.md`
- **קבצים קשורים:** `writing-plans/SKILL.md`, `subagent-driven-development/SKILL.md`

### `.claude/skills/finishing-a-development-branch/SKILL.md`
- **מה הוא עושה:** מדריך לסיום ענף פיתוח — merge, PR, או cleanup — כשהמימוש הסתיים.
- **משויך ל:** שלב סיום פיתוח
- **קבצים קשורים:** `requesting-code-review/SKILL.md`, `verification-before-completion/SKILL.md`

### `.claude/skills/receiving-code-review/SKILL.md`
- **מה הוא עושה:** סקיל לטיפול בפידבק של code review — לפני יישום הערות, בוחן את תקפותן.
- **משויך ל:** תהליך code review
- **קבצים קשורים:** `requesting-code-review/SKILL.md`

### `.claude/skills/requesting-code-review/SKILL.md`
- **מה הוא עושה:** סקיל לבקשת code review לאחר השלמת פיצ'ר או לפני merge.
- **משויך ל:** תהליך code review
- **קבצים קשורים:** `receiving-code-review/SKILL.md`, `code-reviewer.md`, `finishing-a-development-branch/SKILL.md`

### `.claude/skills/requesting-code-review/code-reviewer.md`
- **מה הוא עושה:** תבנית prompt לשליחת sub-agent שמבצע code review.
- **משויך ל:** `requesting-code-review/SKILL.md`
- **קבצים קשורים:** `requesting-code-review/SKILL.md`

### `.claude/skills/subagent-driven-development/SKILL.md`
- **מה הוא עושה:** סקיל לביצוע תכנית מימוש עם tasks עצמאיים בסשן הנוכחי.
- **משויך ל:** `executing-plans/SKILL.md`
- **קבצים קשורים:** `implementer-prompt.md`, `spec-reviewer-prompt.md`, `code-quality-reviewer-prompt.md`

### `.claude/skills/subagent-driven-development/implementer-prompt.md`
- **מה הוא עושה:** תבנית prompt לשליחת sub-agent שמממש קוד.
- **משויך ל:** `subagent-driven-development/SKILL.md`
- **קבצים קשורים:** `subagent-driven-development/SKILL.md`

### `.claude/skills/subagent-driven-development/spec-reviewer-prompt.md`
- **מה הוא עושה:** תבנית prompt לשליחת sub-agent שבודק עמידה ב-spec.
- **משויך ל:** `subagent-driven-development/SKILL.md`
- **קבצים קשורים:** `subagent-driven-development/SKILL.md`

### `.claude/skills/subagent-driven-development/code-quality-reviewer-prompt.md`
- **מה הוא עושה:** תבנית prompt לשליחת sub-agent שבודק איכות קוד.
- **משויך ל:** `subagent-driven-development/SKILL.md`
- **קבצים קשורים:** `subagent-driven-development/SKILL.md`

### `.claude/skills/systematic-debugging/SKILL.md`
- **מה הוא עושה:** סקיל לדיבוג שיטתי — לפני כל תיקון, לאחר כישלון טסט או התנהגות לא צפויה.
- **משויך ל:** כל תיקון באגים
- **קבצים קשורים:** `condition-based-waiting.md`, `defense-in-depth.md`, `root-cause-tracing.md`

### `.claude/skills/systematic-debugging/CREATION-LOG.md`
- **מה הוא עושה:** לוג יצירת הסקיל — דוגמה לתהליך extraction ומבנה של סקיל.
- **משויך ל:** `systematic-debugging/SKILL.md`
- **קבצים קשורים:** `writing-skills/SKILL.md`

### `.claude/skills/systematic-debugging/condition-based-waiting.md`
- **מה הוא עושה:** הפניה לשימוש ב-condition-based waiting (polling) במקום sleep.
- **משויך ל:** `systematic-debugging/SKILL.md`
- **קבצים קשורים:** `systematic-debugging/SKILL.md`

### `.claude/skills/systematic-debugging/defense-in-depth.md`
- **מה הוא עושה:** הפניה לתבנית defense-in-depth validation.
- **משויך ל:** `systematic-debugging/SKILL.md`
- **קבצים קשורים:** `systematic-debugging/SKILL.md`

### `.claude/skills/systematic-debugging/root-cause-tracing.md`
- **מה הוא עושה:** הפניה לתהליך root cause tracing — מציאת שורש הבעיה לפני תיקון.
- **משויך ל:** `systematic-debugging/SKILL.md`
- **קבצים קשורים:** `systematic-debugging/SKILL.md`

### `.claude/skills/systematic-debugging/test-academic.md`
- **מה הוא עושה:** טסט אקדמי/תיאורי לסקיל הדיבוג.
- **משויך ל:** `systematic-debugging/SKILL.md`
- **קבצים קשורים:** `test-pressure-1.md`, `test-pressure-2.md`, `test-pressure-3.md`

### `.claude/skills/systematic-debugging/test-pressure-1/2/3.md`
- **מה הם עושים:** טסטים של לחץ (adversarial) לסקיל הדיבוג — בודקים שהסקיל עומד בפני rationalization.
- **משויך ל:** `systematic-debugging/SKILL.md`
- **קבצים קשורים:** `test-academic.md`, `writing-skills/testing-skills-with-subagents.md`

### `.claude/skills/test-driven-development/SKILL.md`
- **מה הוא עושה:** סקיל TDD — לפני כתיבת קוד מימוש, כותב טסטים קודם.
- **משויך ל:** כל פיצ'ר חדש או תיקון
- **קבצים קשורים:** `testing-anti-patterns.md`, `verification-before-completion/SKILL.md`

### `.claude/skills/test-driven-development/testing-anti-patterns.md`
- **מה הוא עושה:** רשימת anti-patterns לכתיבת טסטים — מה לא לעשות (mocks, test-only methods וכד').
- **משויך ל:** `test-driven-development/SKILL.md`
- **קבצים קשורים:** `test-driven-development/SKILL.md`

### `.claude/skills/using-superpowers/SKILL.md`
- **מה הוא עושה:** סקיל bootstrap — נטען בתחילת כל שיחה ומגדיר כיצד למצוא ולהשתמש בשאר הסקילים.
- **משויך ל:** כל הסקילים
- **קבצים קשורים:** כל קבצי `SKILL.md` בפרויקט

### `.claude/skills/using-superpowers/references/codex-tools.md`
- **מה הוא עושה:** הפניה לכלים הזמינים ב-Codex CLI.
- **משויך ל:** `using-superpowers/SKILL.md`
- **קבצים קשורים:** `copilot-tools.md`, `gemini-tools.md`

### `.claude/skills/using-superpowers/references/copilot-tools.md`
- **מה הוא עושה:** הפניה לכלים הזמינים ב-GitHub Copilot CLI.
- **משויך ל:** `using-superpowers/SKILL.md`
- **קבצים קשורים:** `codex-tools.md`, `gemini-tools.md`

### `.claude/skills/using-superpowers/references/gemini-tools.md`
- **מה הוא עושה:** הפניה לכלים הזמינים ב-Gemini CLI.
- **משויך ל:** `using-superpowers/SKILL.md`
- **קבצים קשורים:** `codex-tools.md`, `copilot-tools.md`

### `.claude/skills/verification-before-completion/SKILL.md`
- **מה הוא עושה:** סקיל לפני סיום משימה — מריץ פקודות verification ומאשר output לפני כל commit/PR.
- **משויך ל:** שלב סיום כל משימה
- **קבצים קשורים:** `finishing-a-development-branch/SKILL.md`, `requesting-code-review/SKILL.md`

### `.claude/skills/writing-plans/SKILL.md`
- **מה הוא עושה:** סקיל לכתיבת תכנית מימוש — לפני נגיעה בקוד, כשיש spec או דרישות.
- **משויך ל:** `executing-plans/SKILL.md`
- **קבצים קשורים:** `plan-document-reviewer-prompt.md`, `executing-plans/SKILL.md`

### `.claude/skills/writing-plans/plan-document-reviewer-prompt.md`
- **מה הוא עושה:** תבנית prompt לשליחת sub-agent שסוקר תכנית מימוש.
- **משויך ל:** `writing-plans/SKILL.md`
- **קבצים קשורים:** `writing-plans/SKILL.md`

### `.claude/skills/writing-skills/SKILL.md`
- **מה הוא עושה:** סקיל ליצירה ועריכה של סקילים חדשים — כולל ולידציה לפני deployment.
- **משויך ל:** תהליך יצירת סקילים
- **קבצים קשורים:** `anthropic-best-practices.md`, `testing-skills-with-subagents.md`, `persuasion-principles.md`

### `.claude/skills/writing-skills/anthropic-best-practices.md`
- **מה הוא עושה:** Best practices של Anthropic לכתיבת סקילים אפקטיביים.
- **משויך ל:** `writing-skills/SKILL.md`
- **קבצים קשורים:** `writing-skills/SKILL.md`

### `.claude/skills/writing-skills/persuasion-principles.md`
- **מה הוא עושה:** עקרונות persuasion לעיצוב סקילים — איך לגרום ל-agent להפעיל אותם נכון.
- **משויך ל:** `writing-skills/SKILL.md`
- **קבצים קשורים:** `writing-skills/SKILL.md`

### `.claude/skills/writing-skills/testing-skills-with-subagents.md`
- **מה הוא עושה:** מדריך לבדיקת סקילים עם subagents — לפני deployment, ולחץ adversarial.
- **משויך ל:** `writing-skills/SKILL.md`
- **קבצים קשורים:** `systematic-debugging/test-pressure-1/2/3.md`

### `.claude/skills/writing-skills/examples/CLAUDE_MD_TESTING.md`
- **מה הוא עושה:** דוגמה ל-CLAUDE.md לצורכי בדיקת סקילים.
- **משויך ל:** `writing-skills/SKILL.md`
- **קבצים קשורים:** `writing-skills/SKILL.md`, `CLAUDE.md`

---

## Skills — Obsidian Plugin

### `.claude/skills/obsidian-vault-workflow/SKILL.md`
- **מה הוא עושה:** פרוטוקול חובה לניהול vault של Obsidian — קריאה לפני כל משימה, כתיבה בסיום. Long-term memory של הפרויקט.
- **משויך ל:** כל סשן עבודה
- **קבצים קשורים:** `vault/Meeting Notes/_index.md`, כל קבצי ה-vault

### `.claude/skills/obsidian-markdown/SKILL.md`
- **מה הוא עושה:** סקיל ליצירה ועריכה של Obsidian Flavored Markdown — wikilinks, callouts, frontmatter וכד'.
- **משויך ל:** כל קובץ `.md` ב-vault
- **קבצים קשורים:** `obsidian-vault-workflow/SKILL.md`, `obsidian-bases/SKILL.md`

### `.claude/skills/obsidian-bases/SKILL.md`
- **מה הוא עושה:** סקיל ליצירה ועריכה של Obsidian Bases (`.base` files) — views, filters, formulas.
- **משויך ל:** database-like views ב-Obsidian
- **קבצים קשורים:** `obsidian-markdown/SKILL.md`

---

## Vault (נוצר בסשן זה)

### `vault/Meeting Notes/_index.md` — אינדקס נושאי סשנים
### `vault/Meeting Notes/project-setup.md` — לוג הקמת הפרויקט
### `vault/Meeting Notes/project-documentation-scan.md` — לוג הסריקה הזו
### `vault/Content Briefs/_index.md` — אינדקס briefs תוכן
### `vault/Brand Guidelines/_index.md` — אינדקס קווים מנחים מיתוג
### `vault/Publishing Log/_index.md` — אינדקס לוג פרסום
