## Filename: itemClose.md
## Version: 1.0.1
### Close GitHub issue: move stage to done, add comment, close with reason

### Input params
owner   - e.g. pashute
repo    - e.g. aiSpecsDev
itemNum - issue number
comment - multiline comment in herestring format
reason  - close reason: "completed", "not planned", or "duplicate"
dupItemNum - (optional for duplicate) duplicate issue number

### Output format
JSON object with:
- success: true/false
- message: description of result or error

### Errors
- Invalid item number/repo/owner: HTTP 404 Not Found
- Invalid reason value
- Comment creation failed
- Close operation failed

### Confirmed code for ai to use

```powershell
# Step 1: Move workflow stage to "done" using itemStage.md setter
# Call aiCode/itemStage.md with stage="done"

# Step 2: Add comment to issue
$commentBody = @"
$comment
"@

gh api repos/{owner}/{repo}/issues/{itemNum}/comments --raw-field body="$commentBody"

# Step 3: Close issue with reason
if ($reason -eq "duplicate") {
  gh api -X PATCH repos/{owner}/{repo}/issues/{itemNum} -f state=closed -f state_reason=$reason -f duplicate_of={dupItemNum}
} else {
  gh api -X PATCH repos/{owner}/{repo}/issues/{itemNum} -f state=closed -f state_reason=$reason
}

$result = @{
  success = $?
  message = if ($?) { "Item closed successfully" } else { "Failed to close item" }
}

$result | ConvertTo-Json
```
