## Filename: steps.md
## Version: 1.2

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

Last action: reopened item 10 (metadata fix) by AI assistant (Cascade)

## Running dynamAI task: 2b.CloseProjdevItem by AI assistant (Cascade)
Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)

### Step 1.0 Record self
1.0.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: 2b.CloseProjdevItem by AI assistant (Cascade)`

1.0.2 Write project info to steps.md:
`Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)`

## fix openClose projman item steps (reopened)

- [x] 0. Fix username error (discussed with developer)
- [x] 1. Check steps and projmng.yaml with reopened item
- [x] 2. Rename files (projdev.yaml → projmng.yaml, .dyn.md, .ai.md extensions, update references)
- [x] 3. Update error handling (create halt.dyn.md, confirmAction.dyn.md, update references, remove inline handling)
- [x] 4. Update all dynamAI files with new references
- [x] 5. Rename projdevUpdate.md to projmngUpdate.dyn.md
- [x] 6. Fix 2b.CloseProjdevItem.md next-item suggestion
- [x] 7. Add openItem failure handling to 2a.OpenProjdevItem.md
- [x] 8. Verify feature subitems stages
- [x] 9. Move item 5 to completed_items
- [x] 10. Add instruction to CloseItem.dyn.md for item description updates
- [x] 11. Update small version on all new files (.dyn and .ai)
- [x] 12. Delete old .md files (after checking for new code)
- [x] 13. Check header.frmt.md references and update instructions.md
- [x] 14. Move version instructions from format.header to appropriate files (instructions.md, 3.CommitAndPush, 1b.EndFeature)
- [x] 15. Stage and commit old file deletions through dynamAI (3.CommitAndPush)
- [x] 16. Correct confirmAction.dyn.md assurance instructions (first confirmation assurance depends on action, no assurance in second confirmation)
- [x] 17. Disperse format.dynamAI.md:
  - [x] 17.1 Create steps.frmt.md (lines 77-117)
  - [x] 17.2 Create itemComment.frmt.md (lines 127-144)
  - [x] 17.3 Update references to new format files
  - [x] 17.4 Delete format.dynamAI.md
- [x] 18. Update 1a.StartFeature.dyn.md Developer's Consent step
- [x] 19. Update 1b.EndFeature.dyn.md Developer's Consent and second confirmation
- [x] 20. Update confirmAction.dyn.md with new structure
- [x] 21. Apply consent message footer to all confirmation steps
- [x] 22. Shorten pseudo sections (remove verifications if in prerequisites)
- [x] 23. Commit changes via dynamAI (3.CommitAndPush)
- [x] 24. Single-consent change:
  - [x] 24.1 Create silentCommitAndPush.dyn.md
  - [x] 24.2 Update 1a.StartFeature.dyn.md consent (show subitems state/stage)
  - [x] 24.3 Update 1b.EndFeature.dyn.md consent (show closed subitems, add silent commit)
  - [x] 24.4 Update 2a.OpenProjdevItem.dyn.md (remove second consent, show steps/subitems)
  - [x] 24.5 Update 2b.CloseProjdevItem.dyn.md (show closed steps/subitems, add silent commit)
  - [x] 24.6 Update 3.CommitAndPush.dyn.md (merge consents, add silent commit)
  - [x] 24.7 Fix all dynamAI last steps to beep and say done

### Ad-hoc fixes: Wait for developer's command for each:
- [v] 1. reset active item - from error.
- [v] 2. debug dev-consent not being requested. Simulate, no code changes.
     if steps.md had an instruction that modified a file's version
     and then "dyn commit (not silent)"
     Is there a waiting developer consent stage at the beginning and is it clear?
     Result: fixed dev-consent recorded as step with id (step number)
- [v] 2.1 consent step instruction in steps.md ([v] 1a, [v] 1b, [v] 2a, [v] 2b, [v] 3)
- [v] 3. datetime for completed item (closeItem.dyn)
  - [v] 3.1 projdev -> projmng and mini version
  - [v] 3.1.1 rename in vanilla/ folder projdev.yaml to projmng.yaml
  - [v] 3.1.2 increase mini version
  - [v] 3.1.3 rename 3rd version digit as "mini version" (iteration number) wherever instructed. (2 dyn files)
  - [v] 3.2 the completed time field for items completed in the vanilla/projmng.yaml
- [x] 4. subitems field ([x] openItem.dyn instructions + [x] projmng quickfix)
- [x] 5. feature: ai ui for steps consolidation (specsdev.ai)
- [x] 6. feature: ren project? specsdev.ai
- [x] 7. feature: bugfix items (option in yaml if is bugfix or feature, branchname fix/...)
- [x] 8. feature: vscode-extensionize specsdev.ai
- [x] 9. feature: tunes.ai (success: ta da da, fail: wa wa wa, warn: SOS)
- [x] 10. dev folder and file organize
  - [x] 10.1 make and move to folder dynamai/actions/ the 5 action dyn files there
  - [x] 10.2 make and move to folder dynamai/helper/ the rest of the dyn files
  - [x] 10.3 rename instructions.md to instructions.dyn.md and update all refs
  - [x] 10.4 rename in formats/ folder all format.{section}.md to {section}.frmt.md and update all refs
  - [x] 10.5 find unused files and unused sections and mark them with remark
- [v] 11. Get developer consent for 3.CommitAndPush (commit and push)
## Running dynamAI task: 3.CommitAndPush by AI assistant (Cascade)
Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)

### Step 1.0 Record self
1.0.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: 3.CommitAndPush by AI assistant (Cascade)`
1.0.2 Write project info to steps.md:
`Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)`

