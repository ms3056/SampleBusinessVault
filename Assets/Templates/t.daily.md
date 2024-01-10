---
created: <% tp.date.now("YYYY-MM-DD") %>
week: '[[<% moment(tp.date).format("gggg-[W]ww") %>]]'
quarter: '[[<% moment(tp.date).format("gggg-[Q]Q") %>]]'
year: '[[<% moment(tp.date).format("gggg") %>]]'
summary:
---

# Meetings
---


# Journal
---



# Inbox
---
``` dataview
LIST
FROM "Inbox" 
SORT created ASC
 ```
 