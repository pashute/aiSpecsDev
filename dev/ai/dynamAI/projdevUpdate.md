## Filename: projdevUpdate.md
**Version:** 1.3

Project development data at current stage

## Purpose
Instructions for updating projdev.yaml during the workflow.

## Variable notation
{varname} = placeholder for known value or PowerShell command result
Example: {owner} = current repo owner from projdev.yaml

## Sections

### On Start Feature
- 1. Set active_item from provided item number: 
```markdown
gh api repos/{owner}/{repo}/issues/{itemNum} # fetch item details
```

- 2. Verify issue is suitable as feature item:
```markdown
# Use aiCode/isFeatureItem.md to check:
# - Has feature name format (title starts with "feature/")
# - Has no parent
# If not valid, stop with error
```
- !! If parent exists, stop with error:  
_Start feature should be a top level item!_   
_it has a parent:_  {parent num }: {parent_title}

- 3. Move project item to in-progress.

Use aiCode/projectDetails.md to fetch project details and cache in projdev.yaml projman section:
- projman.num = projectNumber
- projman.name = projectTitle
- projman.uid = projectUID
Use aiCode/itemStage.md setter to advance workflow stage to "in progress".

- 4. Set feature.item fields same as active item fields


### On End Feature
- Clear feature.item, parent_item, active_item

### On Open Projdev Item
- Set active_item with item details (num, title, state, stage, url, milestone: {number, title, due}) from GitHub
- Set parent_item with parent details (num, title, state, stage, url, milestone: {number, title, due})
- Fetch and populate subtasks array using aiCode/subItems.md (num, title, state, stage, url, milestone: {number, title, due} for each)
- Advance workflow stage to "in progress" using itemStage.md setter

### On Close Projdev Item
- Move active_item to completed_items
- IMPORTANT: completed_items should only include items that are done or deferred
- Clear active_item
- Update parent_item if needed

#### Close feature item
If this is a request to close a feature head item, 
go to 1b. End Feature dynamAI

### On item step start
- Record step start time in /dev/ai/steps.md 
- Record telegraphic planned step content 

### On item step completed
- Record steps.md step completion status ([-] deferred, [x] cancelled, [V] no need, [v] done, [!] discuss)

### On Commit and Push
- Log commit details in commits section (see format.projdev.md for schema)
- Verification steps (see 3.CommitAndPush.md for commands):
  - Verify commit succeeded with `git log -1 --format="%H %s"`
  - Get commit URL: https://github.com/{owner}/{repo}/commit/{hash}
  - Verify push succeeded with `git log origin/{branch}..HEAD` (should be empty)
  - Get GitHub commit URL: https://github.com/{owner}/{repo}/commit/{hash}

### Format
- projdev.yaml schema and field explanations is listed in /dev/ai/dynamAI/formats/format.projdev.md
