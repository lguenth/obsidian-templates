<%* 
// Get daily note and open it in a new leaf, fails if note doesn't exist... but I'm lazy

return app.workspace.getLeaf(true, 'vertical').openFile(app.vault.getAbstractFileByPath("50 Periodic/" + moment().format("YYYY") + "/" + moment().format("YYYY-MM-DD") + ".md")) 
%>