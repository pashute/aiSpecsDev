## Filename: format.steps.md
**Version:** 0.9.1

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
See this file "DynamAI Step Format" section for 1st step instructions. 

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

# DynamAI Step Format

## Step 1. Self listing step
(Note: step 1 of all DynamAI tasks)
1. **Record self**
1.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: {dynamAI name}`

1.2 If available in projmng.yaml: write whatever you have to steps.md:
`Project info: projman name, branch (feature), [{itemnum}.{itemname}](url)`

## Input Validation steps
### Step 2.1 Critical: Verify that ...
On result:
  - problem: Critical. Halt task. Warn and consult developer.
  or:
  - problem: Warn developer with reason. Suggest alternative. Wait for instructions.
  - no problem: Close step.

## Action steps
### 3.1 ...
on result:
  - problem: Mark to be discussed [!], notify developer, beep, and continue without waiting for developer's response.
  - no problem: Close step

## Result verification steps
### 4.1 Verify that ...
- on result:
  - problem: consult developer.
  - no problem: close step

## On result pattern
Each task step (except the first) should be followed by:

```
On result:
- problem: Consult the developer
- no problem: Close step
```

State the type of problem (i.e. a prerequisite validation failure or a result verification error) along with its details.

## Close step
Close step (when no problems occurred) does the following:
- Marks step done in steps.md
- Notifies developer with a telegraphic summary of what was done, including dynamAI name and step number: "{dynamAI taskname (ie `(1a) OpenItem`)} {stepnum}.{stepname}"
- Continues to next step, unless otherwise instructed. 