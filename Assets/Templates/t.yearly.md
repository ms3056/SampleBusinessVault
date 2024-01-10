---
created: <% tp.date.now("YYYY-MM-DD") %>
summary: 
tags: []
---

# Journal
---




# Documents
---

```dataview
TABLE summary AS Summary
	FROM "Journal/Quarterly" 
	WHERE year = "<% moment(tp.date).format('gggg') %>" OR contains(year, link("<% moment(tp.date).format('gggg') %>"))
	SORT file.name ASC
```

