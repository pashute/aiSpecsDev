Document name: steps
Version: 1.0
Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [!] discuss

- [v] 1. Create projdevUpdate.md dynamAI file
- [v] 2. Update projdev.yaml according to projdevUpdate.md specs
  - [v] Remove archiving from On End Feature
  - [v] Add workflow stage advance to On Start Feature
  - [v] Add workflow stage advance to On Open Projdev Item
  - [v] Add parent number retrieval command
  - [v] Add {variable} notation explanation
  - [v] Change item order to active, parent, head
- [v] 3. Correct 1a.StartFeature to accept projdev item link for feature creation

- a. addendum: Developer added aiCode folder
- [v] a1. Familiarize new folder and files
- [v] a2. look for and notify developer of code for finding subItems. 
- [v] a3. Wait for developer's ok
- [v] a4. move the code to new subItems.md
- [v] a5. notify done and give developer the current item details 
     (number, url, title)
- [v] a6. wait for developer to run and check it manually. We'll be checking the current item. (feature/WriteSomeSpecs)
- [v] a7. see dev changes to subItems.md and finish Update for version 1.1 with input/output/error. 

- b. addendum: 
- [v] b5. Before each step ai tells developer what it intends to do. (telegraphic)
- [v] b6. Run each step only after developer's ok.
- [v] b7. discuss each step's results (telegraphic)


- c. addendum: Check 2a.startItem with developer
- [v] b1. We'll be using the first subItem of the current feature. 
- [v] b2. Developer changed readme.md with feature hierarchy of items. see it, and update instructions and openFeature accordingly. (the feature is now the parent item) see next step too.
- [v] b3. Developer changed yaml schema (in aiCode). accordingly change yaml (developer made some changes towards that) 
- [v] b4. show developer list of what files need to be corrected and how to update yaml correctly. 
- [v] b5. update the yaml's feature item and subtasks. 
- [v] b6. fix all. and then review that everything is unified nothing missing. finally, make a checkbox list of all fixes and have developer review. add into the list any questions you have
- [v] b7. commit and push without following the commit-push instructions (only this once). use msg:  feature/WriteSomeSpecs instruction fixes. And telegraphic list of files changed and why (3 words at most per file)

- d. addendum: Create aiCode functions for item/project details
- [v] d1. Create aiCode/itemDetails.md with state, labels, milestone, closed reason
- [v] d2. Create aiCode/projectSame.md - check project hasn't changed
- [v] d3. Create aiCode/projectDetails.md - cache or fetch project field IDs
- [v] d4. Check that 1a is correct with inserting current feature number and name (while leaving yaml comments as is)
- [v] d5. Update yaml with current project details (num: 5, url: https://github.com/users/pashute/projects/5)
- [v] d6. Check if project numbers are listed elsewhere and move to projectDetails.md as remarks for hum&AI team
- [v] d7. Clean up references to point to aiCode files

- c. addendum:  update 1a with subitems search and record (in yaml).
- [v] check that developer is on same page. sees 1aStartFeature file
- [v] propose instruction text for subitem search in 2a: 
  - [v] this should include each input on a line and where its from 
- [v] propose aiCode filenames for any missing "functions" that are used in 1a.
- [v] upon ok do it, and get the developer's ok

- [v] reminder: before each step, wait for developer's ok to proceed.
- [v] 4. Update 2b.CloseProjdevItem with verification logic
- [v] 5. Update 2a.OpenProjdevItem.md with active item check
- [v] 6. Add file header description to all dynamAI files
- [V] 7. Move projdev.yaml update instructions to projdevUpdate.md
- [v] 8. Add variable notation explanation to instructions.md
- [v] 9. Check that all documents have header with two lines
- [v] 10. Check process correctness and discuss improvements
- [v] 10.1 fix bell: in settins.json
- [v] 10.2 check it works (command: [console]::Beep(800, 500))
- [v] 10.3 restart vscode
- [v] 10.4 ask copilot about the blue button and giving it permission so it wont ask again.
- [v] 11. Use dynamAI instructions for all relevant requested actions from now.
- [v] 12. Add single-change instruction to format.commit.md
- [v] 12.1 Add new/removed file instructions to format.commit.md
- [v] 13. Commit using dynamAI instructions
- [v] 14. Add commit/push verification instructions to 3.CommitAndPush.md
- [v] 15. Verify commit 2889cc2 and get commit URL
- [v] 16. Verify push and get GitHub commit URL
- [v] 17. Update projdev.yaml with commit details
- [v] 18. Check if commit/push verification instructions are redundant in projdevUpdate.md
- [v] 19. Check if dynamAI 3.CommitAndPush.md correctly references projdevUpdate.md for yaml updates
- [v] 19.1 Fix format.projdev.md to clarify array structure
- [v] 19.2 Simplify projdevUpdate.md to reference format.projdev.md
- [ ] 20. Commit changes to instructions and steps.md
- [ ] 21. Show results to developer
- [ ] 22. Close current item (follow dynamai)
