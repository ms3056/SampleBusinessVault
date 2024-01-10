---
created: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
aliases: []
tags: []
manager:
---
<%* 
let title = tp.file.title 
if (title.startsWith("Untitled")) {
 title = await tp.system.prompt("Title"); 
 } 
 await tp.file.rename(title) 
 -%>
 
```dataview
TABLE without ID
rows.file.link as "Files", rows.topic as "Topic", Date
FROM "Journal" 
WHERE contains(people, link("<% title %>")) OR contains(file.outlinks, link("<% title %>")) 
SORT dateformat(file.day, "yyyy-MM-dd") ASC
GROUP BY dateformat(file.day, "yyyy-MM") AS Date
```
