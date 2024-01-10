---
created: "[[2024-01-06]]"
aliases:
  - Bob
tags: 
manager: "[[Mike Flay|Mike]]"
---
# Creation
---
- Right click on the People folder, Create Note, then enter the person's name. The Templater Script will create the note, name it, and setup the query for you automatically. 

# Usage
---
- I use this to see the activity of a person to prepare for a review with them


```dataview
TABLE without ID
rows.file.link as "Files", rows.topic as "Topic", Date
FROM "Journal"
WHERE contains(people, link("Bob Smith")) OR contains(file.outlinks, link("Bob Smith")) 
SORT dateformat(file.day, "yyyy-MM-dd") ASC
GROUP BY dateformat(file.day, "yyyy-MM") AS Date
```
