## Filename: hereString.frmt.md
## Version: 1.0

### PowerShell here-string format
- Enclosed in @" "@
- @" at beginning of line
- Open sign @" at end of line, no trailing spaces after the double quotemark
- Close sign "@ at beginning of last extra line:
  - No preceding spaces or text
  - No trailing spaces or text after @

### Example
```
@"
line 1
line 2
line 3
"@
```
