## Filename: itemStage.md
## Version: 1.4
### Get or set GitHub Project V2 item workflow stage (status field)

### Getter mode (no stage input)
Fetch current workflow stage for an item.

### Setter mode (with stage input)
Set workflow stage for an item.

### Input params
owner  - e.g. pashute
repo   - e.g. aiSpecsDev
number - item number (Github Project V2 issue) e.g. 7
stage  - (optional for getter, required for setter) e.g. "In progress", "Done"
projectUID - GitHub Project V2 UID (from projdev.yaml projman.uid) - setter only
statusFieldUID - Status field UID (from projdev.yaml projman.status_field_uid) - setter only
itemUID - (optional) Project item UID from projdev.yaml active_item.item_uid - if provided, skip fetching

### Output format (getter)
JSON object with:
- stage: current workflow stage value
- stageUID: current workflow stage option UID

### Output format (setter)
JSON object with:
- success: true/false
- message: description of result or error

### Errors (getter)
- Invalid item number/repo/owner: HTTP 404 Not Found
- Project not found: GraphQL error
- Status field not found: GraphQL error

### Errors (setter)
- Invalid item number/repo/owner: HTTP 404 Not Found
- Invalid stage value: GraphQL error
- Project not found: GraphQL error
- Status field not found: GraphQL error

### Getter code

```powershell
# Get current workflow stage (status field) for an item
gh api graphql -f query='
  query($owner: String!, $repo: String!, $number: Int!) {
    repository(owner: $owner, name: $repo) {
      issue(number: $number) {
        projectItems(first: 10) {
          nodes {
            id
            fieldValues(first: 20) {
              nodes {
                ... on ProjectV2ItemFieldSingleSelectValue {
                  id
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
' -F owner={owner} -F repo={repo} -F number={number} --jq '.data.repository.issue.projectItems.nodes[0].fieldValues.nodes[] | select(.name != null) | {stage: .name, stageUID: .optionId}'
```

### Setter code

```powershell
# Set workflow stage (status field) for an item
# Check if itemUID is provided (cached from yaml)
if ({itemUID}) {
  $projectItemUID = {itemUID}
} else {
  # First, get the project item UID
  $projectItemUID = gh api graphql -f query='
    query($owner: String!, $repo: String!, $number: Int!) {
      repository(owner: $owner, name: $repo) {
        issue(number: $number) {
          projectItems(first: 10) {
            nodes {
              id
            }
          }
        }
      }
    }
  ' -F owner={owner} -F repo={repo} -F number={number} --jq '.data.repository.issue.projectItems.nodes[0].id'
}

# Use cached stage option UID from projdev.yaml or constant from note below
# Stage option UIDs are constant across all GitHub V2 Projects:
# backlog: "f75ad846", ready: "08afe404", in_progress: "47fc9ee4", in_review: "4cc61d42", done: "98236657"
$stageOptionUID = switch ({stage}) {
  "Backlog" { "f75ad846" }
  "Ready" { "08afe404" }
  "In progress" { "47fc9ee4" }
  "In review" { "4cc61d42" }
  "Done" { "98236657" }
}

# Set the stage using cached project UID and status field UID from projdev.yaml
gh api graphql -f query='
  mutation($projectItemUID: ID!, $fieldUID: ID!, $value: String!, $projectUID: ID!) {
    updateProjectV2ItemFieldValue(input: {
      projectId: $projectUID
      itemId: $projectItemUID
      fieldId: $fieldUID
      value: {
        singleSelectOptionId: $value
      }
    }) {
      projectV2Item {
        id
      }
    }
  }
' -f projectItemUID=$projectItemUID -f fieldUID={statusFieldUID} -f value=$stageOptionUID -f projectUID={projectUID}
```

### Note
Stage option UIDs are constant across all GitHub V2 Projects:
- backlog: "f75ad846"
- ready: "08afe404"
- in_progress: "47fc9ee4"
- in_review: "4cc61d42"
- done: "98236657"
