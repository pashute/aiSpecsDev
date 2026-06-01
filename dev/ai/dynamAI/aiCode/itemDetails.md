## Filename: itemDetails.md
## Version: 1.3
### Fetch GitHub item details with state, labels, milestone

### Input params
owner  - e.g. pashute
repo   - e.g. aiSpecsDev
number - item number (Github Project V2 issue) e.g. 7

### Output format
JSON object with:
- number: item number
- title: item title
- state: open/closed
- stateReason: reason for closed state (e.g., "duplicate", "completed"), null if open
- labels: array of label objects (if any exist)
- milestone: {number, title, due}

### Errors
- Invalid item number/repo/owner: HTTP 404 Not Found

### Confirmed code for ai to use

```powershell
# Fetch item details (tested by developer)
gh api repos/{owner}/{repo}/issues/{number} --jq '{number, title, state, stateReason, labels, milestone: {number: .milestone.number, title: .milestone.title, due: .milestone.due_on}}'
```

### AI instruction for labels
If labels array is not empty, extract label UID and name:
```powershell
# Get labels with UID and name (if labels exist)
gh api repos/{owner}/{repo}/issues/{number} --jq '.labels | map({id: .node_id, name})'
```
