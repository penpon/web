# Prompt ID Duplicate Checker & Search

This page automatically checks for duplicate `prompt_id` values and provides search functionality.

```dataviewjs
// Method 1: Using folder path
let pages = dv.pages().where(p => p.file.folder === "Web/content/Zettelkasten/PermanentNote");

// If Method 1 doesn't work, try Method 2: Using path contains
if (pages.length === 0) {
    pages = dv.pages().where(p => p.file.path.includes("PermanentNote"));
}

// If still no results, try Method 3: All pages then filter
if (pages.length === 0) {
    pages = dv.pages().where(p => p.file.folder?.includes("PermanentNote"));
}

// Convert to array and process
const pagesArray = Array.from(pages);
const filesWithPromptId = pagesArray.filter(p => p.prompt_id);

// Create search functionality using DataviewJS
dv.header(2, "🔍 Prompt ID Search");
dv.paragraph("**How to search:**");
dv.paragraph("1. Use browser search (Ctrl+F / Cmd+F) in the 'All Files' section below");
dv.paragraph("2. Or check the quick search examples:");

// Quick search examples with common patterns
const searchExamples = [
    "E000140", "E000141", "E000142", "E000143", "E000144"
];

dv.paragraph("**Quick Examples:** " + searchExamples.map(id => {
    const matches = filesWithPromptId.filter(f => f.prompt_id === id);
    if (matches.length > 0) {
        return `<code style="background:#d4edda; padding:2px 4px;">${id}</code> (${matches.length} file${matches.length>1?'s':''})`;
    } else {
        return `<code style="background:#f8d7da; padding:2px 4px;">${id}</code> (not found)`;
    }
}).join(" | "));

dv.header(3, "📋 All Files with prompt_id");
if (filesWithPromptId.length > 0) {
    const sortedFiles = filesWithPromptId.sort((a, b) => a.prompt_id.localeCompare(b.prompt_id));
    dv.table(
        ["prompt_id", "File", "ID", "Path"],
        sortedFiles.map(p => [
            `<code>${p.prompt_id}</code>`,
            p.file.link,
            p.id || "—",
            `<small><code>${p.file.path}</code></small>`
        ])
    );
} else {
    dv.paragraph("⚠️ No files with prompt_id found.");
}

// Group by prompt_id manually
const groupedByPromptId = {};
filesWithPromptId.forEach(p => {
    const promptId = p.prompt_id;
    if (!groupedByPromptId[promptId]) {
        groupedByPromptId[promptId] = [];
    }
    groupedByPromptId[promptId].push(p);
});

// Find duplicates
const duplicates = Object.entries(groupedByPromptId)
    .filter(([promptId, files]) => files.length > 1)
    .sort((a, b) => a[0].localeCompare(b[0]));

dv.header(2, "🔍 Scanning Results");
dv.paragraph(`Scanned files: **${pagesArray.length}** total files in PermanentNote`);
dv.paragraph(`Files with prompt_id: **${filesWithPromptId.length}**`);

if (duplicates.length > 0) {
    dv.header(2, "🚨 Duplicated prompt_id Found");
    dv.table(
        ["prompt_id", "Count", "Files", "Paths"],
        duplicates.map(([promptId, files]) => [
            promptId,
            files.length,
            files.map(p => p.file.link).join("<br>"),
            files.map(p => `\`${p.file.path}\``).join("<br>")
        ])
    );
    
    dv.header(3, "📊 Summary");
    dv.paragraph(`Total duplicated prompt_id values: **${duplicates.length}**`);
    const totalDuplicatedFiles = duplicates.reduce((sum, [promptId, files]) => sum + files.length, 0);
    dv.paragraph(`Total files with duplicates: **${totalDuplicatedFiles}**`);
} else {
    dv.header(2, "✅ No Duplicates Found");
    dv.paragraph("All prompt_id values in PermanentNote directory are unique.");
}

// Debug: Show sample of found files
dv.header(3, "🔧 Debug Info");
const sampleFiles = pagesArray.slice(0, 5);
if (sampleFiles.length > 0) {
    dv.paragraph("Sample files found:");
    dv.list(sampleFiles.map(p => `${p.file.name} (${p.file.path}) - prompt_id: ${p.prompt_id || "none"}`));
} else {
    dv.paragraph("⚠️ No files found in PermanentNote directory. Please check the path configuration.");
}
```

## 🔧 How to Use

### Duplicate Detection
1. The checker automatically scans all files in the PermanentNote directory
2. Duplicate `prompt_id` values are displayed in the "Duplicated prompt_id Found" section
3. Click on any file link to navigate directly to that file

### Searching for Specific prompt_id
1. **Browser Search Method** (Recommended):
   - Look at the "All Files with prompt_id" table above
   - Use browser search (Ctrl+F / Cmd+F) to find specific prompt_id values
   - All prompt_id values are displayed in `code` format for easy searching

2. **Quick Check Method**:
   - Check the "Quick Examples" line for common prompt_id values
   - Green background = found, Red background = not found

3. **Table Features**:
   - Files are sorted by prompt_id for easy browsing
   - Includes file links, ID values, and file paths
   - Click any file link to open that file directly

## 📝 Notes

- **Scope**: Only scans files in the PermanentNote directory
- **Filter**: Files without `prompt_id` property are ignored  
- **Auto-update**: Results refresh automatically when files are modified
- **Search Tip**: Use browser search (Ctrl+F / Cmd+F) in the table above for fastest results