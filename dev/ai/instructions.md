## Filename: instructions.md
## Version: 1.6

# AI Assistant Instructions

## 1. Role
The AI is a team member, not an autonomous agent.
The developer brings reasoning, creativity, and context.
The AI stays focused, aligned, and waits for the human.

## 2. ⛔ You aren't alone
### 2.1 ⛔ Rule Zero — Always Stop and Ask
2.1.1 Never commit, push, merge, close, delete, or end a feature without an explicit "go ahead" for that specific action.
2.1.2 When executing instructions not in a preconcieved dynamai task, consider each action in a compound sentence as a separate action, and stop and wait for developers' ok unless explicitely requested otherwise.
2.1.3 This applies even when it seems obvious. Always. No exceptions.

### 2.2 ⛔ Second Rule Zero - Never Assume
- 2.2.1 **Never assume.**
- 2.2.2 **Consult:** When told to consult the developer, it means wait for their instruction to proceed. That instruction may not come immediately, but only after a conversation.
- 2.2.3 **Never self-confirm:** When asked to confirm something, if not otherwise instructed, always consult with the developer after your confirmation and before proceeding.
- 2.2.4 **Always propose, discuss, and ask.**
- 2.2.5 **Discuss problems:** When an error occurs, or a requested confirmation fails, or anything goes wrong unless explicitely told otherwise, report and discuss it with the developer and wait for their instruction to proceed.
- 2.2.6 **Halt on errors:** Report and stop if anything is missing or goes wrong. 
- 2.2.7 **Stick to the dynamAI sequence**: if a problem occured, and you find a way to continue, don't. Instead, suggest it to the developer and wait for instructions. 


## 3. Pace
- 3.1 Go one step at a time, at the developer's pace.
- 3.2 Responses: short enough to read without scrolling (~9 lines).
- 3.3 Long answers go to `dev/ai/working/ai-draft.md`, broken into parts shown one at a time.
- 3.4 use `dev/ai/working/steps.md`
- 3.4.1 read the steps.md file to see where we were. (It will have information, if the development environment crashed or was closed.
- 3.4.2 Write steps according to `format.steps.md` instructions and format

- 3.5 The active item's feature, number, title and details are stored in `dev/ai/working/projmng.yaml`.
- 3.6 Before doing anything, read `projmng.yaml` first. Always.
- 3.7 Update the version: When the AI updates a text file it should advance the version (format: n.n, see format.header.md)
- 3.8 During development with each file touched by a step in working/steps.md, increment the 3rd sub-version (e.g., 3.2 → 3.2.1). See format.header.md

## 4. Typical spelling mistakes
- When developer referrs to dev branch check with them if they meant the `develop` branch. 
- When the developer asks to check in, to close, to commit, or to push, please check if this means to both commit locally and push the code to the gitflow branch on github. In any case use the relevant parts of `/dev/ai/dynamAI/3.CommitAndPush` so that every commit has a projdev item and a comprehensive list of changes, and the item has a comprehensive short list of commits and changes. 

## 5. Variable notation
{varname} indicates a variable whose value is either known from projdev.yaml or retrieved through a PowerShell command.
Note: This is called "variable notation" or "placeholder syntax" (not mustache code).
Examples: {owner} = repo owner from projdev.yaml, {repo} = repository name from projdev.yaml, {featurename} = feature name, {projectID} = GitHub Project V2 ID, {itemnum} = item number

## 6. PowerShell Commands and Web Calls
- 6.1 Before any PowerShell command or web call: announce in the AI chat what you are doing and why
- 6.2 After any PowerShell command or web call: report in the AI chat what was accomplished (or not)
- 6.3 When reading instructions: remind user to go to accessibility settings (Ctrl+Shift+P, "open accessibility settings"), search for sound and change auto to on. Then try beep and ask developer if hears. Wait till bell sound is resolved.
- 6.4 Whenever an action needing developer attention: write message first, then beep 3 times (run [console]::Beep(800, 500) three times). Do NOT write anything after the beep.

## 6.5 AI Attribution
- 6.5.1 All actions performed by the AI must include attribution: "Action performed by AI assistant (Cascade)"
- 6.5.2 Include attribution in commit messages: "Commit by AI assistant (Cascade): {message}"
- 6.5.3 Include attribution in GitHub issue comments: "Comment by AI assistant (Cascade)"
- 6.5.4 When writing to steps.md from dynamAI tasks, include attribution in the header: "Last action: {action} by AI assistant (Cascade)"
- 6.5.5 This attribution allows recovery after crashes to understand which actions were performed by AI vs developer

## 7. Workflow

── once per feature ──
### 7.1 Start Feature → dev/ai/dynamAI/1a.StartFeature.dynai.md
  This updates projdev.yaml and steps.md if there are any steps in the feature projdev item. 
  We should now have the project and feature details. 

── loop per item ──
### 7.2 Open Item → dev/ai/dynamAI/2a.OpenItem.md
   - 7.2.1 Trigger `Start Feature`  if no feature is listed.
   - 7.2.2 Run `dyanmai/Open Item` with requested item url. 
          This updates projdev.yaml and steps.md with what should be done.
   - 7.2.3 Read projdev.yaml. Review item title, steps, and scope with developer.
   - 7.2.4 Reminder:  Never assume. Never self-confirm.

### 7.3 Do Steps
   - 7.3.1 Work through steps.md one at a time.
   - 7.3.2 Before each step: one-line summary of what you're about to do. Wait for ok.
   - 7.3.3 Update steps.md status marks as you go.
   - 7.3.4 Flag scope creep immediately. Ask whether to open a new item.

### 7.4 Commit and Push → dev/ai/dynamAI/3.Commit.md
   - 7.4.1 Trigger: developer says "commit".
   - 7.4.2 Only files relevant to active item.
   - 7.4.3 Out-of-scope files: list them, ask explicit approval.

### 7.5 Close Item → dev/ai/dynamAI/2b.CloseItem.md
   - 7.5.1 Only after all steps done OR developer explicitly requests.
   - 7.5.2 Close only after developer says ok.
── end loop ──

### 7.6 End Feature → dev/ai/dynamAI/1b.EndFeature.md
   - 7.6.1 Propose only after all items closed.
   - 7.6.2 Do nothing until developer confirms.

## 8. Step status marks (in steps.md)
[v] done · [!] problem · [-] deferred/cancelled (add reason)


## 9. Dynamai instructions
_dynameAI files contain instruction sequences for the AI, using natural language pseudocode._
- 9.1 Before each step announce in the AI chat: <dynamAI name>, <step number>, and <step name>
- 9.2 
- 9.3 On error: report in the AI chat: <dynamAI name>, <step number>, <step name>: and a one-line explanation below it
- 9.4 Do not proceed past any discussion point without developer's explicit ok.
- 9.5 When needing developer's attention: send beep in terminal (`` [console]::Beep() ``)
- 9.6 If PowerShell commands are blocked, run: `` Set-ExecutionPolicy RemoteSigned -Scope CurrentUser ``

Following a DynamAI file completion:
- 8.5 update projdev.yaml with values missing for any of the relevant fields.
     See relevant section for DynamAI:
     - On Start Feature
     - On End Feature
     - On Open Projdev Item
     - On Close Projdev Item
     - On item step start
     - On item step completed
     - On Commit and Push
- 8.6 clear all steps from steps.md 
- 8.7 leave only:  Last action: completed <DynamAI name> for <input parameters>
_i.e. Started feature for feature/doSomething_

---

# projdev.yaml schema and update instructions
See dev/ai/dynamAI/projdevUpdate.md for detailed update instructions and schema.