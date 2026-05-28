## Filename: format.itemClose.md
## Version: 1.0
### Closing comment format for GitHub issues

### Format
```markdown
[{itemNum}]({itemUrl}): {itemTitle}

steps:
- [v] {stepNum}. {stepTitle}
  commits:
  - [{commitHash}]({commitUrl}): {commitHeadline}
    - files: [{file1}!]({fileurl}), [{file2}]({fileurl}), [{file3}]({fileurl}) # ! after filename if important change
```

### Notes
- Use telegraphic style for step titles
- Add ! after filename for important changes
- Include all commits related to the item
