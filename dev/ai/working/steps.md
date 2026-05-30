## Filename: steps.md
## Version: 1.0

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

Last action: completed `Item 7: Finish dynamAI workflow`
but didn't close item yet.  Before that: 

- [v] 1. make a new /dev/ai/working folder
- [v] 2. move into it: projdev.yaml and steps.md and ai-draft.md
- [v] 3. fix all references to these files everywhere in the project to point to the ai/working folder. (you can use that description or give the path).
- [v] addendum 1:  Why were there uncommitted files after we did a commit?! you found it during close item.  look at the instructions of commit and see if we missed something?  (or maybe we cannot check anymore because i put 1 2 and 3 in between after the failed close item.  do we still have the current item set?)
- [v] 4 See changes to instruction.md.
- [v] 5 See new formats/format.dynamAI.md 
- [v] 6 See new formats/format.header.md  (you saw it already if you read the instructions.md carefully)
- [v] 7 See 2b.CloseProjdevItem.md partial changes. lets complete that as follows:
  - [v] 71 replace the `## Developer confirmations required` section with detailed step endings inside the steps, as shown in format.dynamai section 2.3 (i think)
- [v] 72  reconstruct the dynamai according to the format. remove all redundant and unnecessary wording summarize telegraphicly and point to the other files as needed. 
- [v]  73 supply the pseudo
- [v] add steps 8 and on with updating all the other dynamAI to this structure:  8.x  for each dynamAI and 8.x.2 for the pseudo section of each.
- [v] 9.1 Add step for each file changed to steps.md
- [v] 9.2 Change version of any file touched to 0.1.4
- [v] 9.3 Fix 2b.CloseProjdevItem.md according to new format.dynamAI.md structure
- [v] 9.4 Add missing steps from pseudo to 2b.CloseProjdevItem.md (comparison table, discussion)
- [v] 9.5 Delete wrong steps in 2b.CloseProjdevItem.md and update content
- [v] 9.6 Critically review 2a.OpenProjdevItem.md for similar mistakes
- [v] 9.7 Critically review 1a.StartFeature.md for similar mistakes
- [v] 9.8 Critically review 1b.EndFeature.dynai.md for similar mistakes
- [v] 10 Discuss how to verify all files committed when commitAndPush itself modifies files (steps.md, projdev.yaml)
- [v] 11.1 Update 3.CommitAndPush.md to implement two-phase commit (phase 1: all files, phase 2: metadata only)
- [v] 11.2 Add logic to other dynamAI tasks to check if only steps.md and projdev.yaml are uncommitted
- [v] 11.3 If those two reflect recent completed commit, notify developer and add step to commit them
- [v] 11.4 Update all dynamAI files to version 0.1.5
- [v] 12 Commit all changes using 3.CommitAndPush dynamAI
- [ ] 13 Close the item using 2b.CloseProjdevItem dynamAI

Last action: completed 3.CommitAndPush for item 7 (commit 43bfa98)

