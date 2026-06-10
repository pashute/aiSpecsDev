## Filename: projectSame.ai.md
## Version: 1.0.1
### Check if requested project matches stored project

### Input params
requested_owner - e.g. pashute
requested_repo  - e.g. aiSpecsDev

### Output format
Boolean: true if project matches, false if different

### Errors
- projmng.yaml not found or malformed

### Confirmed code for ai to use

```powershell
# AI instruction: Read projmng.yaml and compare project.owner and project.repo
# with requested_owner and requested_repo
# Return true if both match, false otherwise
```
