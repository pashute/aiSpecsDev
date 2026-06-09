## Filename: itemComment.md
## Version: 1.3.1
### Add comment to GitHub issue

### Input params
owner   - e.g. pashute
repo    - e.g. aiSpecsDev
itemNum - issue number
comment - comment text (single line or herestring format)

### Output format
JSON object with:
- success: true/false
- message: description of result or error
- commentUrl: URL of the created comment (if successful)

### Errors
- Invalid item number/repo/owner: HTTP 404 Not Found
- Comment creation failed

### Confirmed code for ai to use

```powershell
# Add comment to issue
$commentBody = @"
$comment
"@

$response = gh api repos/{owner}/{repo}/issues/{itemNum}/comments --raw-field body="$commentBody"

$result = @{
  success = $?
  message = if ($?) { "Comment added successfully" } else { "Failed to add comment" }
  commentUrl = if ($?) { $response.html_url } else { $null }
}

$result | ConvertTo-Json
```
