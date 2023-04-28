<%*
// Choose file in vault to include its content in the current note

const files = this.app.vault.getMarkdownFiles()
const file = await tp.system.suggester((files) => files.basename, files)
tR += await tp.file.include("[[" + file.basename + "]]")
%>