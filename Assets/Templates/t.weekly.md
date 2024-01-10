---
created: <% tp.date.now("YYYY-MM-DD") %>
summary: 
tags: []
quarter: '[[<% moment(tp.date).format("gggg-[Q]Q") %>]]'
---

# Journal
---




# Days
---
```dataview
TABLE without ID
	rows.file.link as File, rows.summary as Summary, Day
	FROM "Journal/Daily" 
	WHERE week = "<% moment(tp.date).format('gggg-[W]ww') %>" OR contains(week, link("<% moment(tp.date).format('gggg-[W]ww') %>"))
	GROUP BY dateformat(file.day, "EEE") AS Day
	SORT rows.file.link ASC
```

