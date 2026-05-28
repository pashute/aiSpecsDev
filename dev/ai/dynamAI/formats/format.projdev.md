## Filename: format.projdev.md
## Version: 1.0
### Schema for projdev.yaml
project:  
  owner, repo

projman:  # project management details (Github Project)
  id, name, uid, url   # id is project number, not the uid

feature:
  name, branch
  item:
    id, title, state, stage, url, milestone, date     # id is the feature item issue number, not the uid

active_item:   # same as feature item, if no subitem was chosen
  id, title, state, stage, url, milestone, date
  subtasks:
    - id, title, state, stage, url, milestone, date

parent_item:     # empty if the active item is the feature item itself
  id, title, state, stage, url, milestone, date

commits:
  - id, headline     # id is the commit hash
    details          # multiline free-text block (array of telegraphic description lines)
    filechanges
      - filename, path
        changes    # multiline free-text block (array of telegraphic change descriptions)

