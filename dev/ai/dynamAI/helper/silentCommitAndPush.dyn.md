## Filename: silentCommitAndPush.dyn.md
**Version:** 1.0

# Pseudo:
Goal: Silent second phase commit and push of metadata files (projmng.yaml, steps.md)

Inputs: None (uses calling dynamAI task context)

Prerequisites:
- Called from another dynamAI task after main action completed
- Only metadata files should be changed (projmng.yaml, steps.md)
- On problems NOTIFY, HALT, and CONSULT

Verifications:
- Verify only projmng.yaml and steps.md are modified

Steps:
- Verify only metadata files are changed
- Commit metadata files
- Push to origin
- Verify commit and push succeeded
- On failure: attempt comment to GitHub item, notify developer, beep and say ended

Results:
- Metadata files committed and pushed
- Or: failure notification sent to developer

Error handling:
- On commit/push failure: do NOT halt, attempt comment to GitHub item with error details
- Notify developer with originating dynamAI task and step
- Beep and say "ended" with success or error message

# General instructions for this dynamAI task:
Reminders:
- See ai/instructions.dyn.md section 2.2. Specifically:
  - Discuss with the developer includes waiting for their response.
  - Stop execution if something is wrong.
  - On error NOTIFY, HALT, and CONSULT according to `halt.dyn.md`

- See formats/steps.frmt.md for instructions about writing to steps.md file

- See formats/steps.frmt.md for instructions to close a step
(steps.md, notify developer)

- This task is NOT listed in steps.md
- This task has NO developer confirmation
- This task is called by other dynamAI tasks for second phase metadata commit

# Steps:

## Input Validation steps

### Step 1.0 Record self (silent - not written to steps.md)
This step does NOT write to steps.md as this is a silent task.

### Step 1.1 Verify only metadata files changed
1.1.1 Check git status for modified files
1.1.2 Verify only projmng.yaml and steps.md are modified
1.1.3 If other files are modified:
  - Log error: "Unexpected files modified in silent commit"
  - Continue anyway (do not halt)
On result:
- problem: Log error, continue
- no problem: Continue

## Action steps

### Step 2.1 Commit metadata files
2.1.1 Stage metadata files: `git add dev/ai/working/projmng.yaml dev/ai/working/steps.md`
2.1.2 Commit with message: "Metadata update from {calling_dynamAI_task}"
2.1.3 Get commit hash
On result:
- problem: Attempt error notification, beep and say ended
- no problem: Continue

### Step 2.2 Push to origin
2.2.1 Push: `git push`
2.2.2 Verify push succeeded
On result:
- problem: Attempt error notification, beep and say ended
- no problem: Continue

## Result verification steps

### Step 3.1 Verify commit and push
3.1.1 Verify commit: `git log -1 --format="%H %s"`
3.1.2 Verify push: `git log origin/{branch}..HEAD` (should be empty if pushed)
On result:
- problem: Attempt error notification, beep and say ended
- no problem: Beep and say "done" with success message

## Error notification

### On failure
- Attempt to add comment to GitHub item (active_item or feature.item)
- Comment format: "Silent commit failed from {calling_dynamAI_task}. Error: {error_details}"
- If comment fails: log error
- Beep and say: "ended with error from {calling_dynamAI_task}"
- Do NOT halt execution of calling task
