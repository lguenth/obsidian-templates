<% "---" %>
tags: 📥/📚
type: # fiction or nonfiction
pages: {{totalPage}}
fileclass: book
title: "{{title}}"
created: <% tp.file.creation_date("YYYY-MM-DD") %>
modified: <% tp.file.last_modified_date("YYYY-MM-DD") %>
cover: {{coverUrl}}
<% "---" %>

![cover|150]({{coverUrl}})

> [!meta]+ Metadaten
> - Author:: {{authors}}
> - Year:: {{publishDate}}
> - Status:: 
> - Read:: 