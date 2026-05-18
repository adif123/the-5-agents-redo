# Claude Configuration

## Overview
תיקיית `.claude/` מכילה את כל ההגדרות הספציפיות לפרויקט עבור Claude Code. המבנה: `agents/` להגדרות sub-agents, `skills/` לסקילים הניתנים להפעלה כ-slash commands, `commands/` לפקודות workflow מותאמות. בנוסף קיים `settings.json` ברמת project המפעיל את ה-plugin `skill-creator@claude-plugins-official`. `settings.local.json` קיים לשימוש מקומי בלבד ולא מועלה ל-git.

## Open Questions
- `commands/` ריק כרגע — אילו פקודות מותאמות יוגדרו בעתיד?
- `agents/` ריק כרגע — מתי ייוצרו הגדרות sub-agents ראשונות?
- מה תוכן `settings.local.json` שאינו מועלה ל-git?

## Session Log

### 2026-05-19 — תיעוד מבנה .claude/ ראשוני [shipped]
- **What was done:** נסרק מבנה `.claude/` המלא. תועד settings.json עם plugin skill-creator. זוהה ש-agents ו-commands ריקים.
- **Decisions:** הותקן `skill-creator@claude-plugins-official` ב-scope project — נדחף ל-main. זהו ה-plugin היחיד הפעיל כרגע.
- **Notes / Caveats:** `settings.local.json` קיים אך תוכנו לא נסרק (מקומי בלבד).
- **Related:** [[project-overview]], [[skills-roster]]
