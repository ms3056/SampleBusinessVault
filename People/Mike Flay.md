---
created: "[[2024-01-06]]"
aliases:
  - Mike
tags: 
manager:
---
# Creation
---
- Right click on the People folder, Create Note, then enter the person's name. The Templater Script will create the note, name it, and setup the query for you automatically. 
- The Direct Reports query below is added manually for managers. 

# Usage
---
- I use this to see the activity of a person to prepare for a review with them


# Direct Reports
---
```dataview
TABLE without ID
file.link as "Files", tags as "Tags"
FROM "People"
WHERE contains(manager, link("Mike Flay"))
```

- Add this query (above) for managers to list their direct reports. 
- Notice the query references the full name of the manager - even though we reference the alias for each person

# Notes
---
```dataview
TABLE without ID
rows.file.link as "Files", rows.topic as "Topic", Date
FROM "Journal"
WHERE contains(people, link("Mike Flay")) OR contains(file.outlinks, link("Mike Flay"))
SORT dateformat(file.day, "yyyy-MM-dd") ASC
GROUP BY dateformat(file.day, "yyyy-MM") AS Date
```
