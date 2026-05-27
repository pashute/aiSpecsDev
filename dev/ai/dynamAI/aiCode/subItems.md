## Filename: subItems.md
## Version: 1.2
### Find all subitems (Github Project subissues)

### Input params
owner  - e.g. pashute
repo   - e.g. aiSpecsDev
number - parent item number (Github Project V2 issue) e.g. 7 

### Output format
JSON array of objects, each with:
- id: item number
- title: item title
- url: item HTML URL


### Errors
- No subitems: empty output (no error)
- Invalid item number/repo/owner: HTTP 404 Not Found


### Confirmed code for ai to use


```powershell
# Fetch sub-issues from GitHub issue (tested by developer)
gh api repos/{owner}/{repo}/issues/{number}/sub_issues --jq '.[] | {id: .number, title, url: .html_url}'
```

