## Filename: steps.md
## Version: 1.1

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

Last action: completed 2b.CloseProjdevItem for item 8

## Running dynamAI task: 2b.CloseProjdevItem
Project info: aiSpecsDev, feature/WriteSomeSpecs, [8.fix closeItem problem](https://github.com/pashute/aiSpecsDev/issues/8)

## Fix projdev.yaml and test project details

- [v] 0. beep after sending mesasage to user.
- [v] 0.1 for now skip asking user between steps but:  you need to close step for each step done:
  - mark step done in steps
  - beep
  - (get ok to proceed - off for now)
  - IMPORTANT when you reach executing the dynamAI code, you need to definitely get back to asking for ok between each step in steps and between each stop point in the dynamai. this is critical for testing together.
- [v] 1.1 Create a new subitem under the featureItem. (new item. set head feature-item as parent)
- [v] 1.2 update projdev.yaml with this subitem as next after the closed one (which was 7)  - use subItems aicode
- [v] 2. Keep cached setter in itemStage.md (verify it's still used in the code there)
- [v] 3. Fix StartFeature to get the workflow-stage (proj v2 status) uid with its option uids into the projdev.yaml.
- [v] 4. Fix projdev.yaml - missing workflow stage UID and options (project V2 status)
- [v] 5 update current projdev.yaml with stage (V2 status) and options UIDs
- [v] 6. Test itemStage.md with the cached details and fix any errors there.
- [v] 7. Correct CloseItem to Clear parent item from projdev.yaml when done.
- [v] 8. Correct Yaml to have cleared parent.
- [V] 9. Check that close item wrties to suggest next item from projdev.yaml
- [v] 10. if all ok commitNpush. otherwise consult developer (meaning wait through iterations tell the user releases the conversation)
- [v] 11. Add confirmation question format to format.dynamAI.md and update all dynamAI files (1a, 2a, 1b(rename), 2b, 3,projdevInstructions) versions 0.1.6
- [x] REVERT:  revert latest commit, done without consent!!!. But keep these steps.md instructions.
- [v] 12. verify that the first (and 2nd where applicable) confirm-message instructions importance is listed in BOLD in all basic dynamai's  (1a, 1b, 2a, 2b, 3, format.dynamAI.md)
- [v] 13. summary instructions of commit and push should show WHAT was done. File list is secondary with 5 files in each row at most.
- [v] 14. promised 2nd developer confirmation should work where needed. (at least: 1b, 2b, 3(b?)) is it clearly in the instructions.
- [v] 15. Discuss with user if something can be done to prevent commits and closures wihtout consent.
- [v] 16. confirmation messages
  - [v] 16.1 format.dynamai.md should have INTERNAL INSTRUCTION: STOP! NO {ACTION} WITHOUT IMMEDIATE DEVELOPER'S CONSENT. before every basic dynamai main action: COMMIT, START OF FEATURE, END OF FEATURE, ITEM OPENED, ITEM CLOSED. The first one is an ARE YOU SURE kind of question.
  - [v] 16.2 verify that before the 2nd developer confirmation message in the different files (with feature-end note, item-close note, commit note), should say: STOP!! NO {ACTION} WITHOUT AN INFORMED DEVELOPER'S CONSENT
  - [v] 16.3 verify that both confirmation messages should be shown in md format with line after line. long lists should be turned into sections ie 5 filenames on each line at most.
  - [v] 16.4 during dynamai step notification to developer format: {dynamAI taskname (ie `(1a) OpenItem`)} {stepnum}.{stepname}
- [V] 19. review dynamAI files: verify pseudo matches steps and critical halt is marked
  - [V] 19.1 review 1a.StartFeature.md pseudo vs steps - MISMATCH: pseudo missing first confirmation step
  - [V] 19.2 review 1b.EndFeature.md pseudo vs steps - MISMATCH: pseudo missing first and second confirmation steps
  - [V] 19.3 review 2a.OpenProjdevItem.md pseudo vs steps - MISMATCH: pseudo missing first confirmation step
  - [V] 19.4 review 2b.CloseProjdevItem.md pseudo vs steps - MISMATCH: pseudo missing first and second confirmation steps
  - [V] 19.5 review 3.CommitAndPush.md pseudo vs steps - MISMATCH: pseudo missing first and second confirmation steps
  - [V] 19.6 review confirmation.md - OK
- [V] 20. CRITICAL HALT: review changes before commit (beep 3 times, wait for approval)
- [V] 17. commit (with aicode and dynamai-task) to test dynamai changes
- [V] 18. close item 8 to test both dynamAI questions
