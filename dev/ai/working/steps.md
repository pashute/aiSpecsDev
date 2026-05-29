## Filename: steps.md
## Version: 1.0
Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

- [v] make a new /dev/ai/working folder
- [v] move into it: projdev.yaml and steps.md and ai-draft.md
- [v] fix all references to these files everywhere in the project to point to the ai/working folder. (you can use that description or give the path).

# Item 7: Finish dynamAI workflow
- [V] 1. Create projdevUpdate.md dynamAI file
  - [V] Create file in /dev/ai/dynamAI folder with header (Filename, Version)
  - [V] Add description: "Instructions for updating projdev.yaml"
  - [V] Mark "update" sections (chapters) `On Start Feature`, `On Open Item`, `On Commit and Push`, `On Close Item`, `On End Feature` and a `Format` section
  - [V] Move projdev.yaml format section from instructions.md to bottom of projdevUpdate.md
  - [V] Add below it a section Format explanations
  - [V] Move out of all long explanations from projdev.yaml to this section of projdevUpdate.md
  - [V] Confirm one by one with developer that they are correct
  - [V] Change instruction for Head item: (Set during Start Feature)
    - If no parent, the head is the same as the item itself
    - Parent stays empty if no parent
  - [V] Subtasks field should have an array of subtask item number and title
  - [V] Turn around the order of the item section in the yaml format, to: 1. current, 2. parent and 3. head
  - [V] Every item should have issue_state (open/closed) with reason (duplicate, not planned, completed)
  - [V] Every item should have workflow_stage (GH Project V2 item status): backlog, ready, in progress, in review, done
  - [V] Add new section in projdev.yaml format with projman fields
  - [V] In section On Start Feature: change instructions for head/current/parent item
  - [V] In section On Start Feature: Add step to fetch project-specific field IDs
  - [V] Add project-specific field ID fetching instructions
  - [V] Add GraphQL command for workflow-stage (status field) and options
  - [V] In each chapter, document what fields are updated and when
  - [V] Add repo validation
- [v] 2. Update projdev.yaml according to projdevUpdate.md specs
  - [v] Change field order
  - [v] Add the new fields
  - [v] Run the code to fill the project section field IDs
  - [v] Consult the developer with changes, and wait for ok to proceed
- [v] 3. Correct 1a.StartFeature to accept projdev item link for feature creation
  - [V] Developer supplies GitHub issue URL/Github Project item number when starting feature
  - [V] Go to On Start Feature section in projdevUpdate dynamAI subsection: set item and get project information
  - [V] Verify that the given item has no parent item (supply the generic code)
  - [V] Developer will manually run the commands and see that all works ok
  - [V] Wait for developer's ok to proceed
- [v] 4. Update 2b.CloseProjdevItem with verification logic
  - [v] Verify with user that we are closing the current item
  - [v] Cannot close if any unclosed subtasks (GitHub project sub-issues)
  - [v] Check subtasks array in projdev.yaml before allowing close
- [v] 5. Update 2a.OpenProjdevItem.md with active item check
  - [v] Check active_item in projdev.yaml
  - [v] If empty → proceed (previous item closed)
  - [v] If active_item is parent of new item → proceed, no warning
  - [v] If active_item is other item → stop, warn, ask to close first
- [v] 6. Check file header with Filename and Version in all files (code,md or any other text format)
  [v] 7. Move projdev.yaml update instructions to projdevUpdate.md
  - [v] Remove detailed update instructions from instructions.md
  - [v] Keep only "update projdev.yaml" reference in instructions.md give section and subsection
  - [v] Remove detailed update instructions from 1a.StartFeature.md Step 1 (lines 24-32), replace with reference to projdevUpdate.md section "On Start Feature" subsection 1
  - [v] Remove detailed update instructions from 1a.StartFeature.md Step 6 (lines 96-103), replace with reference to projdevUpdate.md section "On Start Feature" subsection 2
  - [v] Remove detailed update instructions from 2a.OpenProjdevItem.md Step 3 (lines 41-49), replace with reference to projdevUpdate.md section "On Open Item" subsection 1
  - [v] Reference projdevUpdate.md for detailed instructions in all dynamAI files with section and subsection
  - [v] In projdevUpdate.md Add a subsection number if a reference to a certain subsection exists. And update the caller with that index number
- [v] 8. Add variable notation explanation to instructions.md
  - [v] Add "Variable notation" section after "Typical spelling mistakes"
  - [v] Explain that {varname} indicates a variable whose value is either known from projdev.yaml or retrieved through a PowerShell command
  - [v] Note: This is called "variable notation" or "placeholder syntax" (not mustache code)
  - [v] Include examples: {owner} = repo owner from projdev.yaml, {repo} = repository name from projdev.yaml, {featurename} = feature name, {projectID} = GitHub Project V2 ID, {itemnum} = item number
- [=] 9. Check that all documents have header with two lines (duplicate of step 6)
