<%*
const selection = tp.file.selection()
const workbench = tp.file.find_tfile("Workbench") // Name of your Workbench file
if (selection) {
    // New line, bullet point with today's date prepended
    const line = "\n- " + tp.date.now("YYYY-MM-DD ") + selection.split("\n").join(" ")
    await app.vault.append(workbench, line)
}
tR += selection
%>