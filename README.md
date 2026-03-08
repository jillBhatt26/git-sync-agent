# Git Sync Agent

A specialized Gemini CLI skill for synchronizing local Git repositories, designed to streamline development workflows in microservices environments.

## Overview

The Git Sync Agent eliminates the need for manual repository switching and repetitive `git pull` sequences. It's built for developers who manage multiple repositories and want a seamless way to keep their local environments up-to-date with remote changes.

## Key Features

- **Multi-Repo Synchronization**: Sync all repositories in a directory or target specific ones using `@repo-name`.
- **Automatic Stashing**: Safely stashes uncommitted changes before pulling and restores them after the sync.
- **Target Branch Intelligence**: Automatically identifies the default remote branch or allows targeting specific branches.
- **Conflict Awareness**: Detects and reports merge conflicts, stopping for manual intervention when necessary.
- **Safe Execution**: By default, runs sync operations directly but honors explicit requests for review or approval.

## Usage

Invoke the agent by referencing it in your prompt with the `@git-sync-agent` handle:

- **Sync All Repositories**:
  `@git-sync-agent sync`
- **Sync a Specific Repository**:
  `@git-sync-agent sync @auth-service`
- **Pull a Specific Branch**:
  `@git-sync-agent pull feature/new-api`
- **Sync with a Specific Base Directory**:
  `@git-sync-agent sync in ./services/`

## How It Works

1.  **Safety & Intent**: Parses your query for specific repositories, branches, or constraints.
2.  **Repo Discovery**: Locates the targeted repositories and checks their current status.
3.  **Sync Sequence**:
    - Verifies the repository's existence.
    - Stashes any uncommitted changes.
    - Determines the remote target branch.
    - Executes `git pull origin <target_branch>`.
    - Restores the stash if applicable.
4.  **Reporting**: Provides a conversational summary of the results, including the number of repositories synced and any detected conflicts.

---
*Created as part of the Hackathon March 2026.*
