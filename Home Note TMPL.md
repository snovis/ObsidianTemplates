<%*
/**
How to use Home Note TMPL
You will need Templeter installed for this template to work.
There is javascript code in this template that does a few things.  The main
cool thing this template does is try to build a better alias for linking to this file.
How do use it.
1. Make a new file with a name like `_Home something Note`.  The initial underscore, or first character is to force Obsidian to list the file _first_ in the folder list at the top.
2. Then run the command: Run the command `Templater: Open Insert Template Modal` and pick this template.  This command will then use the file name to create a better alias, and it will use the name in other parts of the file.
3. Replace the `sql` tag in the code block with `dataview` to cause the file list to work.

**Note**: How the end of this template runs up against the first `-` of the three hyphens that start front matter.  It has to be like this or the frontmatter won't work.

**/
let basename = tp.file.title.slice(1);
let wordToReplace = "Home";
let replacementWord = "";

let modifiedString = basename.replace(new RegExp("\\b" + wordToReplace + "\\b", "gi"), replacementWord).trim() + " Index";

%>---
Aliases: [<%modifiedString%>]
Author: Scott Novis
Created: <% tp.file.creation_date("YYYY-MM-DD") %>
Updated: 
Tags: [HomeNote]
Comments: Discoverable comment
---
# <%tp.file.title.slice(1)%>

## Overview

## Plans

## Branches
- 

## Journal
- 

## Notes In This Folder


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
- [[<% tp.date.now("YYYY-MM-DD") %>]]