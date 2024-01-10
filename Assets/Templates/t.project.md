---
created: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
aliases: []
tags: []
topic:
status:
project: 
start:
finish:
---
<%* 
let title = tp.file.title 
if (title.startsWith("Untitled")) {
 title = await tp.system.prompt("Project Name"); 
 } 
 await tp.file.rename(title) 
 -%>

# Overview



# Meetings

```dataview
TABLE without ID
rows.file.link as "Files", rows.topic as "Topic", Date
FROM "Journal/Notes" 
WHERE contains(project, link("<% title %>")) OR contains(file.outlinks, link("<% title %>")) 
SORT dateformat(file.day, "yyyy-MM-dd") ASC
GROUP BY dateformat(file.day, "yyyy-MM-dd") AS Date
```
