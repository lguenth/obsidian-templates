<%"---"%>
tags: 📥/📹
created: <% tp.file.creation_date("YYYY-MM-DD") %>
modified: <% tp.file.last_modified_date("YYYY-MM-DD") %>
<%"---"%>
<%*
const url = await tp.system.clipboard()
const response = await fetch(`https://youtube.com/oembed?url=${url}&format=json`)
const data = await response.json()
console.log(data)

// Create a safe title... there's probably a better way to do this
const title = data.title.replaceAll("", "").replaceAll('"', '').replaceAll("\\", "").replaceAll("/", "").replaceAll("<", "").replaceAll(">", "").replaceAll(":", "").replaceAll("|", "").replaceAll("?", "")
const author = data.author_name
const author_url = data.author_url
const html = data.html

// Change target path to whatever, has to exist (I think; read the Templater docs)
const newPath = "40 Media/" + title
await tp.file.move(newPath)
const regex = /v=(.*)/gm
const m = regex.exec(url)
-%>

> [!meta]+ Metadaten
> Source:: [<% title %>](<% url %>)
> Channel: [<% author %>](<% author_url %>)
> Published: 
> Watched: <% tp.date.now() %>

<% tp.file.cursor(0) %>

---
<iframe src="https://www.youtube-nocookie.com/embed/<% m[1] %>?vq=hd1080&modestbranding=1&rel=0&iv_load_policy=3" width="569" height="317" frameborder="0" style="margin: 0 auto; display: block;"></iframe>