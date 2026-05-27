# AI assisted development using Github Project V2

Feature and subtask based development with Copilot
A template to add to any Visual Studio project running with a powershell terminal

## AI instructions and dyanamic code

- Instructions file:  `/dev/ai/instructions.md` file.
- The copilot becomes a team member with the developer.
- The developer supplies the feature, its items and each items steps. 
- The copilot discusses and develops the project: 
  - reads the development feature, its items and steps,  
  - assesses and suggests 
  - develops step by step, constantly consulting the developer between steps. 
- The copilot keeps track using 
  - Internal Steps.md file     - telegraphic plan and traced execution.
  - Internal projdev.yaml file - for project development parameters
  - Git:  Structured telgraphic commit comments (accomplished, file changes, problems)
  - GitFlow:  commiting pushing and branching with the GitFlow pradigm of development 
  - Github project: Structured closing comments. Ticked step lists. 

### Features items and tasks
- Each feature is a parent issue in Github Project V2.
- The feature has items - subissues in Github Project V2.
- Each item has tasks - a checkbox list of todo items, in the main description, and in comments.
- An item may have sub-items. 

##  Sample project

This repo includes a sample simple html js and css under src folder.
A dev folder for all things dev.

- `/dev/docs` folder and in it `devplan.md`, `specs.md` of the mock project
- `/dev/ai` - the main part of this project - where all ai instructions and assisting files go
  - `instructions.md` - the main instruction file
  - `projdev.yaml` - place where projdev information is stored
  - `aitemp.md` - file for ai to store vars and other stuff
  - `dynai` - folder under ai with specific dynamai (dynamic ai) instructions.
    These files are computer program flowcharts with common project-development specific tasks like
    gitflow feature opening and closing, following projdev items (GH project issues) iterations and milestones.

Every doc opens with `Document name:` and then `Version:` starting at 0.90
