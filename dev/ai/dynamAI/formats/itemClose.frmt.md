## Filename: itemClose.frmt.md
## Version: 1.1
### Closing comment format for GitHub issues

### Format
```markdown
[{itemNum}]({itemUrl}): {itemTitle}

steps:
- [v] {stepNum}. {stepTitle}
  commits:
  - [{commitHash}]({commitUrl}): {commitHeadline}
    - files: [{file1}!]({fileurl}), [{file2}]({fileurl}), [{file3}]({fileurl}) # ! after filename if important change

---
Comment by AI assistant (Cascade)
```

### Notes
- Use telegraphic style for step titles
- Add ! after filename for important changes
- Include all commits related to the item
- Include attribution line at end of comment
