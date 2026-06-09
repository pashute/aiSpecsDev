## Filename: addItem.dyn.md
**Version:** 0.1.0

# Pseudo:
Goal: Add a new GitHub project item to the current feature

Inputs: parentNumber (optional), featureNumber (optional)

Prerequisites:
- Feature branch exists and is active in Git
- Correct feature is listed in projmng.yaml
- Developer confirmation before adding item
- On problems NOTIFY, HALT, and CONSULT

Verifications:
- Ask developer for parentNumber (if not provided)
- Ask developer for featureNumber (if not provided)
- Verify parent item exists and is open
- Verify item with same number does not already exist
- Check for similar items (warn if found)

Steps:
- Ask developer for item title
- Ask developer for item steps (in steps.md format)
- Create GitHub issue with title and steps
- Add item to parent's subtasks in projmng.yaml
- Set item stage to "backlog"
- Update steps.md with new item steps

Results:
- New GitHub issue created
- Item added to parent's subtasks in projmng.yaml
- Item stage set to "backlog"
- steps.md populated with item steps

Error handling:
- On error: NOTIFY, HALT, and CONSULT according to halt.dyn.md

# General instructions for this dynamAI task:
Reminders:
- See ai/instructions.md section 2.2. Specifically:
  - Discuss with the developer includes waiting for their response.
  - Stop execution if something is wrong.
  - On error NOTIFY, HALT, and CONSULT according to `halt.dyn.md`

- See formats/format.steps.md for instructions about writing to steps.md file

- See formats/format.dynamAI.md for instructions to close a step
(steps.md, notify developer)
- Before any PowerShell command or web access: announce in AI chat what you are doing and why
- After any PowerShell command or web access: report in AI chat what was accomplished

# Steps:

## Input Validation steps

### Step 1.0 Record self
1.0.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: addItem by AI assistant (Cascade)`
No result checking here. Continue.

1.0.2 Write project info to steps.md:
`Project info: {projman.name}, {feature.branch}, [adding new item]`
No result checking here. Continue.

### Step 1.1 Get parent and feature numbers
1.1.1 If parentNumber not provided, ask developer: "Enter parent item number (or leave empty if no parent):"
1.1.2 If featureNumber not provided, ask developer: "Enter feature item number (or leave empty if current feature):"
1.1.3 If parentNumber provided, verify parent item exists and is open using aiCode/itemState.md
1.1.4 If parent is not open, warn developer and ask to confirm
On result:
- problem: Consult the developer
- no problem: Close step

### Step 1.2 Check for duplicates and similar items
1.2.1 Check if item with same number already exists in projmng.yaml
1.2.2 If duplicate found, warn developer and ask to confirm
1.2.3 Check for similar items (by title) in projmng.yaml
1.2.4 If similar items found, warn developer and ask to confirm
On result:
- problem: Consult the developer
- no problem: Close step

## Action steps

### Step 2.1 Get item details
2.1.1 Ask developer for item title
2.1.2 Ask developer for item steps (in steps.md format with checkboxes)
2.1.3 Display summary of item details and ask for confirmation
On result:
- problem: Consult the developer
- no problem: Close step

### Step 2.2 Create GitHub issue
2.2.1 Use GitHub API to create new issue with title and steps
2.2.2 Input: owner, repo, title, body (steps)
2.2.3 Get the issue number and URL from response
On result:
- problem: Consult the developer
- no problem: Close step

### Step 2.3 Update projmng.yaml
2.3.1 Add new item to parent's subtasks in projmng.yaml (or to feature.item if no parent)
2.3.2 Set item stage to "backlog"
2.3.3 Include item number, title, state, stage, url
On result:
- problem: Consult the developer
- no problem: Close step

### Step 2.4 Update steps.md
2.4.1 Write the new item steps to steps.md
2.4.2 Format steps as checkboxes with proper indentation
On result:
- problem: Consult the developer
- no problem: Close step
