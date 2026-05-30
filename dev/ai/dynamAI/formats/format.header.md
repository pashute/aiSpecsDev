## Filename: format.header.md
**Version:** 1.0

# Format 
```
## Filename: {filename}.md
**Version:** {n.n}[.n]
```

# Instructions

1. Every text file that allows a comment must have a header section with the filename and version.  (The format above is for any .md file)

2. The version format is n.n (starting with 0.1)  

3. During development with each file touched by a step in working/steps.md an extra 3rd .n will be added or incremented.  

4. During a commit and push all touched files will have the steps sub-version removed and the minor version incremented.  

5. When closing a feature the developer will be asked at the beginning of the process and decide if they wish to set all document version numbers to a  single major (and perhaps minor) value.   
