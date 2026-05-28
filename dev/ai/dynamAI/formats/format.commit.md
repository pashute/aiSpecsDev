## Filename: format.commit.md
## Version: 1.0
### Commit message format for projdev.yaml

### Format
```yaml
commits:
  - id: {commitHash}
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
```

### Notes
- When multiple changes to same file, list filename once with dashes for each change
- When only one change to a file, put it on the same line after a colon
- Group new files by type with headers (e.g., "New format files:", "New aiCode files:")
- For removed files: list as "Removed files:" followed by filenames in a single line
- id is the commit hash
- details and changes are free text lines
- Use telegraphic style (3 words or less per line)
