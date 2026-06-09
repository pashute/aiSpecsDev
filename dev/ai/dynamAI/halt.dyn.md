Filename: halt.dyn.md
Version: 0.9

This procedure is called when a critical error was encountered during a DynamAI action. (start/end feature, open/close item, commit and push)

# input
- {dynamAI} - action (number and name): 1a. startFeature
- {step} - action step (number and name): 3. set stage in progress
- {error} - error message
- {fix suggestion} - suggested fix
- {next steps} - missing steps to complete the action

## CRITICAL HALT INSTRUCTIONS:
1. Report internally and externally
1.1 Internal report (steps.md): Mark step with [!] and telegraphic error and fix info. 
1.2 External report (item comment): In GH Project add a comment to the current item (itemComment.ai.md). Use report line from steps.md

2. Notify:
2.1 Beep 3 times (run [console]::Beep(800, 500) three times)
2.2 In chat notify developer: error, fix suggestion, missing steps
2.3 Wait for developer's instructions
2.4 If developer asks further question, discuss but don't change files until an explicit developer's ok. 