## Filename: projectDetails.md
## Version: 1.0
### Fetch and cache GitHub Project V2 field IDs

### Input params
owner   - e.g. pashute
repo    - e.g. aiSpecsDev
itemnum - issue number to get project from (e.g., 7)

### Output format
JSON object with:
- projectUID: Project V2 uid
- projectNumber: Project number
- projectTitle: Project title
- statusFieldUID: Workflow stage field uid
- stageBacklogUID: Backlog option uid
- stageReadyUID: Ready option uid
- stageInProgressUID: In Progress option uid
- stageInReviewUID: In Review option uid
- stageDoneUID: Done option uid

### Errors
- Issue not in any project: no projectItems found
- Invalid item number/repo/owner: HTTP 404 Not Found

### Confirmed code for ai to use

```powershell
# Get project UID from issue (tested by developer)
$query = 'query($owner:String!, $name:String!, $number:Int!) { repository(owner:$owner, name:$name) { issue(number:$number) { projectItems(first:1) { nodes { id project { id title number } } } } } }'
$projectUID = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.id'
$projectNumber = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.number'
$projectTitle = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.title'

# Get project field UIDs (tested by developer)
gh api graphql -f query='query($id: ID!) { node(id: $id) { ... on ProjectV2 { fields(first: 20) { nodes { ... on ProjectV2SingleSelectField { id dataType name options { id name } } } } } } }' -f id={projectID}
```

### AI instruction for caching
- Check if project details exist in projdev.yaml projman section
- If exists and projectSame returns true, use cached values
- If not, fetch new values and store in projdev.yaml
