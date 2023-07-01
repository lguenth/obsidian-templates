# Obsidian Templates

This is a collection of [Obsidian](https://obsidian.md/) templates that I use or have used in the past. Most of them require Templater (and its "Trigger on file creation" feature) but I'll list all plugin dependencies in the [overview below](#overview). You might also need to adjust the folder paths and file names used in the Templater scripts.

## Download

You can download all of the templates by cloning the repository:
```
git clone https://github.com/lguenth/obsidian-templates.git
```

You can also download them individually by clicking on a file in the directory listing above and then using the **Download raw file** button that appears in the top right. Place the files in your vault to start using them.

## Overview

- [book.md](book.md)
  - Add a book to your vault
  - Plugins: Templater, Book Search
- [callouts.md](callouts.md)
  - Choose one of the default callouts to insert at your cursor
  - Plugins: Templater
- [include.md](include.md)
  - Insert the content of a note at your cursor
  - Plugins: Templater
- [lecture.md](lecture.md)
  - Create a lecture (session) note
  - Plugins: Templater
- [meeting.md](meeting.md)
  - Create a meeting note for today/yesterday/tomorrow, select a project from a folder
  - Plugins: Templater
- [movie.md](movie.md)
  - Similar to the book template, add a movie (or TV show) to your vault
  - Plugins: Templater, QuickAdd (plus this script and the setup for it: <https://quickadd.obsidian.guide/docs/Examples/Macro_MovieAndSeriesScript>)
- [open-daily.md](open-daily.md)
  - Open today's daily note (extremely basic, no error handling)
  - Plugins: Templater
- [wikilink.md](wikilink.md)
  - Insert a wikilink to a note
  - Plugins: Templater
- [workbench.md](workbench.md)
  - Adds the current selection to a "workbench" note as a bullet point with today's date
  - Plugins: Templater, Workbench (optional)
- [youtube.md](youtube.md)
  - Gets metadata from a YouTube video and embeds it, works by copying the video URL to the clipboard & then running the template
  - Plugins: Templater
- [zettel.md](zettel.md)
  - Basic Zettelkasten template, asks for the type of the Zettel (I differentiate claims from concepts and questions)
  - Plugins: Templater
- [zotero.md](zotero.md)
  - Create a literature note from a Zotero item, pulling some metadata and all your PDF annotations
  - The callouts are styled according to their highlight colour by using this CSS snippet: [litnote-colors.css](css/litnote-colors.css)
    - Place the file in the `.obsidian/snippets` folder at the base of your vault, then enable through `Settings > Appearance > CSS snippets`.
  - Plugins: Zotero Integration
