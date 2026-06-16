## Filename: projdev.frmt.md
## Version: 1.5
### Schema for projmng.yaml
project:  
  owner, repo

projman:  # project management details (Github Project)
  num, name, uid, url

feature:
  name, version, branch
  item:
    num, title, state, stage, url, milestone: {number, title, due}

active_item:   # same as feature item, if no subitem was chosen
  num, title, state, stage, url, milestone: {number, title, due}, item_uid
  subtasks:
    - num, title, state, stage, url, milestone: {number, title, due}

parent_item:     # empty if the active item is the feature item itself
  num, title, state, stage, url, milestone: {number, title, due}, steps_progress

commits:
  - hash, headline     # hash is the commit hash
    details          # multiline free-text block (array of telegraphic description lines)
    filechanges      # comma-separated list of changed filenames

completed_items:
  - num, title, status, remarks, has_open_subitems
  # IMPORTANT: Only include items that are done or deferred
  # has_open_subitems: true if item closed but still has open subitems (partial close)

