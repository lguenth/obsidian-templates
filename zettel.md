<% "---" %>
lang: # de, en
tags:
  - 🗃<% await tp.system.suggester(["Concept", "Claim", "Question"], ["/💠", "/🌱", "/❓"])%>
title: "<% tp.file.title %>"
date: <% tp.file.creation_date("YYYY-MM-DD") %>
lastmod: <% tp.file.last_modified_date("YYYY-MM-DD") %>
<% "---" %>

<% tp.file.cursor(0) %>

- Keywords:: 
- Quelle: 
- Siehe: 