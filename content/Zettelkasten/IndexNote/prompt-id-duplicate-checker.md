# Prompt ID Duplicate Checker

Lightweight duplicate detection tool focused exclusively on finding duplicate prompt_id values.

```dataviewjs
// Efficient single-pass data collection
let pages = dv.pages().where(p => p.file.folder === "Web/content/Zettelkasten/PermanentNote");
if (pages.length === 0) {
    pages = dv.pages().where(p => p.file.path.includes("PermanentNote"));
}

const pagesArray = Array.from(pages);
const filesWithPromptId = pagesArray.filter(p => p.prompt_id);

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
dv.paragraph(`**Files scanned:** ${stats.total} | **With prompt_id:** ${stats.withPromptId} | **Duplicates found:** ${stats.duplicates}`);

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

// Detailed duplicate analysis
if (duplicates.length > 0) {
    dv.header(3, "📊 Duplicate Analysis");
    const totalDuplicatedFiles = duplicates.reduce((sum, [pid, files]) => sum + files.length, 0);
    dv.paragraph(`**Total affected files:** ${totalDuplicatedFiles}`);
    dv.paragraph(`**Duplicate prompt_id values:** ${duplicates.length}`);
    
    // Show severity
    const severity = duplicates.length > 5 ? "🔴 High" : duplicates.length > 2 ? "🟡 Medium" : "🟢 Low";
    dv.paragraph(`**Severity:** ${severity}`);
    
    // Detailed breakdown of each duplicate
    dv.header(3, "🔍 Detailed Breakdown");
    
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
        
        // Analysis of this specific duplicate
        const analysis = [];
        if (files.some(f => f.id && f.id !== pid.replace('E', 'PI-'))) {
            analysis.push("⚠️ ID field doesn't match prompt_id pattern");
        }
        if (files.some(f => f.file.name.includes('PI-') && !f.file.name.includes(pid.replace('E', 'PI-')))) {
            analysis.push("⚠️ Filename doesn't match prompt_id");
        }
        
        // Check for PI-XX vs PI-XX-YY pattern conflicts
        const hasMainFile = files.some(f => f.file.name.match(/PI-\d+-[^-]+\.md$/));
        const hasSubFiles = files.some(f => f.file.name.match(/PI-\d+-\d+\.md$/));
        if (hasMainFile && hasSubFiles) {
            analysis.push("🔄 Mix of main file and sub-files detected");
        }
        
        if (analysis.length > 0) {
            dv.paragraph("**Issues detected:**");
            analysis.forEach(issue => dv.paragraph(`- ${issue}`));
        } else {
            dv.paragraph("✅ No structural issues detected");
        }
        
        // Recommendations
        dv.paragraph("**💡 Recommended Actions:**");
        if (files.length === 2) {
            dv.paragraph("- Review content to determine if files should be merged");
            dv.paragraph("- Assign unique prompt_id to one of the files");
            dv.paragraph("- Check if one file is a draft or outdated version");
        } else {
            dv.paragraph("- **High Priority**: Multiple files sharing same prompt_id");
            dv.paragraph("- Audit all files for content overlap");
            dv.paragraph("- Consider creating a file naming convention document");
        }
        
        dv.paragraph("---");
    });
    
    // Global recommendations
    dv.header(3, "🛠️ Global Recommendations");
    const globalRecs = [];
    
    if (duplicates.length === 1) {
        globalRecs.push("**Low Impact**: Single duplicate detected - easy to resolve");
        globalRecs.push("Assign a new unique prompt_id to one of the duplicate files");
    } else if (duplicates.length <= 3) {
        globalRecs.push("**Medium Impact**: Multiple duplicates require attention");
        globalRecs.push("Review file creation workflow to prevent future duplicates");
    } else {
        globalRecs.push("**High Impact**: Systematic duplicate issue detected");
        globalRecs.push("Implement prompt_id generation and validation process");
        globalRecs.push("Consider bulk renaming tools for consistency");
    }
    
    globalRecs.push("Use [[prompt-id-search]] to verify uniqueness before creating new files");
    
    globalRecs.forEach(rec => dv.paragraph(`- ${rec}`));
}
```

