## Filename: isFeatureItem.md
## Version: 1.0.1
### Verify issue is suitable as a feature item

### Input params
owner  - e.g. pashute
repo   - e.g. aiSpecsDev
number - item number (Github Project V2 issue) e.g. 2

### Output format
JSON object with:
- valid: true/false
- errors: array of error messages (empty if valid)
- hasFeatureName: true/false
- hasParent: true/false

### Errors
- Invalid item number/repo/owner: HTTP 404 Not Found
- Issue has parent: not suitable as feature item
- Issue lacks feature name format: title should start with "feature/"

### Confirmed code for ai to use

```powershell
# Check if issue is suitable as feature item
$issue = gh api repos/{owner}/{repo}/issues/{number}

# Check 1: Has feature name format (title starts with "feature/")
$hasFeatureName = $issue.title -like "feature/*"

# Check 2: Has no parent
$parentNumber = gh api graphql -f query='query($owner:String!, $name:String!, $number:Int!) { repository(owner:$owner, name:$name) { issue(number:$number) { parent { number } } } }' -F owner={owner} -F name={repo} -F number={number} --jq '.data.repository.issue.parent.number'
$hasParent = $parentNumber -ne $null

# Build result
$errors = @()
if (-not $hasFeatureName) { $errors += "Issue title does not start with 'feature/'" }
if ($hasParent) { $errors += "Issue has a parent (sub-issue), not suitable as feature item" }

$result = @{
  valid = ($errors.Count -eq 0)
  errors = $errors
  hasFeatureName = $hasFeatureName
  hasParent = $hasParent
}

$result | ConvertTo-Json
```
