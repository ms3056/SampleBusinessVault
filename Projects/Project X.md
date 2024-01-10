---
created: "[[2024-01-06]]"
aliases: 
tags: 
topic: A project to design and bring to market a widget
status: 
project:
  - "[[Project X]]"
start: 2024-01-01
finish: 2024-09-30
---
# Creation
---
- Right click on the Projects folder and Create Note - the Templater Script will prompt you for a name and then setup the query automatically

# Usage
---
- I provide an overview of what the project is about and the query shows a list of meetings for this project along with the topic of each meeting.
- This is a great place to get a summary of a project. 


# Overview



# Meetings

```dataview
TABLE without ID
rows.file.link as "Files", rows.topic as "Topic", Date
FROM "Journal/Notes" 
WHERE contains(project, link("Project X"))
SORT dateformat(file.day, "yyyy-MM-dd") ASC
GROUP BY dateformat(file.day, "yyyy-MM-dd") AS Date
```
