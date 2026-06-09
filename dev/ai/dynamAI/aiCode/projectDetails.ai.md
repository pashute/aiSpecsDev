## Filename: projectDetails.md
## Version: 1.0.1
### Fetch and cache GitHub Project V2 field IDs

### Input params
owner   - e.g. pashute
repo    - e.g. aiSpecsDev
itemNum - issue number to get project from (e.g., 7)

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
$projectUID = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemNum} --jq '.data.repository.issue.projectItems.nodes[0].project.id'
$projectNumber = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemNum} --jq '.data.repository.issue.projectItems.nodes[0].project.number'
$projectTitle = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemNum} --jq '.data.repository.issue.projectItems.nodes[0].project.title'

# Get field UIDs of project
## (among them the project status, and its enumerated options: backlog, in-progress etc.)
gh api graphql -f query='query($id: ID!) { node(id: $id) { ... on ProjectV2 { fields(first: 20) { nodes { ... on ProjectV2SingleSelectField { id dataType name options { id name } } } } } } }' -f id={projectUID}
```

### AI instruction for caching
- Check if project details exist in projmng.yaml projman section
- If exists and projectSame returns true, use cached values
- If not, fetch new values and store in projmng.yaml

### AI instruction for feature subitems stage tracking
- When startFeature is called, use projectDetails to fetch stage option UIDs
- Ensure all feature subitems have stage information populated in projmng.yaml
- Use aiCode/itemStage.md to set and verify stages for each subitem
- This ensures stage tracking works for all subitems in the feature

### Remarks for human/AI team
- Current project UID: PVT_kwHOABsSM84BXhNk
- This UID is constant for this project and should be cached in projmng.yaml projman.uid
- Stage option UIDs are constant across all GitHub V2 Projects:
  - backlog: "f75ad846"
  - ready: "08afe404"
  - in_progress: "47fc9ee4"
  - in_review: "4cc61d42"
  - done: "98236657"
