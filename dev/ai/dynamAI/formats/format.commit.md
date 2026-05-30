## Filename: format.commit.md
## Version: 1.4
### Commit message format for projdev.yaml

### Format
```yaml
commits:
  - hash: {commitHash}
    headline: {commitHeadline}
    details:
      - "{detail line 1}"
      - "{detail line 2}"
    filechanges:
      - filename: {filename}
        path: {path/to/file}
        changes:
          - "{change description 1}"
          - "{change description 2}"
      - filename: {anotherFilename}
        path: {path/to/another/file}
        changes:
          - "{change description 1}"
    itemsteps:
      - "{item step 1 from GitHub description/comments}"
      - "{item step 2 from GitHub description/comments}"
```

### Notes
- When multiple changes to same file, list filename once with dashes for each change
- When only one change to a file, put it on the same line after a colon
- Group new files by type with headers (e.g., "New format files:", "New aiCode files:")
- For removed files: list as "Removed files:" followed by filenames in a single line
- hash is the commit hash
- details and changes are multiline free-text blocks (array of telegraphic description lines)
- itemsteps: list of all checkbox steps from the item's GitHub description and comments (NOT from steps.md)
- Use telegraphic style (3 words or less per line)

### Summary display format (for developer review)
When showing commit summary to developer (step 2.2 in 3.CommitAndPush.md):
1. **Primary**: Show WHAT was done (headline + details)
2. **Secondary**: Show file list (5 files per row max)
3. Display completion table before commit message
4. Wait for developer ok before proceeding
