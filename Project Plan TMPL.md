<%*
/**
Project Plan TMPL: How to use
You will want to delete everything between these comments.  The three hyphes `-` should
be the very first thing in your file, line 0, starting at character 0.

How to use this file.
1. Make a new note.
2. Give the note a name starting with an underscore, like _Project - Make a Template.  You use the underscore so that this file ALWAYS sorts first in the folder view.  You could also use a 0, or underscore, anything that sorts BEFORE the letter `A` or `a`.
3. Run the command `Templater: Open Insert Template Modal` and pick this template.
4. This template will remove the first character of the file name, build out the frontmatter, and then put in place holders for project management.
5. To use the file list, replace the `sql` in the code block with `dataview`.  I use the tag `sql` so the code is easy to read and understand before you let it run.
6. Then fill in all the form fields and you are good to go.
**/
%>
---
Aliases: [<% tp.file.title.slice(1) %>]
Author: Scott Novis
Created: <% tp.file.creation_date("YYYY-MM-DD") %>
Updated: 
Tags: [ProjectPlan]
Comments: 
---

# <%tp.file.title.slice(1)%>

## Overview
_Quick overview, purpose, standards._  

## Goal
_link to goal_

## Done Looks Like
_how do I know I'm done?_

## Branches

## Resources


## Plans
- [ ] What is next?

## Journal
- 


## Files
```sql
TABLE WITHOUT ID 
	link(file.name,file.aliases[0]) as "Note",
	Comments as "Description"
WHERE 
	contains(file.path, this.file.folder) 
	AND file.name != this.file.name
SORT file.aliases[0] ASC
```


## Connections
- [[<% tp.date.now("YYYY-MM-DD") %>]] - Daily Note for day this file was created.