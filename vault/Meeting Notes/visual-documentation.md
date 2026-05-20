# Visual Documentation (Obsidian Canvas)

## Overview
תיעוד ויזואלי של הפרויקט באמצעות קבצי Obsidian Canvas תחת `docs/`. ארבעה קנבסים: `Home.canvas` (ניווט מרכזי), `Architecture.canvas` (זרימת נתונים + רכיבים + APIs), `Roadmap.canvas` (סטטוס במבנה Done/In Progress/Next/Later), ו-`Filemap.canvas` (מבנה קבצים לפי תפקיד עם קישורים לתיעוד בוואלט). הקנבסים נטענים ישירות בתוך Obsidian משום שהפרויקט עצמו הוא ה-vault (`.obsidian/` ב-root).

## Open Questions
- האם להעביר את ה-Canvas Files לתוך `vault/` (כדי לקבץ את כל התיעוד באותה תיקייה) או להשאיר ב-`docs/` כפי שביקש המשתמש
- האם הצורה הנוכחית של file-link nodes ל-`vault/Meeting Notes/*-agent.md` ב-Filemap תיפתח כצפוי באובסידיאן, או תיראה ריקה אם הקובץ עוד לא נראה ב-explorer
- האם הקישורים מ-Home אל יתר הקנבסים פותחים נכון במצב Canvas של אובסידיאן (לא אומת)

## Session Log

### 2026-05-20 — יצירת 4 קבצי Obsidian Canvas לתיעוד ויזואלי [shipped]
- **What was done:** נוצרה תיקייה `docs/` עם 4 קבצי `.canvas`: `Home.canvas` (10 nodes / 9 edges) — מרכז ניווט עם קישורים ל-Architecture/Roadmap/Filemap + טקסט-נודים עבור Agents ו-Configuration. `Architecture.canvas` (18 nodes / 21 edges) — User → CEO → 4 sub-agents → אחסון → APIs חיצוניים + תיבת QA Loop ותיבת Language Rule. `Roadmap.canvas` (6 nodes / 4 edges) — 4 עמודות סטטוס + תיבת Color Legend + Known Risks. `Filemap.canvas` (17 nodes / 11 edges) — קבוצות לפי Configuration, Agent Contracts, Skills, Pipeline, Workspaces, Vault, Visual Docs; file-link nodes לכל `vault/Meeting Notes/*.md`.
- **Decisions:** הקנבסים נשמרו ב-`docs/` (לפי בקשת המשתמש "project root or docs folder") ולא ב-`vault/`. ה-`.claude/` נציג ע"י text nodes (לא file-link) כי אובסידיאן מסתיר dot-directories ב-explorer ולכן file-links עליהם נראים שבורים. כל הוואלט-דוקס מוצגים כ-file-link nodes כדי לאפשר תצוגה מקדימה מובנית. כל JSON עבר אימות (`ConvertFrom-Json`) — אין שגיאות תחביר.
- **Notes / Caveats:** לא אומת ידנית שהקישורים בין-קנבסים (Home → Architecture וכו') באמת פותחים באובסידיאן; כך זה תועד ב-Open Questions. הצבעים בשימוש: 1=red, 2=orange, 3=yellow, 4=green, 5=cyan, 6=purple — תואם לקונבנציה של Obsidian Canvas. Roadmap מתעד את ה-pruning candidates שדוברו בסשן (סקילי TDD/debugging/worktrees ממורשת Superpowers) וכן את ההצעות AGT-05/06/07 שלא הוטמעו.
- **Related:** [[project-overview]], [[ceo-agent]], [[chen-agent]], [[yael-agent]], [[yuval-agent]], [[guy-agent]], [[claude-configuration]], [[skills-roster]]
