# Prompt ID Duplicate Checker

Lightweight duplicate detection tool focused exclusively on finding duplicate prompt_id values.

```dataviewjs
// Efficient single-pass data collection
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

// Single-loop processing for efficiency
const promptIdMap = new Map();
const stats = { total: pagesArray.length, withPromptId: 0, duplicates: 0 };

filesWithPromptId.forEach(file => {
    stats.withPromptId++;
    const pid = file.prompt_id;
    if (!promptIdMap.has(pid)) {
        promptIdMap.set(pid, []);
    }
    promptIdMap.get(pid).push(file);
});

// Find duplicates efficiently
const duplicates = Array.from(promptIdMap.entries())
    .filter(([pid, files]) => files.length > 1)
    .sort((a, b) => a[0].localeCompare(b[0]));

stats.duplicates = duplicates.length;

// Display critical information first
dv.header(2, "📊 Quick Summary");
const excludedMainFiles = pagesArray.filter(p => p.prompt_id && p.file.name.match(/^PI-\d+\s+.+\.md$/)).length;
dv.paragraph(`**Files scanned:** ${stats.total} | **With prompt_id:** ${stats.withPromptId} | **Duplicates found:** ${stats.duplicates}`);
if (excludedMainFiles > 0) {
    dv.paragraph(`<small>ℹ️ Excluded ${excludedMainFiles} main PI-XX files from duplicate check (e.g., "PI-15 Time-Shift Scenario Prompting.md")</small>`);
}

// Priority 1: Show duplicates if any
if (duplicates.length > 0) {
    dv.header(2, "🚨 Duplicate prompt_id Found");
    dv.table(
        ["prompt_id", "Count", "Files"],
        duplicates.map(([pid, files]) => [
            `<code style="color:#dc3545;">${pid}</code>`,
            files.length,
            files.map(f => f.file.link).join(", ")
        ])
    );
} else {
    dv.header(2, "✅ No Duplicates Found");
}

// Structural issues analysis only (no detailed duplicate analysis)
if (duplicates.length > 0) {
    dv.header(3, "🔍 Structural Issues Analysis");
    
    duplicates.forEach(([pid, files], index) => {
        dv.header(4, `${index + 1}. Duplicate prompt_id: ${pid}`);
        
        // File details table
        dv.table(
            ["File", "ID", "Path", "Size"],
            files.map(f => [
                f.file.link,
                f.id || "—",
                `<small><code>${f.file.path}</code></small>`,
                f.file.size ? `${Math.round(f.file.size/1024)}KB` : "—"
            ])
        );
        
        // Detailed structural analysis
        const issues = [];
        
        files.forEach((file, fileIndex) => {
            const expectedId = pid.replace('E', 'PI-');
            const fileName = file.file.name;
            const actualId = file.id;
            
            // ID field analysis
            if (actualId && actualId !== expectedId) {
                issues.push({
                    type: "ID_MISMATCH",
                    severity: "⚠️",
                    file: fileName,
                    message: `ID field doesn't match prompt_id pattern`,
                    details: `Expected: "${expectedId}", Found: "${actualId}", prompt_id: "${pid}"`
                });
            }
            
            // Filename analysis
            if (fileName.includes('PI-')) {
                const fileIdMatch = fileName.match(/PI-(\d+(?:-\d+)?)/);
                if (fileIdMatch) {
                    const fileIdPart = fileIdMatch[1];
                    const expectedFileId = expectedId.replace('PI-', '');
                    
                    if (fileIdPart !== expectedFileId) {
                        issues.push({
                            type: "FILENAME_MISMATCH",
                            severity: "⚠️",
                            file: fileName,
                            message: `Filename doesn't match prompt_id`,
                            details: `File ID part: "${fileIdPart}", Expected: "${expectedFileId}", prompt_id: "${pid}"`
                        });
                    }
                }
            }
            
            // File path analysis
            const expectedPath = file.file.path.includes('PermanentNote');
            if (!expectedPath) {
                issues.push({
                    type: "PATH_ISSUE",
                    severity: "ℹ️",
                    file: fileName,
                    message: `File not in expected PermanentNote directory`,
                    details: `Path: ${file.file.path}`
                });
            }
        });
        
        // Pattern conflict analysis
        const mainFiles = files.filter(f => f.file.name.match(/PI-\d+-[^-]+\.md$/));
        const subFiles = files.filter(f => f.file.name.match(/PI-\d+-\d+\.md$/));
        
        if (mainFiles.length > 0 && subFiles.length > 0) {
            issues.push({
                type: "PATTERN_CONFLICT",
                severity: "🔄",
                file: "Multiple files",
                message: `Mix of main file and sub-files detected`,
                details: `Main files: ${mainFiles.map(f => f.file.name).join(', ')} | Sub files: ${subFiles.map(f => f.file.name).join(', ')}`
            });
        }
        
        // Display issues
        if (issues.length > 0) {
            dv.paragraph("**🔍 Detailed Issues Analysis:**");
            
            issues.forEach((issue, issueIndex) => {
                dv.paragraph(`**${issueIndex + 1}. ${issue.severity} ${issue.message}**`);
                dv.paragraph(`   **File:** \`${issue.file}\``);
                dv.paragraph(`   **Details:** ${issue.details}`);
                dv.paragraph(`   **Type:** \`${issue.type}\``);
                
                // Specific fix suggestions
                if (issue.type === "ID_MISMATCH") {
                    dv.paragraph(`   **💡 Fix:** Update the \`id\` field in the frontmatter to \`${pid.replace('E', 'PI-')}\``);
                } else if (issue.type === "FILENAME_MISMATCH") {
                    const correctFilename = issue.details.match(/Expected: "([^"]+)"/)?.[1];
                    if (correctFilename) {
                        dv.paragraph(`   **💡 Fix:** Rename file to include \`${correctFilename}\` or update prompt_id to match filename`);
                    }
                } else if (issue.type === "PATTERN_CONFLICT") {
                    dv.paragraph(`   **💡 Fix:** Ensure all files with same prompt_id follow consistent naming pattern`);
                }
                
                dv.paragraph("---");
            });
        } else {
            dv.paragraph("✅ **No structural issues detected** - All files have consistent ID, filename, and prompt_id values");
        }
        
        dv.paragraph("---");
    });
}
```

