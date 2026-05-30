## Filename: ai-draft.md
## Version: 0.91
# A file for the AI to do whatever it wants. Do not erase this line

# Backup of projdev.yaml commits list (saved before yaml update)
commits_backup:
  - hash: f85227e
    headline: Add GitHub issue comment format to CommitAndPush
    details:
      - Updated comment step to use GitHub issue comment format from format.dynamAI.md
      - Added telegraphic summary and question to comment format
    filechanges: 3.CommitAndPush.md
  - hash: e34099f
    headline: Add confirmation question format to all dynamAI files
    details:
      - Added confirmation question format to format.dynamAI.md
      - Updated all dynamAI files (1a, 2a, 1b, 2b, 3) to reference format
      - Renamed 1b.EndFeature.dynai.md to 1b.EndFeature.md
      - Updated versions to 0.1.6
    filechanges: format.dynamAI.md, 1a.StartFeature.md, 2a.OpenProjdevItem.md, 1b.EndFeature.md, 2b.CloseProjdevItem.md, 3.CommitAndPush.md, steps.md
  - hash: 1a1d898
    headline: Fix commitAndPush message formatting
    details:
      - Formatted verification message with proper markdown code block for better readability
      - Ensures message displays on separate lines for developer
    filechanges: 3.CommitAndPush.md, steps.md
  - hash: c1c4e22
    headline: feature/WriteSomeSpecs dynamAI refinements and bug fixes
    details:
      - Fixed GraphQL fragment spread in itemStage.md getter
      - Simplified itemStage.md setter using cached stage UIDs
      - Added verification step to 2b.CloseProjdevItem.md
      - Improved 3.CommitAndPush.md user prompt formatting
      - Updated instructions.md to write message before beep
    filechanges: 2b.CloseProjdevItem.md, 3.CommitAndPush.md, aiCode/itemStage.md, instructions.md, steps.md
  - hash: 43bfa98
    headline: feature/WriteSomeSpecs dynamAI workflow refactoring
    details:
      - Standardized all dynamAI task files to format.dynamAI.md structure
      - Added per-step problem handling with On result blocks
      - Pseudo section provides quick overview of each task
      - Instruction pointers to shared code and formatting files
      - Standardized projdev info in yaml
      - Moved steps.md and projdev.yaml to working/ folder
      - Added vanilla/ folder for template files
      - Fixed API errors in aiCode files for proper AI execution
      - Implemented two-phase commit (work files, then metadata)
      - Added metadata-only commit detection in all dynamAI tasks
    filechanges: 1a.StartFeature.md, 1b.EndFeature.dynai.md, 2a.OpenProjdevItem.md, 2b.CloseProjdevItem.md, 3.CommitAndPush.md, steps.md, instructions.md, formats/format.dynamAI.md, formats/format.header.md, formats/format.steps.md
  - hash: 89f62ad
    headline: feature/WriteSomeSpecs working folder and dynamAI refinements
    details:
      - Created dev/ai/working/ folder for active files
      - Moved projdev.yaml, steps.md to working/
      - Updated all file references to point to working/
      - Removed unwanted "Project development data at current stage" line
      - Standardized headers to "## Filename:" and "## Version:" format
      - Enhanced variable notation section with placeholder syntax note
      - Added subsection numbers to projdevUpdate.md
      - Simplified dynamAI files to reference projdevUpdate.md
    filechanges: 1a.StartFeature.md, 1b.EndFeature.dynai.md, 2a.OpenProjdevItem.md, 2b.CloseProjdevItem.md, 3.CommitAndPush.md, projdevUpdate.md, instructions.md, vanilla/ai-draft.md, working/, ai-draft.md, projdev.yaml, steps.md
  - id: b7c67ba
    headline: feature/WriteSomeSpecs instruction refinements
    details:
      - user guide, detailed instructions with verifications tested
    filechanges: README.md, instructions.md, 1a.StartFeature.md, 2a.OpenProjdevItem.md, 2b.CloseProjdevItem.md, projdev.yaml, steps.md, temp.txt
  - hash: 2889cc2
    headline: feature/WriteSomeSpecs bell and accessibility improvements
    details:
      - "Added bell sound accessibility instructions"
      - "Added 3-beep attention notification"
      - "Updated commit dynamAI with format refactoring"
      - "Created format files for commit/item/project"
      - "Created aiCode files for item operations"
      - "Cleaned up redundant schema files"
    filechanges: instructions.md, steps.md, 3.CommitAndPush.md, projdevUpdate.md, format.commit.md, format.itemClose.md, format.projdev.md, itemClose.md, itemParams.md, itemState.md, subItemsClosed.md, item.md
  - id: 62a3271
    headline: feature/WriteSomeSpecs commit instruction refactoring
    details:
      - "Fixed format.projdev.md to clarify array structure"
      - "Simplified projdevUpdate.md to reference format.projdev.md"
      - "Eliminated redundancy between format and instructions"
    filechanges: format.projdev.md, projdevUpdate.md
  - id: ceac471
    headline: feature/WriteSomeSpecs add here-string format and dynamAI terminology
    details:
      - "Created format.hereString.md with PowerShell here-string format specification"
      - "Updated 2b.CloseProjdevItem.md to reference format.hereString.md"
      - "Updated README.md to use dynamAI tasks terminology"
      - "Updated all dynamAI files below 1.0 to version 1.0"
      - "Cleaned up steps.md after previous commit"
    filechanges: format.hereString.md, 2b.CloseProjdevItem.md, README.md, steps.md
  - hash: 87069ed
    headline: feature/WriteSomeSpecs add completion table and project item comment to commit dynamAI
    details:
      - "Added checkbox step parsing to 2a.OpenProjdevItem.md"
      - "Added checkbox step parsing to 1a.StartFeature.md"
      - "Updated format.commit.md to include itemsteps field"
      - "Added completion table step to 3.CommitAndPush.md"
      - "Added project item comment step to 3.CommitAndPush.md"
      - "Updated developer confirmations in 3.CommitAndPush.md"
    filechanges: 2a.OpenProjdevItem.md, 1a.StartFeature.md, format.commit.md, 3.CommitAndPush.md

