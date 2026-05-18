# Dispatching Parallel Agents

## מה הסקיל עושה
שולח 2 agents או יותר במקביל על בעיות עצמאיות. כל agent מקבל context מדויק ומבודד — ללא היסטוריית הסשן הנוכחי.

## מתי מפעילים
כשיש 2+ כשלים/משימות שאינן תלויות זו בזו ויכולות לרוץ במקביל ללא shared state.

**לא מפעילים כשיש:**
- כשלים קשורים (תיקון אחד עלול לפתור את האחרים)
- תלות בין המשימות
- agents שיגעו באותם קבצים

## תהליך בקצרה
1. זיהוי domains עצמאיים
2. כתיבת prompt ממוקד לכל agent (scope + מטרה + constraints + output format)
3. שיגור במקביל
4. קריאת תוצאות, בדיקת conflicts, הרצת test suite

## סקילים קשורים
- [[subagent-driven-development]] — ביצוע תכנית עם agents רצופים (לא מקביל)
- [[requesting-code-review]] — review לאחר איחוד התיקונים
