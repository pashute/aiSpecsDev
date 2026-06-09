## Filename: confirmAction.dyn.md
## Version: 1.0.1

# Critical Action Confirmation Procedure
DO NOT SKIP THIS PROCEDURE. 
DO NOT ASSUME A PREVIOUS OK IS VALID FOR THIS ONE
SOME ACTIONS HAVE TWO CONFIRMATIONS. THE OK FOR ONE IS NOT AN OK FOR THE NEXT. 

## Notify user confirmation is needed
1. Notify:
1.1 Beep 3 times (run [console]::Beep(800, 500) three times)
1.2 Display confirmation question using format from format.dynamAI.md "Confirmation question format"

2. Consult:
2.1 STOP. DO NOT PROCEED.
2.2. Wait for user to type approval (yes, go ahead, proceed, or similar)
2.3. Only after user explicitly approves, then proceed
2.4. If user says anything else or nothing, remain halted

## Input params
- {accomplished}: 5-6 words describing what was accomplished (e.g., "All steps completed", "All changes committed")
- {assurance}: "Will reconfirm after accomplishment details" (for first confirmation) or "Actions listed above" (for second confirmation)
- {question}: The question to ask (e.g., "Commit only or commit and push?" or "Proceed with closing?")

# Notes

## NO OUTPUT OR ERROR HANDLING
This procedure has no output or error handling

## First confirmation (before any action)
This procedure is called at the beginning of all actions:
1aStartFeature, 1bEndFeature, 2aOpenItem 2bCloseItem, 3CommitAndPush


## Second confirmation (after details shown)
This procedure is called after showing details to the user, before executing the action.
- In 1b.EndFeature.md: after showing feature details and action summary
- In 2b.CloseProjdevItem.md: after showing steps.md, active_item details, and commit log
- In 3.CommitAndPush.md: after showing completion table, commit message, and file list
