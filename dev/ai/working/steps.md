## Filename: steps.md
## Version: 1.0

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header "Steps for AI" (including that line)

# Steps for AI:

Last action: completed 2b.CloseProjdevItem for item 7 (closed as completed)

## Running dynamAI task: 3.CommitAndPush
Project info: aiSpecsDev, feature/WriteSomeSpecs, [8.fix closeItem problem](https://github.com/pashute/aiSpecsDev/issues/8)

## Fix projdev.yaml and test project details

- [v] 0. beep after sending mesasage to user. 
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
- [ ] 10. if all ok commitNpush. otherwise consult developer (meaning wait through iterations tell the user releases the conversation)
- [ ] 11. and if all good, close item.  STOP on any problem this is testing that it works. 
 

