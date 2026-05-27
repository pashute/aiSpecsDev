## Filename: projectSame.md
## Version: 1.0
### Check if requested project matches stored project

### Input params
requested_owner - e.g. pashute
requested_repo  - e.g. aiSpecsDev

### Output format
Boolean: true if project matches, false if different

### Errors
- projdev.yaml not found or malformed

### Confirmed code for ai to use

```powershell
# AI instruction: Read projdev.yaml and compare project.owner and project.repo
# with requested_owner and requested_repo
# Return true if both match, false otherwise
```
