## Filename: subItemsClosed.md
## Version: 1.0
### Verify all subitems are closed and in Done stage

### Input params
subtasks - array of subtask objects from projdev.yaml active_item.subtasks
Each subtask has: id, title, state, stage, url, milestone, date

### Output format
JSON object with:
- allClosed: true/false
- incompleteSubtasks: array of subtask objects that are not closed or not in Done stage
- message: description of result

### Errors
- Invalid subtasks array format

### Confirmed code for ai to use

```powershell
# Verify all subtasks are closed and in Done stage
$incompleteSubtasks = @()
foreach ($subtask in $subtasks) {
  if ($subtask.state -ne "closed" -or $subtask.stage -ne "Done") {
    $incompleteSubtasks += $subtask
  }
}

$result = @{
  allClosed = ($incompleteSubtasks.Count -eq 0)
  incompleteSubtasks = $incompleteSubtasks
  message = if ($incompleteSubtasks.Count -eq 0) { "All subtasks are closed and in Done stage" } 
            else { "$($incompleteSubtasks.Count) subtask(s) not closed or not in Done stage" }
}

$result | ConvertTo-Json
```
