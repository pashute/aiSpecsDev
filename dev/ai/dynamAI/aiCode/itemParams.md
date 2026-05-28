## Filename: itemParams.md
## Version: 1.0
### Fetch GitHub item simple parameters (item number, title and url)

### Input params
owner  - e.g. pashute
repo   - e.g. aiSpecsDev
number - e.g. 7 (the issue number)

### Output format
JSON object with:
- number: item number (Github Project V2 issue number)
- title: item title
- url: issue API URL

### Errors
- Invalid item number/repo/owner: HTTP 404 Not Found

### Confirmed code for ai to use

```powershell
# Fetch projdev item (Github Project V2 issue) details
gh api repos/{owner}/{repo}/issues/{number} --jq '{number, title, url}'
```
