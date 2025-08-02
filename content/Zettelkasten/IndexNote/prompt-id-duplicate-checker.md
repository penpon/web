# Prompt ID Duplicate Checker

This page automatically checks for duplicate `prompt_id` values in the PermanentNote directory.

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

## Usage

1. This checker automatically scans all files in the `Web/content/Zettelkasten/PermanentNote` directory
2. It identifies any duplicate `prompt_id` values
3. Results are displayed in a table format with:
   - The duplicated `prompt_id` value
   - Number of files using that ID
   - Direct links to the affected files
4. Click on any file link to navigate directly to that file

## Notes

- This checker only looks at files within the PermanentNote directory
- Files without a `prompt_id` property are ignored
- The results update automatically when files are modified
- To check for a specific prompt_id, use Obsidian's global search: `"prompt_id: E000138"`