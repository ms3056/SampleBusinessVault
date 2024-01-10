---
created: <% tp.date.now("YYYY-MM-DD") %>
summary: 
tags: []
year: '[[<% moment(tp.date).format("gggg") %>]]'
---


# Journal
---




# Weeks
---

```dataview
TABLE summary AS Summary
	FROM "Journal/Weekly" 
	WHERE quarter = "<% moment(tp.date).format('gggg-[Q]Q') %>" OR contains(quarter, link("<% moment(tp.date).format('gggg-[Q]Q') %>"))
	SORT file.name ASC
```

 