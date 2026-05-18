# Obsidian Bases

## מה הסקיל עושה
יוצר ועורך קבצי `.base` ב-Obsidian — views מסוג table/cards/list/map של רשומות vault.

## מתי מפעילים
כשיוצרים `.base` files, views מסוג database של notes, או כשהמשתמש מזכיר Bases, table views, filters, formulas ב-Obsidian.

## מבנה קובץ base

```yaml
filters:
  and: []   # או or/not
formulas:
  myFormula: "expression"
views:
  - type: table   # או cards/list/map
    order:
      - property1
      - property2
```

## תהליך יצירה
1. יצירת קובץ `.base`
2. הגדרת `filters` — אילו notes נכללים (לפי tag, folder, property, תאריך)
3. הגדרת `formulas` (אופציונלי)
4. הגדרת view עם `order`
5. אימות YAML — בדוק quoting של strings עם תווים מיוחדים
6. פתיחה ב-Obsidian לאישור

## בעיות נפוצות
- strings עם תווים מיוחדים ב-YAML חייבים quotes
- `formula.X` ב-views חייב להיות מוגדר ב-`formulas`

## סקילים קשורים
- [[obsidian-markdown]] — syntax כללי של vault
