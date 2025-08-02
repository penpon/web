# Prompt ID Search & Browser

Fast prompt_id search and file browsing functionality for PermanentNote directory.

```dataviewjs
// Efficient data collection
let pages = dv.pages().where(p => p.file.folder === "Web/content/Zettelkasten/PermanentNote");
if (pages.length === 0) {
    pages = dv.pages().where(p => p.file.path.includes("PermanentNote"));
}

const pagesArray = Array.from(pages);
const filesWithPromptId = pagesArray.filter(p => p.prompt_id);

// Create prompt_id mapping for search
const promptIdMap = new Map();
const stats = { total: pagesArray.length, withPromptId: 0 };

filesWithPromptId.forEach(file => {
    stats.withPromptId++;
    const pid = file.prompt_id;
    if (!promptIdMap.has(pid)) {
        promptIdMap.set(pid, []);
    }
    promptIdMap.get(pid).push(file);
});

// Display search overview
dv.header(2, "📊 Search Overview");
dv.paragraph(`**Total files:** ${stats.total} | **Files with prompt_id:** ${stats.withPromptId}`);

// Quick search for common IDs
dv.header(2, "🔍 Quick Search");
const searchIds = ["E000140", "E000141", "E000142", "E000143", "E000144"];
const quickResults = searchIds.map(id => {
    const count = promptIdMap.get(id)?.length || 0;
    const style = count > 0 ? "background:#d4edda; color:#155724;" : "background:#f8d7da; color:#721c24;";
    return `<code style="${style} padding:2px 4px;">${id}</code>${count > 0 ? ` (${count})` : ''}`;
}).join(" | ");

dv.paragraph("**Common IDs:** " + quickResults);

// Enhanced search functionality
dv.header(2, "🔎 Advanced Search");

// Search by ID pattern
const patternSearch = {
    "E0001xx": Array.from(promptIdMap.keys()).filter(pid => pid.startsWith("E0001")).sort(),
    "E0002xx": Array.from(promptIdMap.keys()).filter(pid => pid.startsWith("E0002")).sort(),
    "Latest": Array.from(promptIdMap.keys()).sort().slice(-10)
};

Object.entries(patternSearch).forEach(([pattern, ids]) => {
    if (ids.length > 0) {
        const idLinks = ids.map(id => {
            const files = promptIdMap.get(id);
            const fileLinks = files.map(f => f.file.link).join(", ");
            return `<code>${id}</code>: ${fileLinks}`;
        }).join("<br>");
        dv.paragraph(`**${pattern}:** <br>${idLinks}`);
    }
});

// Complete file listing (expandable)
const showAllFiles = true; // Set to false to hide large table

if (showAllFiles && filesWithPromptId.length > 0) {
    dv.header(2, "📋 All Files with prompt_id");
    const sortedFiles = filesWithPromptId.sort((a, b) => a.prompt_id.localeCompare(b.prompt_id));
    
    // Performance limit: show first 50 files
    const displayLimit = 50;
    const filesToShow = sortedFiles.slice(0, displayLimit);
    
    dv.table(
        ["prompt_id", "File", "ID", "Path"],
        filesToShow.map(p => [
            `<code>${p.prompt_id}</code>`,
            p.file.link,
            p.id || "—",
            `<small><code>${p.file.path.split('/').pop()}</code></small>`
        ])
    );
    
    if (sortedFiles.length > displayLimit) {
        dv.paragraph(`<small>📝 Showing first ${displayLimit} of ${sortedFiles.length} files. Set showAllFiles = false to hide this table.</small>`);
    }
}

// Statistics by ID ranges
dv.header(3, "📈 Statistics by ID Range");
const ranges = {
    "E0001xx": Array.from(promptIdMap.keys()).filter(pid => pid.startsWith("E0001")).length,
    "E0002xx": Array.from(promptIdMap.keys()).filter(pid => pid.startsWith("E0002")).length,
    "Others": Array.from(promptIdMap.keys()).filter(pid => !pid.startsWith("E0001") && !pid.startsWith("E0002")).length
};

const rangeStats = Object.entries(ranges)
    .filter(([range, count]) => count > 0)
    .map(([range, count]) => `**${range}**: ${count} files`)
    .join(" | ");

dv.paragraph(rangeStats);
```

## 🚀 Search Features

✅ **Quick Check**: Instant status for common prompt_id values  
✅ **Pattern Search**: Browse by ID patterns (E0001xx, E0002xx, etc.)  
✅ **Complete Listing**: Full sortable table of all files  
✅ **Statistics**: Distribution analysis by ID ranges  

## 🔧 How to Use

1. **Quick Check**: Use "Common IDs" for frequent lookups
2. **Pattern Browse**: Check "Advanced Search" for ID patterns  
3. **Full Search**: Use browser search (Ctrl+F / Cmd+F) in the complete table
4. **Custom Search**: Use Obsidian global search: `"prompt_id: E000XXX"`
5. **Performance**: Set `showAllFiles = false` to hide large table if needed

## 📝 Search Tips

- **Browser Search**: Most effective in the "All Files" table
- **Pattern Matching**: Use Advanced Search for ID ranges
- **Direct Links**: Click any file link to open directly
- **Performance**: Table limited to 50 files for fast loading