### Step 1.1 Single confirmation (commit)
See dynamAI/confirmation.md for CRITICAL HALT INSTRUCTION and confirmation format.

1.1.1 Display feature/item and steps done from steps.md and projmng.yaml
1.1.2 Write consent step to steps.md:
    - Get current steps.md step number (next available number)
    - Write to steps.md: "- [ ] {num} Get developer consent for 3.CommitAndPush"
    - DO NOT write further dyn steps to steps.md until consent is received

1.1.3 **Display confirmation question** (see confirmAction.frmt.md):
  - 3 beeps
  - "Feature: {feature.name} Item: {active_item.num}.{active_item.title}"
  - "Steps done: {md steps from steps.md}"
  - "Commit only or commit and push?"
  DO NOT PROCEED WITHOUT DEVELOPER'S OK
  If developer discusses, stay halted till ok or rejection given.
  Ask, if not explicitely given the ok to proceed.
On result:
- problem: Consult the developer
- no problem: Close step (developer approved commit and push) [v]

### Step 1.2 Create commit message
1.2.1 Get the commit hash (will be generated after commit)
1.2.2 Give the commit a headline
1.2.3 Give short details
1.2.4 List files (path) and changes
1.2.5 Include itemsteps in commit message (see commit.frmt.md)
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.3 Show summary to developer
1.3.1 Display completion table
1.3.2 Display commit message (headline + details first - WHAT was done)
1.3.3 Display file list secondary (5 files per row max)
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.4 Update versions
1.4.1 Remove the mini version (3rd digit) from all touched files and increment the minor version (e.g., 0.1.8.1 → 0.1.9). See header.frmt.md
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.5 Phase 1: Commit all files
1.5.1 Commit all changes (work files + metadata with completed steps listed): `git commit -m "{commit message}"`
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.6 Phase 1: Push
1.6.1 Push to remote: `git push`
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.7 Update projmng.yaml
1.7.1 Add commit to commits section (see projdev.frmt.md)
1.7.2 Update active_item.stage to "in review"
1.7.3 Update active_item.steps with completed steps from steps.md
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.8 Silent commit and push
1.8.1 Call silentCommitAndPush.dyn.md for metadata commit
1.8.2 On success: beep and say "done"
1.8.3 On failure: beep and say "ended with error"
On result:
- problem: Error already handled by silentCommitAndPush
- no problem: Close step [v]

