## Filename: format.steps.md
**Version:** 1.0

# Format
```
## Filename: steps.md
**Version:** n.n[.n]

Reader: [-] deferred, [x] cancelled, [V] no need, [v] done, [=] duplicate, [!] discuss

- DO NOT MARK AS DONE until an explicit done received from the developer.
- DO NOT MOVE TO A NEXT STEP without the developer saying next
- When clearing the file, leave these lines up to the header `# "Steps for AI"` (including that line)

# Steps for AI:
- [ ] 1. {step name}: **{step description}**
- [ ] 1.1 {substep name}: **{substep description}**
- [ ] 2. {n}.{itemNickname} step #{m}. **{item-stepName}: {description}**
```

# Instructions
These are instructions for recording steps in `working/steps.md`:

1. **DynamAI self details**.** Step 1 of each DynamAI is to record its own details. 
See `format.dynamAI.md` for 1st step instructions. 

2. **Step recording:**  
2.1 **Project management item steps:** Record all planned steps from current item (on opening item)

2.2 **DynamAI steps:** Record all planned steps from the current DynamAI you are running (on starting the dynamAI task)

2.3 **Developer or AI initiated steps:** Record steps inserted into workflow during the discussion.

2.4 **Telegraphic:** Keep the steps discription  telegraphic.

2.5 **Format** as can be seen in the format section: A bulleted checkbox with an index number and a title. 

2.6 **Step type** For a Project management item or DynamAI clearly mark:
  - `{n}.{itemNickname} step #m. Do that` or 
  - `{dynameAI name} step #m. Do the other.`
  - use a nickname to make the project management item shorter. 