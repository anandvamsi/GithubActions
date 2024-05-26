# GitHub Actions

## what is Github Action
GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that run tests whenever you push a change to your repository, or that deploy merged pull requests to production

GitHub Actions is a powerful tool that allows developers to automate their software development workflows directly within GitHub. It provides several key advantages:

### Automation
GitHub Actions enables you to automate many tasks in your development process, such as building, testing, and deploying code. This saves time and ensures consistency.

### Customization
Actions are highly customizable - you can create your own custom actions or use pre-built actions from the GitHub Marketplace to build workflows tailored to your specific needs.

### Community
GitHub Actions has a large and active community that shares pre-built actions and provides support. The community makes it easy to find and use actions for common needs

### Cost Effeciveness 
GitHub Actions is free for public repositories and provides 2,000 free minutes per month for private repos, making it affordable for developers of all sizes

### Event-driven model
The event-driven programming model used by Actions enables workflows to be triggered by specific events like pushes, pull requests, issues, etc.


## Github workflow
Workflows are a set of automated steps that are triggered based on certain events in your GitHub repository. 
These events can include pushing code to the repository, creating pull requests, or releasing a new version. 
Workflows are defined using YAML syntax and are stored in a .github/workflows directory in your repository.
This repository can have several workflows. And each workflow can perform a different set of jobs.
For instance, you can use one workflow to create and test pull requests while another to deploy your application.

### Event
An event is a particular activity in a repository. It is like a trigger for workflows.
When events occur within a repository, GitHub Actions respond to them. These events can push requests, pull requests, or other actions.

### Jobs
Jobs are a ```set of steps in a workflow```. They are executed under the same runner. 
Each step is either a shell script or an action. Scripts execute while actions run.

### Actions
An action is an application for the GitHub Actions. It performs frequently repeated tasks. 
The application helps web developers to reduce the number of repetitive codes they write in their workflow files

### Runner
A runner is a server that runs workflows when they are triggered. 
One runner can perform a single task at a time


## A simple Github workflow
```bash
name: Hello World

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:

  hello-world:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout code
      uses: actions/checkout@v2
      
    - name: Say Hello
      run: echo "Hello, World!"
```

## Breaking down the template
1. 𝖶𝗈𝗋𝗄𝖿𝗅𝗈𝗐: 🔄 Define your workflow in a `.github/workflows` directory. Create a file, e.g., `main.yml`, to get started.
2. 𝖤𝗏𝖾𝗇𝗍𝗌: 📡 This workflow triggers on every push to the `main` branch.
3. 𝖩𝗈𝖻𝗌: 💼 The workflow contains one job named `build` that runs on the latest version of Ubuntu. Each Job can either execute commands or use Actions (Reusable scripts)
4. 𝖱𝗎𝗇𝗇𝖾𝗋𝗌: 🏃‍♂️ GitHub-hosted runner with Node.js installed. Using 𝗋𝗎𝗇𝗌-𝗈𝗇 keyword we define the runner machine OS
5. 𝖠𝖼𝗍𝗂𝗈𝗇𝗌: 🤖 Utilizes actions like `actions/checkout` to clone the repository and `actions/setup-node` to set up Node.js. Actions are like plugins in Jenkins
6. 𝖠𝗋𝗍𝗂𝖿𝖺𝖼𝗍𝗌: 🎨 In this example, the workflow installs dependencies, runs tests, and can produce artifacts for further use.
7. 𝖬𝖺𝗍𝗋𝗂𝗑 𝖡𝗎𝗂𝗅𝖽𝗌: 📊 This example focuses on a single job, but you can expand to matrix builds for parallel testing on different environment




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

## Different JOB with Github Actions

In GitHub Actions, a "job" is a unit of work defined within a workflow file. Jobs allow you to divide the work that needs to be done into smaller, independent tasks, which can run in parallel or sequentially. Here are some common types of jobs you can define in a GitHub Actions workflow:

```Build Job```: This job is responsible for building your project. It typically includes tasks such as compiling source code, generating artifacts, and running static code analysis.

```Test Job```: This job is responsible for running tests on your codebase. It includes tasks such as unit tests, integration tests, and end-to-end tests.

```Deploy Job```: This job is responsible for deploying your application or service to a specific environment, such as staging or production. It may involve tasks such as packaging your application, deploying to servers or cloud platforms, and configuring environment variables.

```Notification Job```: This job is responsible for sending notifications or alerts based on the outcome of other jobs in the workflow. It may involve tasks such as sending emails, Slack messages, or updating issue trackers.

```Cleanup Job```: This job is responsible for cleaning up resources or performing post-processing tasks after the main work of the workflow is complete. It may involve tasks such as deleting temporary files, stopping services, or triggering follow-up actions.

```Security Job```: This job is responsible for performing security-related tasks, such as scanning your codebase for vulnerabilities, running security tests, or enforcing security policies.

```Documentation Job```: This job is responsible for generating and publishing documentation for your project. It may involve tasks such as building documentation from source files, generating API documentation, and publishing documentation to a website or documentation platform.

These are just a few examples of the types of jobs you can define in a GitHub Actions workflow. You can customize your workflow to include any combination of these jobs based on your project's specific requirements. Additionally, you can define multiple jobs within a single workflow file to orchestrate complex workflows involving multiple steps and dependencies.
