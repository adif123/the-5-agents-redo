# CEO Agent

## Overview
ה-CEO Agent הוא ה-root orchestrator של המערכת multi-agent. ה-contract שלו חי ב-`.claude/agents/ceo/agent.md` (folder form), ונטען ע"י `CLAUDE.md` בכל סשן. הסוכן מבצע parse → classify → plan → execute → synthesize → report, ומפעיל sub-agents ברצף. נכון ל-2026-05-19: AGT-01 יעל (שכתוב), AGT-02 יובל (תמונות), ו-AGT-03 חן (מחקר רשת) רשומים ופעילים עם routing rules מוגדרות, כולל composite flows. AGT-04 עדיין TBD.

## Open Questions
- AGT-04: שם ותחום טרם הוגדרו
- ה-`Domain` בסעיף Identity של ה-contract: עדיין `[TO BE DEFINED]`
- מנגנון memory persistence בין סשנים: PRD סעיף 7 פתוח

## Session Log

### 2026-05-19 — CEO Agent contract shipped [shipped]
- **What was done:** נוצר `agents/ceo/agent.md` עם 10 הסעיפים החובה לפי PRD סעיף 5.2 (Identity, Mission, Capabilities, Sub-Agents, Routing Rules, Execution Protocol, Language Rules, Constraints, Output Format, Error Handling). נוצר `agents/ceo/_index.md`. עודכן `CLAUDE.md` עם בלוק `## CEO Agent Protocol` שמחייב טעינת ה-contract בכל סשן.
- **Decisions:** ה-CEO הוא ה-main Claude session ולא sub-agent — זה הדפוס הסטנדרטי ב-orchestration (Anthropic, AutoGen, CrewAI, LangGraph supervisor). ה-contract חי כקובץ נפרד ב-`agents/ceo/agent.md` ולא inline ב-CLAUDE.md, כדי לאפשר עדכון עצמאי כש-sub-agents נוספים. 4 שורות הרישום נשארות `[TBD]` בכוונה — לא להמציא שמות.
- **Notes / Caveats:** ה-contract באנגלית (terminology אחיד); ה-Language Rules עצמן מחייבות תשובות בעברית מלאה כשה-input בעברית — תואם ל-`feedback_rtl_responses.md` ב-memory. `.claude/agents/` נשאר ריק כרגע (רק `.gitkeep`).
- **Related:** [[project-overview]], [[claude-configuration]], [[skills-roster]]

### 2026-05-19 — Contract הועבר ל-`.claude/agents/ceo/` [shipped]
- **What was done:** הועבר ה-contract מ-`agents/ceo/agent.md` (repo root) אל `.claude/agents/ceo/agent.md` (folder form תחת `.claude/`). תיקיית `agents/` ב-repo root נמחקה. עודכנה ההפניה ב-CLAUDE.md ל-path החדש. עודכן ה-internal constraint ב-contract שמדבר על טעינת sub-agent files.
- **Decisions:** המשתמש העלה שמיותר להחזיק שתי תיקיות `agents/` במקביל — הפרויקט מתעד את `.claude/agents/` כבית של agent definitions. נבחרה **folder form** (`.claude/agents/ceo/agent.md`) ולא single-file (`.claude/agents/ceo.md`) כדי למנוע התנגשות ארכיטקטונית: single-file היה גורם ל-Claude Code לרשום את ה-CEO כ-Task sub-agent אוטומטית, בסתירה לכך שה-CEO הוא ה-main session.
- **Notes / Caveats:** סוכני המומחה העתידיים (AGT-01..AGT-04) **חייבים** להיווצר כ-single-file ב-`.claude/agents/<name>.md` עם YAML frontmatter כדי להיות Task-invokable. folder form = inert docs בלבד.
- **Related:** [[project-overview]], [[claude-configuration]]

### 2026-05-19 — ביקורת תאימות עץ הקבצים [debug]
- **What was done:** המשתמש ביקש ביקורת על עץ הקבצים מול הכוונה "CEO הוא main, לא sub-agent". נסקרו `.claude/agents/` (מכיל `.gitkeep` + תת-תיקייה `ceo/`), `.claude/agents/ceo/agent.md`, `_index.md`, ו-`CLAUDE.md`.
- **Decisions:** עץ הקבצים **תואם** את הכוונה — folder form (`ceo/agent.md`) מסתיר את ה-contract מ-auto-discovery של Claude Code (שסורק רק `.md` ישיר ב-`.claude/agents/`), אז ה-CEO לא נרשם כ-Task sub-agent. הוצעו 2 שיפורי תיעוד ל-CLAUDE.md (לא יושמו עדיין, ממתין לאישור משתמש): (1) עדכון שורה 24 כך שהתיאור של `.claude/agents/` יציין שה-CEO contract יושב שם ב-folder form; (2) הוספת משפט הסבר בבלוק `## CEO Agent Protocol` למה folder form ולא single-file.
- **Notes / Caveats:** לא בוצעו שינויי קבצים פרט לעדכון רשומה זו ב-vault. שתי ההצעות מתועדות גם ב-Open Questions למעקב.
- **Related:** [[project-overview]], [[claude-configuration]]

### 2026-05-19 — AGT-01 יעל + AGT-02 יובל רשומים, routing rules מוגדרות [shipped]
- **What was done:** עודכן `ceo/agent.md`: AGT-01 יעל ו-AGT-02 יובל נרשמו בטבלת Sub-Agents. הוגדרו routing rules: יעל ← בקשות תוכן; יובל ← בקשות תמונה; יעל→יובל→CEO ← מאמר עם תמונות.
- **Decisions:** פרוטוקול ה-handoff בין יעל ליובל עובר דרך CEO (לא direct): יעל מחזירה placeholders, CEO מפעיל יובל, CEO מבצע שילוב. זה שומר על CEO כ-single point of control.
- **Notes / Caveats:** AGT-03, AGT-04 נשארים TBD. CLAUDE.md עודכן בנפרד עם אותו מידע (redundancy מכוונת — CLAUDE.md הוא human-readable, agent.md הוא machine-contract).
- **Related:** [[project-overview]], [[yael-agent]], [[yuval-agent]]

### 2026-05-19 — AGT-03 חן רשומה + composite routing rules [shipped]
- **What was done:** עודכן `ceo/agent.md`: AGT-03 חן נרשמה בטבלת Sub-Agents. נוסף routing rule ל-חן (keywords: חפש/מצא/מחקר/research/find/article about). נוסף בלוק "Composite flows" שמגדיר את ה-orchestration לבקשות מורכבות: find+rewrite, find+rewrite+images. הוספה הערה מפורשת שה-image trigger נקבע מהבקשה המקורית של המשתמש — לא מהפלט של יעל (כי יעל הפסיקה להחזיר IMAGE_NEEDED placeholders אחרי ה-pivot).
- **Decisions:** CEO הוא single point of orchestration — אף sub-agent לא קורא ישירות לאחר. ה-tri-agent pipeline (חן → יעל → יובל) מותזם בקריאות נפרדות. composite flows מוסברים בפירוט ב-routing rules כדי שה-CEO ידע מה לעשות בלי לשאול את המשתמש בכל פעם.
- **Notes / Caveats:** העברה ל-3 סוכנים פעילים מחייבת זהירות בזיהוי intent — CEO חייב לפרק את הבקשה המקורית למרכיבי "find", "rewrite", "images" לפני ההפעלה.
- **Related:** [[project-overview]], [[chen-agent]], [[yael-agent]], [[yuval-agent]]
