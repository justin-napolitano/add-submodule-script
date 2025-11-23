---
slug: "github-add-submodule-script"
title: "add-submodule-script"
repo: "justin-napolitano/add-submodule-script"
githubUrl: "https://github.com/justin-napolitano/add-submodule-script"
generatedAt: "2025-11-23T08:34:12.625328Z"
source: "github-auto"
---


# Write a Script to Add a Submodule to Repo

## Motivation

Managing Git submodules manually can be tedious and error-prone. The process involves multiple steps: creating a branch, adding the submodule at a specific location, committing changes, pushing the branch, and finally opening a pull request. Automating these steps reduces manual overhead and enforces consistency.

## Problem Statement

Adding a Git submodule to a repository typically requires running several Git commands in sequence. This can lead to mistakes such as committing on the wrong branch, forgetting to push, or improperly structuring the submodule path. Additionally, creating a pull request is a separate step that often involves navigating the GitHub UI or using the CLI manually.

## Solution Overview

This project provides a Bash script that automates the entire workflow of adding a submodule. Given a submodule repository URL and a target location within the parent repository, the script:

1. Extracts the submodule repository name from the URL.
2. Creates a new Git branch named after the submodule repository.
3. Adds the submodule under the specified location.
4. Commits the changes with a standardized message.
5. Pushes the branch to the remote repository.
6. Creates a pull request targeting the main branch using the GitHub CLI.

## Implementation Details

The script accepts two positional arguments: the submodule link and the location where the submodule should be added.

- It validates the presence of both arguments and exits with an error message if either is missing.
- The repository name is extracted using `basename -s .git` on the submodule URL, which strips the `.git` suffix and isolates the repo name.
- A new branch is checked out with the repo name to isolate changes.
- The `git submodule add` command adds the submodule at the specified directory path, which is constructed by combining the provided location and the repo name.
- Changes are staged and committed with a message indicating the submodule added.
- The branch is pushed to the remote origin.
- The GitHub CLI command `gh pr create` is used to open a pull request, with the title and body referencing the submodule and location.

## Practical Considerations

- The script assumes the user has Git and the GitHub CLI installed and authenticated.
- It does not currently handle errors from Git or the GitHub CLI commands beyond initial argument validation.
- The base branch for the pull request is hardcoded as `main`.
- The commit message and pull request content are standardized but could be parameterized in future iterations.

## Usage

Make the script executable:

```bash
chmod +x add_submodule.sh
```

Run the script:

```bash
./add_submodule.sh <submodule-link> <location>
```

For example:

```bash
./add_submodule.sh https://github.com/username/repo.git content/posts
```

This adds the `repo` submodule inside `content/posts/repo`, creates a branch named `repo`, commits the change, pushes the branch, and opens a pull request against `main`.

## Summary

This script encapsulates a common Git submodule workflow into a single executable command, reducing manual steps and potential errors. It leverages the GitHub CLI to integrate pull request creation directly from the command line, streamlining collaboration and code review processes.

Future improvements could focus on error handling, customization, and supporting batch operations.