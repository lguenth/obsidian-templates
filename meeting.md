<%"---"%>
tags: 💻/📅
created: <% tp.file.creation_date("YYYY-MM-DD") %>
modified: <% tp.file.last_modified_date("YYYY-MM-DD") %>
<%"---"%>
<%*
const days = ["today", "yesterday", "tomorrow"]
const dateValue = await tp.system.suggester(days, days, true)
const newDate = app.plugins.plugins['nldates-obsidian'].parseDate(dateValue).moment.format("YYYY-MM-DD");
const tag = "#💻/🎯"
const files = this.app.vault.getMarkdownFiles()  
    .filter(file => file.path.match("30 Job"))
    .filter(file => {
      const tags = tp.obsidian.getAllTags(app.metadataCache.getFileCache(file));
      return tags.includes(tag);})
    .sort((a, b) => a.basename.localeCompare(b.basename));
const project = (await tp.system.suggester((file) => file.basename, files)).basename;
const newPath = "30 Job/31 Meetings/" + newDate + " " + project;
await tp.file.move(newPath);
-%>

↑ [[<% project %>]]

### Prep
- <% tp.file.cursor(0) %>

### Notes
- 

### Follow-up
- 