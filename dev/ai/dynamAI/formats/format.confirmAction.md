## Filename: format.confirmAction.md
**Version:** 1.0

# Confirmation Action Format

When asking the developer for confirmation to proceed with an action:

1. Beep 3 times: `[console]::Beep(800, 500)` three times
2. Display the confirmation message with:
   - Action being requested (e.g., "Start Feature {number}.{name} requested")
   - Relevant details (e.g., markdown item list with url links)
   - Question: "Proceed?"
3. Wait for developer approval
4. DO NOT PROCEED WITHOUT DEVELOPER'S OK

## Confirmation Message Structure

The confirmation message should include:
- 3 beeps
- Context-specific information (feature number.name, item list, etc.)
- Clear question asking for approval
- Reference to this format if needed

## Second Confirmation (after details shown)

For actions that have a second confirmation (after showing details):
- No assurance section needed
- Show the details
- Ask for final approval
- DO NOT PROCEED WITHOUT DEVELOPER'S OK
