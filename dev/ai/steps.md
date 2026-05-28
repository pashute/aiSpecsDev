Document name: steps
Version: 1.0
Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [!] discuss

- some of following steps have been done. you'll pretend you're doing it again, this time stopping after each step, verifying that it was done by looking at the code, and consulting with your important team-mate the developer (named Pashute) between each step.  wait for user to say next before proceeding to next step.

- DO NOT MARK AS DONE until an explicit done received from me.
- DO NOT MOVE TO A NEXT STEP without my saying next

# step by step area. stop for ok between

- [v] 1. update 3.CommitAndPush.md: to create a completion table before commit comment. This is how (and has to be rephrased and put inthe instructions/format/aiCode)
  - 1a. Read item's steps from description and comments
  - 1b. For each item step, find similar steps in steps.md and list them
  - 1c. Decide if step was completed or not by marking it with [v?] or [x?]
  - 1d. When done all steps, or if no steps,  consult with user and WAIT FOR OK TO PROCEED  
  - 1d. Complete the commit-comment with this info
  - 1e. Update format.commit.md to include the github item steps (not our worked-out steps that we decide during our discussions listed in steps.md)
- [v] 2. In projdev.yaml completed section, only include items done or deferred
- [v] 3. In 3.CommitAndPush.md: add comment to project item with commit hash and link
- [v] 4. Commit changes (completed without proper dynamAI confirmations - error)
- [v] 5. Correct projdev.yaml commits section format - filechanges as comma-separated lists
- [v] 6. Update format.projdev.md with completed_items schema and corrected filechanges format
- [v] 7. Fix projdev.yaml feature.name, feature.branch, and active_item.stage fields
- [v] 8. Verify 1a.StartFeature.md and 2a.OpenProjdevItem.md instruct to fill feature/project/branch fields
- [v] 9. Add step in 3.CommitAndPush.md to show developer comment link after creating it 
- [v] 9b. (and wait for ok to proceed!!)
- [v] 10. Update instructions.md with prerequisite check for projdev.yaml completeness
- [v] 11. Fix all ID fields to be 'num' (projectNum, itemNum, etc.) across all aiCode and dynamAI files
- [v] 12. Remove remarks explaining num vs id where no longer needed
- [v] 13. Enhance subItems.md to fetch state, stage, milestone for each subtask
- [v] 14. Fix milestone structure to {number, title, due} across format.projdev.md and projdev.yaml
- [v] 15. Update projdevUpdate.md to fetch projman.name from projectDetails.aiCode
- [v] 16. Update all references to date to be milestone.due
- [v] 16b. Update instructions for moving to subitem/brother item within same feature:
    - Check for uncommitted files before moving to subitem (warn and suggest commit first)
    - When moving down to subitem: check if parent still has open subitems before coming back
    - Add these checks to 2a.OpenProjdevItem.md and relevant dynamAI files
- [v] 16c. Add recursive parent close logic to 2b.CloseProjdevItem.md:
    - After closing item, check if parent has any open subitems using aiCode/subItemsClosed.md
    - If parent has no open subitems, recursively close the parent item
    - Use parent's record from projdev.yaml to close it
- [v] 16d. Add parent progress preservation when opening child item:
    - When opening child without closing parent, save parent's steps progress
    - Store progress in projdev.yaml parent_item section (add steps_progress field)
    - Restore parent progress when returning to parent
- [v] 17. Open item 7 using 2a.OpenProjdevItem.md dynamAI (careful test mode, user OK at each step)
- [v] 17b. Add logic to 2a.OpenProjdevItem.md to check if requested item is a child of current item:
    - Check if active_item has subtasks in projdev.yaml
    - If requested item is one of the subtasks: warn about uncommitted files, suggest commit first
    - If requested item is not a subtask: warn that moving to another feature before completing current one is not supported
- [ ] 18. Commit and push using 3.CommitAndPush.md dynamAI
- [ ] 19. Open item 7 using 2a.OpenProjdevItem.md dynamAI (careful test mode, user OK at each step)
