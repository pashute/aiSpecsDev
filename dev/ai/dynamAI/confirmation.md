## Filename: confirmation.md
## Version: 1.0

# Confirmation with Critical Halt

## CRITICAL HALT INSTRUCTION:
1. Display confirmation question using format from format.dynamAI.md "Confirmation question format"
2. Beep 3 times (run [console]::Beep(800, 500) three times)
3. STOP. DO NOT PROCEED.
4. Wait for user to type approval (yes, go ahead, proceed, or similar)
5. Only after user explicitly approves, then proceed
6. If user says anything else or nothing, remain halted

## Input params
- {accomplished}: 5-6 words describing what was accomplished (e.g., "All steps completed", "All changes committed")
- {assurance}: "Will reconfirm after accomplishment details" (for first confirmation) or "Actions listed above" (for second confirmation)
- {question}: The question to ask (e.g., "Commit only or commit and push?" or "Proceed with closing?")

## Output format
User approval or disapproval

## Errors
- No explicit approval received: HALT and wait

## First confirmation (before any action)
Use this for initial confirmation before starting an action.

## Second confirmation (after details shown)
Use this after showing details to the user, before executing the action.
- In 1b.EndFeature.md: after showing feature details and action summary
- In 2b.CloseProjdevItem.md: after showing steps.md, active_item details, and commit log
- In 3.CommitAndPush.md: after showing completion table, commit message, and file list
