## Filename: itemStage.md
## Version: 1.0
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
projectID - GitHub Project V2 ID (from projdev.yaml projman.id)
statusFieldID - Status field ID (from projdev.yaml projman.status_field_id)

### Output format (getter)
JSON object with:
- stage: current workflow stage value
- stageID: current workflow stage option ID

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
                ... on ProjectV2SingleSelectField {
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
' -F owner={owner} -F repo={repo} -F number={number} --jq '.data.repository.issue.projectItems.nodes[0].fieldValues.nodes[] | select(.name == "Status") | {stage: .name, stageID: .optionId}'
```

### Setter code

```powershell
# Set workflow stage (status field) for an item
# First, get the project item ID
$projectItemID = gh api graphql -f query='
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

# Then, find the stage option ID from project status field
$stageOptionID = gh api graphql -f query='
  query($id: ID!) {
    node(id: $id) {
      ... on ProjectV2 {
        fields(first: 20) {
          nodes {
            ... on ProjectV2SingleSelectField {
              id
              name
              options {
                id
                name
              }
            }
          }
        }
      }
    }
  }
' -f id={projectID} --jq ".data.node.fields.nodes[] | select(.name == \"Status\") | .options[] | select(.name == \"{stage}\") | .id"

# Finally, set the stage
gh api graphql -f query='
  mutation($projectItemID: ID!, $fieldID: ID!, $value: String!) {
    updateProjectV2ItemFieldValue(input: {
      projectId: $projectID
      itemId: $projectItemID
      fieldId: $fieldID
      value: $value
    }) {
      projectV2Item {
        id
      }
    }
  }
' -f projectItemID=$projectItemID -f fieldID={statusFieldID} -f value=$stageOptionID
```

### Note
Stage option IDs are constant across all GitHub V2 Projects:
- backlog: "f75ad846"
- ready: "08afe404"
- in_progress: "47fc9ee4"
- in_review: "4cc61d42"
- done: "98236657"
