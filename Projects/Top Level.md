---
created: "[[2024-01-06]]"
aliases: 
tags: 
topic: 
status: 
project: []
start: 
finish:
---
# Creation
---
- I manually created this top level file

# Usage
---
-  Quick look at the active projects - these are "objects" - well - "files" that are in the Projects directory and of which don't have an empty `project:` property value. When the project is finished you could move the file to another directory or just remove the property value. 


# Overview
```dataview
TABLE without ID
rows.file.link as "Files", rows.topic as "Topic", dateformat(rows.start, "DD") as "Start", dateformat(rows.finish, "DD") as "Finish"
FROM "Projects" 
WHERE project AND project != ""
SORT dateformat(start, "yyyy-MM-dd") ASC
GROUP BY dateformat(start, "yyyy-MM") AS Date
```



