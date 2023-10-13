<%*
/**
How to use Make ZUnique Note
This template does something kind of fun.  First, it generates a Zettlekasten number for the file in the format YYYYMMDDHHMM - so as of the time I'm writing this, it would create a number 202310122022.  This number is combined with the file name to create a unique (Zunique) file name.  But those names are not fun to type, so we also want an alias to make the file more readable.  It does that too.
It also does one other cool thing, it will try to find the note that linked (and navigated) to this note and use that to create an explicity backlink in the Prev Page section.

So how do yo use it?
1. Create a link in a document and surround it with double brackets like [[my new file]]
2. Click on that link.
3. Run the command `Templater: Open Insert Template Modal` and pick this template.
4. This template will then run the javascrip to build the new file name (updating all previous links), and if it can, it will make an explicit link to the previous file.

I recommend going back to the previous file and editing the link you created to use a short cut, usually all you have to do is type a vertical bar `|` or pipe symbol at the end of the name of your old file (before the double close brackets) and Obsidian will pop up the new alias for you to select.  It just looks nicer that way.

You will end up with a structured note, a link to the previous note, and a place to begin to save information.  Some features about this template.
1. you can use the comments in the frontmatter - they work with the Home Note, and Project Note templates.
2. You can change the body anyway you like.  For my system, I like having an overview or executive summer, then I can put as much stuff as I want in the Content section.  The Overview makes the note more "discoverable".  
3. I have a Connections section at the end of every ZUnique note file where I might put connections to other related files, websites, resources, whatever. By default it ALWAYS has a link to the Day Note associated with the day the note was created.

**/
let basename = tp.file.title;
let wordToReplace = "Home";
let replacementWord = "";

// how to find the last file?
// [Creating backlinks in Templater - Help - Obsidian Forum](https://forum.obsidian.md/t/creating-backlinks-in-templater/53256)
// the one downside, I don't have the aliases for the last file.
let last_file = "" 
let recent_leaf = this.app.workspace.getMostRecentLeaf(); 
let back_history = recent_leaf.history.backHistory;
let back_link = back_history[back_history.length-1].title;
let nameArr = back_link.split('-');
if (nameArr.length <= 1) 
	short_link = back_link
else
	short_link = nameArr[1].trim();

await tp.file.rename(tp.date.now("YYYYMMDDHHMMmm") + ' - ' + basename);
%>---
Aliases: [<%basename%>]
Author: Scott Novis
Created: <% tp.file.creation_date("YYYY-MM-DD") %>
Updated: 
Tags: [BranchCard]
Comments: Discoverable comment
---
# <% basename %>
***
**Prev Card**: [[<%back_link + "|"+ short_link%>]]
**Next Card**: 
***

## Overview

## Contents


## Connections
- [[<% tp.date.now("YYYY-MM-DD") %>]] 