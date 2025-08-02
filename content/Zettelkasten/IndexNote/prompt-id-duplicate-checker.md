# Prompt ID Duplicate Checker

This page automatically checks for duplicate `prompt_id` values in the PermanentNote directory.

```dataviewjs
const duplicates = dv.pages('"Zettelkasten/PermanentNote"')
    .where(p => p.prompt_id)
    .groupBy(p => p.prompt_id)
    .filter(g => g.rows.length > 1)
    .sort(g => g.key);

if (duplicates.length > 0) {
    dv.header(2, "🚨 Duplicated prompt_id Found");
    dv.table(
        ["prompt_id", "Count", "Files"],
        duplicates.map(g => [
            g.key,
            g.rows.length,
            g.rows.map(p => p.file.link).join("<br>")
        ])
    );
    
    dv.header(3, "Summary");
    dv.paragraph(`Total duplicated prompt_id values: **${duplicates.length}**`);
    dv.paragraph(`Total files with duplicates: **${duplicates.reduce((sum, g) => sum + g.rows.length, 0)}**`);
} else {
    dv.header(2, "✅ No Duplicates Found");
    dv.paragraph("All prompt_id values in PermanentNote directory are unique.");
}

// Show total count of files with prompt_id
const totalFiles = dv.pages('"Zettelkasten/PermanentNote"')
    .where(p => p.prompt_id)
    .length;

dv.header(3, "Statistics");
dv.paragraph(`Total files with prompt_id property: **${totalFiles}**`);
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