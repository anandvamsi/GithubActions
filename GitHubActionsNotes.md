# GitHub Actions


## Github Skeleton/tree strucuture 
```bash
.github/
  workflows/
    workflow.yml
src/
  main/
    java/
      # Java source files
    resources/
      # Resource files (e.g., configuration files)
  test/
    java/
      # Test source files
      # Test resource files
.gitignore
README.md
LICENSE

```


## ON Paramater 
The on parameter in GitHub Actions is used to define the events that ```will trigger the workflow to run```. It specifies the event that will cause the workflow to execute. The on parameter is a top-level key in the workflow file and accepts a dictionary of event types.
Here's how the on parameter works:
- You can specify one or more event types that will trigger the workflow. These event types can include different GitHub event types, such as push, pull_request, schedule, workflow_dispatch, etc.
- You can also specify filters within event types, such as the branches for push events or the types of activity (opened, synchronize, closed, etc.) for pull_request events.
- Each event type can have additional configuration options, such as specifying the branches for push events, the paths for pull_request events, or the types of activities for schedule events.

```bash
name: My Workflow

on:
  push:
    branches:
      - main
      - feature/*
  pull_request:
    types: [opened, synchronize, reopened]
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:
```

Notes::
- The workflow will run on every push to the main branch or any branch starting with feature/.
- The workflow will run on pull requests when they are opened, synchronized (updated), or reopened.
- The workflow will run on a schedule according to the specified cron expression (0 0 * * *, meaning midnight every day).
- The workflow can also be manually triggered using the GitHub UI (workflow_dispatch).
