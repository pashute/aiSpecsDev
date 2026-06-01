## Filename: ai-draft.md
## Version: 0.91
# A file for the AI to do whatever it wants. Do not erase this line

# Pseudo dynamAI for opening item 10 and setting stage

**dynamai name:** 2a.OpenProjdevItem (for item 10)

**action:** Open item 10 and set stage to in progress

**step 1.1 First confirmation (item open)**
- Display confirmation question with {accomplished}, {assurance}, {question}
- Follow confirmation.md CRITICAL HALT INSTRUCTION

**step 1.2 Fetch item details**
- Verify issue state is "open" using aiCode/itemState.md
- Fetch item details using aiCode/itemDetails.md
- Fetch subitems using aiCode/subItems.md
- Parse item body for checkbox steps

**step 1.3 Check active_item context**
- Check if requested item is a subtask of active_item
- Check for uncommitted files using `git status --porcelain`

**step 1.4 Confirm item open**
- Display confirmation question
- Wait for developer's ok

**step 2.1 Handle parent progress**
- Save current steps.md progress to parent_item.steps_progress if needed

**step 2.2 Update projdev.yaml**
- Set active_item to item 10 (num, title, url, state, stage, milestone)
- Set parent_item to item 3 (num, title, url)

**step 2.3 Set item stage to in progress**
- Call aiCode/itemStage.md with:
  - owner: pashute (from yaml)
  - repo: aiSpecsDev (from yaml)
  - number: 10 (item num)
  - stage: "In progress"
  - projectUID: PVT_kwHOABsSM84BXhNk (from yaml projman.uid)
  - statusFieldUID: PVTSSF_lAHOABsSM84BXhNkzhSth4Q (from yaml projman.status_field_uid)

**aiCode/itemStage.md:**
- GraphQL query to get project item UID:
  ```
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
  ```
  - Parameters: owner (String), repo (String), number (Int)
  - Returns: project item UID

- GraphQL mutation to set stage:
  ```
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
  ```
  - Parameters: projectItemUID (ID), fieldUID (ID), value (String - stage option UID), projectUID (ID)
  - Returns: success/failure status

**step 2.4 Generate steps**
- Read item body to understand requirements
- Generate steps in steps.md based on item requirements

