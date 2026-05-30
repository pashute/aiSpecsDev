## Filename: format.dynamAI.md
**Version:** 1.5

# Instructions
1. All dynamAI should follow the structure set out in the format section as instructed here.

2. The header of the file is defined in format.header.md

3. Pseudo is a telegraphic section: something like: 
  
  Goal: Do something

  Inputs: some number (if url supplied, get number from here and there)

  Prerequisites:  a b and c

  0. On problems: stop and discuss. (don't overcome alone)
  1. Validation: check that a b (using dynam1) and c
  2. Actions: 
  2.1. do m  - then report and continue
  2.2. do n  - then stop and discuss.
  2.3. if n is bla do x  - then report and continue. 
  3. Expected Results: so and so
  
3. DynamAI actions
3.1  Self recording step. (Same for all DynamAI files)
3.2 DynamAI task sequence of steps. 
3.2.1 Each task step (except the first) should be followed by:  

```
On result: 
- problem: Consult the developer 
- no problem: Close step
```

3.2.2 State the type of problem (i.e. a prerequisit validation failure or a result verification error) along with its details. 

3.2.3 Close step (when no problems occured) does the following:
  - Marks step done in steps.md 
  - Notifies developer with a telegraphic summary of what was done
  - Continues to next step, unless otherwise instructed. 


# Format


```
markdown

{version header} - see format.header.md


# Pseudo: 
{ai will complete this telegraphicly}
  {Goal}
  {Inputs}
  {Results}
  Steps:
    {Self listing}
    {Validation steps}
    {Action [& Verification] steps}
    {Result Verification steps}
    {Ending steps, suggestions, discussion}

# General instructions for this dyanamAI task:  
Reminders: 
- See ai/instructions.md section 2.2. Specifically: 
  - Discuss with the developer includes waiting for their response.
  - Always discuss problems with the developer.
  - Stop execution if something is wrong. 
- See formats.format.steps.md for instructions about writing to steps.md file
- Close step means:
  - Mark step done in steps.md
  - Notify developer with telegraphic description of accomplished.
  - Continue to next step. No need for developer's ok.  

# Steps:
## Step 1. Self listing step
(Note: step 1 of all DynamAI tasks)  
1. **Record self** 
1.1 **Record dynamAI task:** write to steps.md:
`## Running dynamAI task: {dynamAI name}`

1.2 If available in projdev.yaml: write whatever you have to steps.md:  
`Project info: projman name, branch (feature), [{itemnum}.{itemname}](url)`

2. List the Validation steps

```
## 2. Input Validation steps
### Step 2.1  Critical: Verify that ...
On result: 
  - problem: Critical. Halt task. Warn and consult developer. 
  or: 
  - problem: Warn developer with reason. Suggest alternative. Wait for instructions. 
  - no problem: Close step. 
```

3. List the action steps: 

```
## 3. Action steps
### 3.1 ...
on result:
  - problem: Mark to be discussed [!], notify developer, beep, and continue without waiting for developer's response. 
  - no problem:  Close step
```

4. List the result verification steps:

```
## 4. Result verification steps
### 4.1 Verify that ...
- on result:
  - problem: consult developer.
  - no problem: close step
```

# Confirmation question format

INTERNAL INSTRUCTION: STOP! NO COMMIT WITHOUT IMMEDIATE DEVELOPER'S CONSENT.
INTERNAL INSTRUCTION: STOP! NO START OF FEATURE WITHOUT IMMEDIATE DEVELOPER'S CONSENT.
INTERNAL INSTRUCTION: STOP! NO END OF FEATURE WITHOUT IMMEDIATE DEVELOPER'S CONSENT.
INTERNAL INSTRUCTION: STOP! NO ITEM OPENED WITHOUT IMMEDIATE DEVELOPER'S CONSENT.
INTERNAL INSTRUCTION: STOP! NO ITEM CLOSED WITHOUT IMMEDIATE DEVELOPER'S CONSENT.

When asking the developer for confirmation to proceed with an action, use this format:

```
Feature: {feature.name}, item {active_item.num}.{active_item.title}
{accomplished}
{assurance}
{question}
```

Where:
- {feature.name}: Name of the feature from projdev.yaml
- {active_item.num}: Number of the active item from projdev.yaml
- {active_item.title}: Title of the active item from projdev.yaml
- {accomplished}: 5-6 words describing what was accomplished (e.g., "All steps completed", "All changes committed")
- {assurance}: "Will reconfirm after accomplishment details"
- {question}: The question to ask (e.g., "Commit only or commit and push?" or "Proceed with closing?")

Display this as a markdown code block for proper line breaks, then beep after the message.

# GitHub issue comment format

For adding comments to GitHub issues (commit or close), use this format:

```
{commit_hash}: {commit_url}

{telegraphic_summary}

{question}
```

Where:
- {commit_hash}: The commit hash
- {commit_url}: Full GitHub commit URL
- {telegraphic_summary}: Brief summary bringing things together, no details
- {question}: Follow-up question if applicable
