## Filename: steps.md
## Version: 1.1

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

Last action: opened item 10 and set stage to in progress

## Running dynamAI task: 3.CommitAndPush
Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)

## workflow stage fix

| step | name | details | verified | changed |
|------|------|---------|----------|---------|
| 1 | Stage change only in open item | Item change to in progress should be ONLY in open item, NOT during commit | yes | no |
|   | | Changes: None (no stage setting found in commit dynamAI) | | |
| 2 | Open item fail on stage error | Item open should fail, abort, and discuss with user if in-progress cannot be set | yes | yes |
|   | | Changes: Add error handling in 2a.OpenProjdevItem.md, halt on GraphQL failure | | 2a.OpenProjdevItem.md |
| 3 | Cache item UID in yaml | Item open should store itemID in yaml, itemStage should check yaml first | yes | yes |
|   | | Changes: Add item_uid field to active_item in projdev.yaml, update itemStage to check yaml | | projdev.yaml, itemStage.md, format.projdev.md |
| 4 | In progress until close | In progress stays from opening until item fully closed, subitems add to in progress items | yes | yes |
|   | | Changes: Added step 2.9 to set stage to done before closing, renumbered steps | | 2b.CloseProjdevItem.md |
| 5 | Close fail on stage error | Failing to change stage in item close should halt closeProjdevItem abort and discuss | yes | yes |
|   | | Changes: Added error handling in step 2.9, halt on GraphQL failure | | 2b.CloseProjdevItem.md |
| 6 | Commit validate stage | Commit should NOT proceed if in progress is not set, critical validation before committing | yes | yes |
|   | | Changes: Added step 1.1 to validate stage, renumbered subsequent steps | | 3.CommitAndPush.md |
| 7 | Item 10 open status review | Review if item 10 is open correctly or if in-progress failed, check for missing steps | yes | no |
|   | | Changes: None (review only) | | |

## fix openClose projman item steps

- [ ] Add closeItem suggestion instructions to 2b.CloseProjdevItem.md (check yaml, then item subitems, then feature subitems, then next feature)
- [ ] Add openItem failure handling to 2a.OpenProjdevItem.md (if item CLOSED in GitHub but open in yaml and NOT in completed_items: suggest reopen OR move to completed)
- [ ] Verify feature subitems stages in startFeature/projectDetails (ensure stage tracking works for all subitems)
- [ ] Move item 5 (templates) to completed_items in projdev.yaml with reason 'not planned' (cancelled)

- [x] 2b.CloseProjdevItem (aborted - need to update yaml with subitem first)
- [v] Update yaml with item 3's subitem 10
- [v] Verify automatic partial detection in closeItem - DOES NOT WORK (requires explicit developer choice)
- [v] Add automatic partial detection to 2b.CloseProjdevItem.md (added step 2.5, renumbered steps)
- [v] Commit changes
- [v] Partial close item 3 (automatic detection worked)
- [v] Commit partial close changes

## NodeJS implementation steps

- [v] 1. install nodejs (already installed v22.20.0)
- [v] 2. update src to run from a server (created server.js)
- [v] 3. run and check that all works (server tested successfully at http://localhost:3000/)
