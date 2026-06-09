## Filename: confirmAction.dyn.md
## Version: 1.1

# Critical Action Confirmation Procedure
DO NOT SKIP THIS PROCEDURE.
DO NOT ASSUME A PREVIOUS OK IS VALID FOR THIS ONE
SOME ACTIONS HAVE TWO CONFIRMATIONS. THE OK FOR ONE IS NOT AN OK FOR THE NEXT.

## Procedure
1. Beep 3 times: `[console]::Beep(800, 500)` three times
2. Display the confirmation message provided by the calling .dyn file
3. Wait for user approval (yes, go ahead, proceed, or similar)
4. Only after user explicitly approves, then proceed
5. If user says anything else or nothing, remain halted

## Notes
- The calling .dyn file builds and provides the actual confirmation message
- This procedure handles beep, display, and waiting for approval
- No output or error handling in this procedure
- See format.confirmAction.md for message structure guidelines
