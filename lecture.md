<% "---" %>
tags: 🎓/📝
created: <% tp.file.creation_date("YYYY-MM-DD") %>
modified: <% tp.file.last_modified_date("YYYY-MM-DD") %>
<% "---" %>
<%* 
const newDate = await tp.date.now("YYYY-MM-DD");

const files = this.app.vault.getMarkdownFiles()  
    // Filter by folder
    .filter(file => file.path.match("20 Studium/26"))
    .sort((a, b) => a.basename.localeCompare(b.basename));

// Further filter by tag
const filesWithTags = files.filter(file => app.metadataCache.getFileCache(app.vault.getAbstractFileByPath(file.path)).frontmatter?.tags?.includes("🎓/📌"));

const fileNames = filesWithTags.map(file => file.basename);
const filePaths = filesWithTags.map(file => file.path);

const courseFolder = await tp.system.suggester(fileNames, filePaths.map(folder => folder.split("/").slice(0,3).join("/")), true);

const newPath = courseFolder + "/Sessions/" + newDate;
await tp.file.move(newPath);

const courseName = filesWithTags.filter(file => file.path.includes(courseFolder)).map(file => file.basename);

-%>

<%*
// Un-escape wikilinks
let content = "↑ LV:: \[\[" + courseName + "\]\]";
const replaced = content.replace(/\\/g, "");
tR += replaced;
-%>
<% tp.file.cursor(0) %>