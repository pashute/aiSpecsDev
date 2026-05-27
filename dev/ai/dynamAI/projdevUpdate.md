## Filename: projdevUpdate.md
**Version:** 0.93

## Purpose
Instructions for updating projdev.yaml during the workflow.

## Variable notation
{varname} = placeholder for known value or PowerShell command result
Example: {owner} = current repo owner from projdev.yaml

## Sections

### On Start Feature
- 1. Set active_item from provided item number: 
```markdown
gh api repos/{owner}/{repo}/issues/{itemnum} # fetch item details
```

- 2. Verify no parent exists:  
```markdown
gh api graphql -f query=$query -F owner={owner} -F name={repo} -F number={itemnum} --jq '.data.repository.issue.parent.number' # get parent number. null if none. 
# if parent_number is not null: 
gh api repos/{owner}/{repo}/issues/{parent_number} # fetch parent details
```
- !! If parent exists, stop with error:  
_Start feature should be a top level item!_   
_it has a parent:_  {parent id }: {parent_title}

- 3. Move project item to in-progress. 

In order to do so, we need to fetch `project specific IDs`:  
The item's fieldID, the workflow stage ("status") fieldID, and its enumerated options: Backlog, Ready, In Progress, In Review, Done. 

```yaml
# needed to add/update the issue's project item and set it's workflow stage
projectId: "{projectId}" # GH Project V2 id
itemId:    "projItemId"  # issue in GH Project V2

# workflow stage fields: 
statusFieldId: "{statusFieldId}" 

# workflow stage options: 
inProgressOptionId: "{inProgressOptionId}" # in progress
doneOptionId: "{doneOptionId}"             # done
```

For these we need first to get the project ID: 

- 3.1 Start with the {projectID} and {projitemID}: 
```powershell
# must use params with -F flag, otherwise query strips quotemarks
$query = 'query($owner:String!, $name:String!, $number:Int!) { repository(owner:$owner, name:$name) { issue(number:$number) { projectItems(first:1) { nodes { id project { id title number } } } } } }'

$projectId = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.id'

$projectNumber = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.number'

$projectTitle = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.title'

# example:


#
```powershell
# must use params with -F flag, otherwise query strips quotemarks
$query = 'query($owner:String!, $name:String!, $number:Int!) { repository(owner:$owner, name:$name) { issue(number:$number) { projectItems(first:1) { nodes { id project { id title number } } } } } }'
$query = 'query($owner:String!, $name:String!, $number:Int!) { repository(owner:$owner, name:$name) { issue(number:$number) { projectItems(first:1) { nodes { id project { id title number } } } } } }'

$projectId = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.id'
$projectTitle = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.title'
$projectNumber = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.repository.issue.projectItems.nodes[0].project.number'

# example:
$projectid = gh api graphql -f query=$query -F owner="pashute" -F name="aiSpecsDev" -F number=7 --jq 'data.repository.issue.projectItems.nodes[0].project.id'

# data/repository/issue/projectItems/nodes[0]
# "id": "PVTI_lAHOABsSM84BXhNkzgsnkd4",
# "project/id": "PVT_kwHOABsSM84BXhNk",
# "title": "aiSpecsDev",
# "number": 5
```

- 3.2  Get rest of fields according to the {projectID}
```markdown
# fetch project-specific field IDs
gh api graphql -f query='query($id: ID!) { node(id: $id) { ... on ProjectV2 { fields(first: 20) { nodes { ... on ProjectV2SingleSelectField { id dataType name options { id name } } } } } } }' -f id={projectID}

# Field IDs
$FID_WorkflowStage = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].id'

# Workflow Stage options:
$FID_Backlog = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].options[0].id'

$FID_Ready = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].options[1].id'

$FID_InProgress = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].options[2].id'

$FID_InProgress = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].options[2].id'

$FID_InReview = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].options[3].id'

$FID_Done = gh api graphql -f query=$query -F owner="{owner}" -F name="{repo}" -F number={itemnum} --jq '.data.node.fields.nodes[2].options[4].id'

#example
$projID = "PVT_kwHOABsSM84BXhNk"
gh api graphql -f query='query($id: ID!) { node(id: $id) { ... on ProjectV2 { fields(first: 20) { nodes { ... on ProjectV2SingleSelectField { id dataType name options { id name } } } } } } }' -f id=$projID

# Workflow Stages (Project V2 Item Status)
# field id and name
# ----------------------------------------
# stageID = "PVTSSF_lAHOABsSM84BXhNkzhSth4Q"
# stage   = "Status"

# --- Workflow-stage options ---
# (Note: These Field IDs are constant across all GH V2 Projects)
# stageBacklogID    = "f75ad846",  stageBacklog    ="Backlog"
# stageReadyID      = "08afe404",  stageReady      = "Ready"
# stageInProgressID = "47fc9ee4",  stageInProgress = "In progress"
# stageInReviewID   = "4cc61d42", stageInReview    = "In review"
# stageDoneID       = "98236657", stageDone        = "Done"

```

- 4. Advance the item's workflow-stage (from "Backlog" to "in progress"
```markdown
#advance current item to in progress

```

- 4. Set feature.item fields same as active item fields


### On End Feature
- Clear feature.item, parent_item, active_item

### On Open Projdev Item
- Set active_item with item details (id, title, state, stage, url, milestone, date) from GitHub
- Set parent_item with parent details (id, title, state, stage, url, milestone, date)
- Fetch and populate subtasks array (id, title, state, stage, url, milestone, date for each)
- Advance workflow stage to "in progress" using itemStage.md setter

### On Close Projdev Item
- Move active_item to completed_items
- Clear active_item
- Update parent_item if needed

### On item step start
- Record step start time

### On item step completed
- Record step completion
- Update steps.md status

### On Commit and Push
- Log commit details in commits section

### Format
- projdev.yaml schema and field explanations
