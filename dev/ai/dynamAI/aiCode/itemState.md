## Filename: itemState.md
## Version: 1.0
### Get GitHub issue state

### Input params
owner   - e.g. pashute
repo    - e.g. aiSpecsDev
number  - issue number

### Output format
JSON object with:
- state: issue state (open, closed)
- stateReason: reason for state (e.g., completed, not planned, duplicate)

### Errors
- Invalid item number/repo/owner: HTTP 404 Not Found

### Confirmed code for ai to use

```powershell
# Get issue state
$issue = gh api repos/{owner}/{repo}/issues/{number}

$result = @{
  state = $issue.state
  stateReason = $issue.state_reason
}

$result | ConvertTo-Json
```
