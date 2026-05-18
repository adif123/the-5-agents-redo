# Obsidian Markdown

## מה הסקיל עושה
יוצר ועורך Obsidian Flavored Markdown — wikilinks, embeds, callouts, frontmatter ועוד.

## מתי מפעילים
כשעובדים עם קבצי `.md` ב-Obsidian, או כשהמשתמש מזכיר wikilinks, callouts, frontmatter, tags, embeds.

## syntax מרכזי

**Wikilinks (קישורים פנימיים):**
```
[[Note Name]]
[[Note Name|Display Text]]
[[Note Name#Heading]]
```
השתמש ב-wikilinks לקישורים פנימיים בvault — Obsidian עוקב אחרי שינויי שם אוטומטית.

**Callouts:**
```
> [!info]
> תוכן הcallout
```

**Frontmatter:**
```yaml
---
title: כותרת
tags: [tag1, tag2]
aliases: [שם חלופי]
---
```

**Embeds:**
```
![[Note Name]]
![[image.png]]
```

## כלל עיצוב
- קישורים לvault: `[[wikilink]]`
- קישורים חיצוניים: `[text](url)`

## סקילים קשורים
- [[obsidian-vault-workflow]] — כיצד לכתוב קבצי vault
- [[obsidian-bases]] — .base files ב-Obsidian
