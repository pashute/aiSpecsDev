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

## Step 1.0 Record self
1.0.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: 2b.CloseProjdevItem by AI assistant (Cascade)`

1.0.2 Write project info to steps.md:
`Project info: aiSpecsDev, feature/WriteSomeSpecs, [10.fix openClose projman item](https://github.com/pashute/aiSpecsDev/issues/10)`

## fix openClose projman item steps (reopened)

- [x] 0. fix username error. When dynamai is being used, changes to the project are listed on the developer mflam, and not on the ai's user. ai should discuss how it can and will fix the problem. should subscribe with AI username during openItem. IMPORTANT: no changes till AFTER the developer approval and explicit ok to proceed.
- [x] 1. Check that steps and projmng.yaml are with reopened item if not mark #10 as the current item being worked on, and take it out manually from the yaml completed items section, or mark it partialy complete. (discuss this with the developer, explain what you want to do and get approval b4 doing.
- [x] 2. rename files as follows:
  - [x] rename projdev.yaml to projmng.yaml
  - [x] rename dynamAI files to .dyn.md extension
  - [x] rename aiCode files to .ai.md extension
  - [x] check that all references are correct in all documentation and code including steps.md and yaml
- [x] 3. Update error handling and confirmation procedures:
  - [x] Create halt.dyn.md for error handling
  - [x] Create confirmAction.dyn.md for confirmation flow
  - [x] Update instructions.md to reference halt.dyn.md
  - [x] Update dynamAI files to reference halt.dyn.md and confirmAction.dyn.md
  - [x] Remove inline error handling from dynamAI pseudo sections
  - [x] Remove pseudo steps placeholders from dynamAI files
- [x] 4. Update all dynamAI files with new references:
  - [x] 1a.StartFeature.dyn.md
  - [x] 1b.EndFeature.dyn.md
  - [x] 2a.OpenProjdevItem.dyn.md
  - [x] 2b.CloseProjdevItem.dyn.md
  - [x] 3.CommitAndPush.dyn.md
  - [x] addItem.dyn.md
- [x] 5. Rename projdevUpdate.md to projmngUpdate.dyn.md and update references
- [x] 6. Fix 2b.CloseProjdevItem.md next-item suggestion
- [x] 7. Add openItem failure handling to 2a.OpenProjdevItem.md
- [x] 8. Verify feature subitems stages
- [x] 9. Move item 5 to completed_items (already done)
- [x] 10. Add instruction to CloseItem.dyn.md to update item description with checkboxes ticked on what was done
- [x] 11. Update small version on all new files (.dyn and .ai extensions)
- [x] 12. Handle renamed old files:
  - [x] 12.1 Before deleting old files check we didn't put new code into them by mistake
  - [x] 12.2 Delete the old files
- [x] 13. Versions:
  - [x] 13.1 Check where format.header.md is called
  - [x] 13.2 Read instructions section in format.header and update instructions.md and other dyn files accordingly
- [ ] 14. Move version instructions from format.header.md to appropriate files:
  - [ ] 14.1 Update instructions.md with version instructions (3.7, 3.8)
  - [ ] 14.2 Update 3.CommitAndPush.dyn.md with version update step (before commit)
  - [ ] 14.3 Update 1b.EndFeature.dyn.md with version consolidation step
  - [ ] 14.4 Delete instructions section from format.header.md 