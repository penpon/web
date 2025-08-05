# Prompt ID Search & Browser

Fast prompt_id search and file browsing functionality for PermanentNote directory.

```dataviewjs
// Efficient data collection
let pages = dv.pages().where(p => p.file.folder === "Web/content/Zettelkasten/PermanentNote");
if (pages.length === 0) {
    pages = dv.pages().where(p => p.file.path.includes("PermanentNote"));
}

const pagesArray = Array.from(pages);
// Filter out main PI-XX files (like "PI-15 Time-Shift Scenario Prompting.md")
// Only include sub-files (PI-XX-YY.md format) and other files
const filesWithPromptId = pagesArray.filter(p => {
    if (!p.prompt_id) return false;
    
    // Exclude files that match pattern "PI-XX SomeTitle.md"
    const isMainPIFile = p.file.name.match(/^PI-\d+\s+.+\.md$/);
    return !isMainPIFile;
});

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
const excludedMainFiles = pagesArray.filter(p => p.prompt_id && p.file.name.match(/^PI-\d+\s+.+\.md$/)).length;
dv.paragraph(`**Total files:** ${stats.total} | **Files with prompt_id:** ${stats.withPromptId}`);
if (excludedMainFiles > 0) {
    dv.paragraph(`<small>ℹ️ Excluded ${excludedMainFiles} main PI-XX files from search (e.g., "PI-15 Time-Shift Scenario Prompting.md")</small>`);
}

// Enhanced search functionality
dv.header(2, "🔎 Advanced Search");

// Search by ID pattern
const patternSearch = {
    "E0000xx": Array.from(promptIdMap.keys()).filter(pid => pid.startsWith("E0000")).sort(),
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
    
    dv.table(
        ["prompt_id", "File", "ID", "Path"],
        sortedFiles.map(p => [
            `<code>${p.prompt_id}</code>`,
            p.file.link,
            p.id || "—",
            `<small><code>${p.file.path.split('/').pop()}</code></small>`
        ])
    );
}
```
