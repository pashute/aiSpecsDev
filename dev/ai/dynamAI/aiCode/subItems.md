## Filename: subItems.md
## Version: 1.3
### Find all subitems (Github Project subissues) with full details

### Input params
owner  - e.g. pashute
repo   - e.g. aiSpecsDev
number - parent item number (Github Project V2 issue) e.g. 7

### Output format
JSON array of objects, each with:
- num: item number
- title: item title
- url: item HTML URL
- state: open/closed
- stage: workflow stage (from project status field)
- milestone: {number, title, due}


### Errors
- No subitems: empty output (no error)
- Invalid item number/repo/owner: HTTP 404 Not Found


### Confirmed code for ai to use


```powershell
# Fetch sub-issues from GitHub issue with basic details
$subitems = gh api repos/{owner}/{repo}/issues/{number}/sub_issues --jq '.[] | {num: .number, title, url: .html_url, state, milestone: {number: .milestone.number, title: .milestone.title, due: .milestone.due_on}}'

# For each subitem, fetch its workflow stage using GraphQL
$result = @()
foreach ($subitem in $subitems) {
  $stageData = gh api graphql -f query='
    query($owner: String!, $repo: String!, $number: Int!) {
      repository(owner: $owner, name: $repo) {
        issue(number: $number) {
          projectItems(first: 10) {
            nodes {
              fieldValues(first: 20) {
                nodes {
                  ... on ProjectV2SingleSelectField {
                    name
                    optionId
                  }
                }
              }
            }
          }
        }
      }
    }
  ' -F owner={owner} -F repo={repo} -F number=$subitem.num --jq '.data.repository.issue.projectItems.nodes[0].fieldValues.nodes[] | select(.name == "Status") | .name'
  
  $subitem | Add-Member -MemberType NoteProperty -Name "stage" -Value $stageData
  $result += $subitem
}

$result | ConvertTo-Json
```

