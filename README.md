# GitHub Daily Contribution Automation

An automated GitHub Actions workflow that runs once every 24 hours, updates a repository maintenance file, and pushes a commit automatically.

## Overview

This project uses **GitHub Actions** to automate a daily repository update without requiring your computer to stay powered on.

Once configured, GitHub handles the entire process in the cloud.

## How It Works

The workflow follows this sequence:

1. **Scheduled Trigger** — GitHub Actions starts the workflow every day at 00:00 UTC.
2. **Repository Checkout** — The latest repository version is downloaded into the runner.
3. **Git Configuration** — Git is configured with the GitHub Actions bot identity.
4. **File Update** — The workflow updates `.github/daily-update.txt` with the current UTC timestamp.
5. **Commit Creation** — Git creates a commit containing the updated file.
6. **Push to GitHub** — The new commit is pushed to the repository.

## Workflow Architecture

```text
       GitHub Actions Scheduler
                 |
                 v
          Daily Trigger
                 |
                 v
        Checkout Repository
                 |
                 v
          Configure Git
                 |
                 v
        Update Maintenance File
                 |
                 v
          Create Commit
                 |
                 v
          Push to GitHub
                 |
                 v
         Repository Updated
```

## Schedule

| Configuration | Value |
|---|---|
| Execution frequency | Every 24 hours |
| Cron expression | `0 0 * * *` |
| UTC execution time | 00:00 |
| Pakistan time | 05:00 AM |
| Execution environment | Ubuntu Latest |
| Automation platform | GitHub Actions |
| Manual execution | Supported |

**Note:** GitHub scheduled workflows use UTC and may experience execution delays during periods of high platform load.

## Project Structure

```text
repository/
│
└── .github/
    ├── workflows/
    │   └── daily-contribution.yml
    │
    └── daily-update.txt
```

## Installation

### 1. Create the workflow

Create the following file:

`.github/workflows/daily-contribution.yml`

Add the workflow configuration.

### 2. Configure permissions

Navigate to:

`Repository → Settings → Actions → General`

Under Workflow permissions, select:

**Read and write permissions**

Save your changes.

### 3. Activate automation

Push the workflow file to your default branch.

GitHub Actions will automatically schedule future executions.

## Manual Execution

You can also trigger the workflow manually:

1. Open your GitHub repository.
2. Navigate to the Actions tab.
3. Select Daily Contribution.
4. Click Run workflow.

## Requirements

- A GitHub account.
- A repository with GitHub Actions enabled.
- Write permissions for the workflow.
- The workflow file committed to the repository's default branch.

## Important Notes

- Your computer does not need to be running.
- GitHub Actions executes the workflow independently.
- Every successful run updates the maintenance timestamp.
- A commit is created only when the file changes.
- Scheduled workflows are not guaranteed to execute at an exact time.
- GitHub contribution visibility depends on contribution eligibility and repository settings.

## License

MIT License — use and modify this workflow freely.
