<%*
const files = this.app.vault.getMarkdownFiles()
const file = await tp.system.suggester((files) => files.basename, files)
tR += "[[" + file.basename + "]]"
%>