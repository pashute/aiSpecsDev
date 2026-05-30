## Filename: steps.md
## Version: 1.1

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

Last action: completed 2b.CloseProjdevItem for item 7 (closed as completed)

## Running dynamAI task: 3.CommitAndPush
Project info: aiSpecsDev, feature/WriteSomeSpecs, [8.fix closeItem problem](https://github.com/pashute/aiSpecsDev/issues/8)

## Running dynamAI task: 2b.CloseProjdevItem
Project info: aiSpecsDev, feature/WriteSomeSpecs, [8.fix closeItem problem](https://github.com/pashute/aiSpecsDev/issues/8)

## Fix projdev.yaml and test project details

- [v] 0. beep after sending mesasage to user. 
- [v] 3.CommitAndPush step 1.1: Displayed confirmation question
- [v] 16.1 format.dynamai.md: Added INTERNAL INSTRUCTION for all main actions
- [v] 16.2 Added STOP!! instruction before 2nd confirmation in 1b, 2b, 3
- [v] 16.3 Verified confirmation format uses markdown code blocks (already in format)
- [v] 16 confirmation messages completed
- [v] 3.CommitAndPush step 1.1: Verified commit and push request
- [v] 3.CommitAndPush step 1.2: No item steps found in GitHub issue
- [v] 3.CommitAndPush step 2.1: Created commit message
- [v] 3.CommitAndPush step 2.2: Showed summary to developer 
- [v] 0.1 for now skip asking user between steps but:  you need to close step for each step done:  
  - mark step done in steps
  - beep 
  - (get ok to proceed - off for now)
  - IMPORTANT when you reach executing the dynamAI code, you need to definitely get back to asking for ok between each step in steps and between each stop point in the dynamai. this is critical for testing together. 
- [v] 1.1 Create a new subitem under the featureItem. (new item. set head feature-item as parent)

Here's the code:
```
$headers = @{ "Authorization" = "token YOUR_GITHUB_TOKEN"; "Accept" = "application/vnd.github+json" }
$childId = (Invoke-RestMethod -Uri "https://api.github.com/repos/OWNER/REPO/issues/CHILD_NUM" -Headers $headers).id
$body    = @{ sub_issue_id = [int]$childId } | ConvertTo-Json
Invoke-RestMethod -Uri "https://api.github.com/repos/OWNER/REPO/issues/PARENT_NUM/sub_issues" -Method Post -Headers $headers -Body $body
```

  - title: fix closeItem problem
  - if any problem continues after two tries discuss with developer and wait for them. 
- [v] 1.2 update projdev.yaml with this subitem as next after the closed one (which was 7)  - use subItems aicode

- [v] 2. Keep cached setter in itemStage.md (verify it's still used in the code there)
- [v] 3. Fix StartFeature to get the workflow-stage (proj v2 status) uid with its option uids into the projdev.yaml.
  - [v] probably in projdevInstructions in the startFeature (where it should be) or openProjdevItem (where it shouldn't be)
  - [v] probably has a call to aiCode (good) or has the actual code (no good)
   - [v] find which aiCode has it, and which (pref: projectDetails  or itemDetails) should have it.
   - [V] test the aicode with the developer. (meaning wait for developers response)  use the corrected? (FieldItemSingleSelectValue) perhaps quotemarks for uid setting
- [v] 4. Fix projdev.yaml - missing workflow stage UID and options (project V2 status)
- [v] 5 update current projdev.yaml with stage (V2 status) and options UIDs 
- [v] 6. Test itemStage.md with the cached details and fix any errors there. 
- [v] 7. Correct CloseItem to Clear parent item from projdev.yaml when done. 
- [v] 8. Correct Yaml to have cleared parent. 
- [V] 9. Check that close item wrties to suggest next item from projdev.yaml
- [v] 10. if all ok commitNpush. otherwise consult developer (meaning wait through iterations tell the user releases the conversation)
- [v] 11. Add confirmation question format to format.dynamAI.md and update all dynamAI files (1a, 2a, 1b(rename), 2b, 3,projdevInstructions) versions 0.1.6 
- (no need. [x] REVERT:  revert latest commit, done without consent!!!. But keep these steps.md instructions. )
- [v] 12. verify that the first (and 2nd where applicable) confirm-message instructions importance is listed in BOLD in all basic dynamai's  (1a, 1b, 2a, 2b, 3, format.dynamAI.md) 
- [v] 13. summary instructions of commit and push should show WHAT was done. File list is secondary
with 5 files in each row at most. 
- [v] 14. promised 2nd developer confirmation should work where needed. (at least: 1b, 2b, 3(b?)) is it clearly in the instructions. 
- [v] 15. Discuss with user if something can be done to prevent commits and closures wihtout consent.
- [ ] 16. confirmation messages
  - [ ] 16.1 format.dynamai.md should have 
  INTERNAL INSTRUCTION: STOP! NO {ACTION} WITHOUT IMMEDIATE DEVELOPER'S CONSENT.
  before every basic dynamai main action: COMMIT, START OF FEATURE, END OF FEATURE, ITEM OPENED, ITEM CLOSED, 
The first one is an ARE YOU SURE kind of question. 

   - [ ] 16.2  Before the 2nd developer confirmation message in the different files, 
(with feature-end note, item-close note, commit note),  should say:
   STOP!! NO {ACTION} WITHOUT AN INFORMED DEVELOPER'S CONSENT
  
  - [ ] 16.3  both confirmation messages should be shown in md format with line after line.
        - long lists should be turned into sections ie 5 filenames on each line at most. 

- [ ] 17. commit (with aicode and dynamai-task) to test dynamai changes
- [ ] 18. close item 8 to test both dynamAI questions 
 