### Step 1.9 Add comment to project item
1.9.1 Add comment to the GitHub project item (see itemComment.frmt.md):
  - {commit_hash}: Phase 1 commit hash
  - {commit_url}: Full GitHub commit URL
  - {telegraphic_summary}: Brief summary of changes
  - {question}: "Commit only or commit and push?" (already answered, use same response)
1.9.2 Use aiCode/itemComment.md to add comment
1.9.3 Input: owner, repo, itemNum, comment
1.9.4 Retrieve the comment URL from the response
1.9.5 Show the developer the link to the created comment
1.9.6 Beep and say "done"
On result:
- problem: Consult the developer
- no problem: Close step [v]

## Running dynamAI task: 2b.CloseProjdevItem by AI assistant (Cascade)
Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)

### Step 1.0 Record self
1.0.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: 2b.CloseProjdevItem by AI assistant (Cascade)`
1.0.2 Write project info to steps.md:
`Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)`

### Step 1.1 First confirmation (item close)
See dynamAI/confirmation.md for CRITICAL HALT INSTRUCTION and confirmation format.

1.1.1 Write consent step to steps.md:
    - Get current steps.md step number (next available number)
    - Write to steps.md: "- [ ] {num} Get developer consent for 2b.CloseProjdevItem"
    - DO NOT write further dyn steps to steps.md until consent is received

1.1.2 **Display confirmation question** (see confirmAction.frmt.md):
  - 3 beeps
  - "Close Item {itemNum} requested"
  - "Closed steps: {md steps from steps.md}"
  - "Closed subitems: {md subitem number.name list from projmng.yaml completed_items}"
  - "Proceed?"
  DO NOT PROCEED WITHOUT DEVELOPER'S OK
  If developer discusses, stay halted till ok or rejection given.
  Ask, if not explicitely given the ok to proceed.
On result:
- problem: Consult the developer
- no problem: Close step (developer approved item close) [v]

### Step 1.2 Validate current item
1.2.1 Read projmng.yaml to get active_item
1.2.2 Verify active_item matches item to close
1.2.3 If mismatch: Consult developer
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.3 Verify steps done
1.3.1 Read steps.md to verify all steps are marked as done
1.3.2 If any step not done: Consult developer
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.4 Determine close reason
1.4.1 Ask developer for close reason (completed, cancelled, deferred, duplicate)
1.4.2 Record close reason
On result:
- problem: Consult the developer
- no problem: Close step [v] - developer selected: completed

### Step 1.5 Close the item
1.5.1 Use aiCode/itemClose.md to close the GitHub item
1.5.2 Input: owner, repo, itemNum, close_reason
1.5.3 Verify item closed successfully
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.6 Update projmng.yaml for partial close
1.6.1 Move active_item to completed_items section
1.6.2 Add completed_at timestamp
1.6.3 Add close_reason
1.6.4 Add remarks if any
1.6.5 Clear active_item section
On result:
- problem: Consult the developer
- no problem: Close step [v]

### Step 1.7 Set item stage to Done
1.7.1 Use aiCode/itemStage.md to set item stage to "Done"
1.7.2 Verify stage set successfully
On result:
- problem: ERROR: Could not resolve to a node with the global id of 'PVTI_lAHOABsSM84BXhNkzzguQTLc' - item was closed before stage was set. Halt and consult developer.
- no problem: Close step

### Step 1.8 Silent commit and push
1.8.1 Call silentCommitAndPush.dyn.md for metadata commit
1.8.2 On success: beep and say "done"
1.8.3 On failure: beep and say "ended with error"
On result:
- problem: Error already handled by silentCommitAndPush
- no problem: Close step [v]

### Step 1.9 Suggest next item
1.9.1 Check projmng.yaml for next item in priority order
1.9.2 If none, check item's subitems for next open item
1.9.3 If none, check feature's subitems for next open item
1.9.4 If none, check for next feature in backlog
1.9.5 Display suggestion to developer
On result:
- problem: Consult the developer
- no problem: Close step [v] 