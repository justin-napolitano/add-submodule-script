---
slug: github-add-submodule-script-note-technical-overview
id: github-add-submodule-script-note-technical-overview
title: Add Submodule Script
repo: justin-napolitano/add-submodule-script
githubUrl: https://github.com/justin-napolitano/add-submodule-script
generatedAt: '2025-11-24T18:30:15.259Z'
source: github-auto
summary: >-
  This repository contains a straightforward Bash script that adds Git
  submodules to your repo. It takes care of everything from creating a branch to
  pushing your changes and setting up a pull request using the GitHub CLI.
tags: []
seoPrimaryKeyword: ''
seoSecondaryKeywords: []
seoOptimized: false
topicFamily: null
topicFamilyConfidence: null
kind: note
entryLayout: note
showInProjects: false
showInNotes: true
showInWriting: false
showInLogs: false
---

This repository contains a straightforward Bash script that adds Git submodules to your repo. It takes care of everything from creating a branch to pushing your changes and setting up a pull request using the GitHub CLI.

## Key Features

- Adds a submodule to a specified directory.
- Generates a new branch named after the submodule.
- Commits and pushes changes.
- Automatically opens a pull request.

## Getting Started

### Prerequisites

- Git installed and configured.
- GitHub CLI (`gh`) installed and logged in. Check [GitHub CLI Installation](https://cli.github.com/manual/installation) for details.

### Usage

1. Clone the repo.
2. Make the script executable:

   ```bash
   chmod +x add_submodule.sh
   ```

3. Run the script with:

   ```bash
   ./add_submodule.sh <submodule-link> <location>
   ```

Example:

```bash
./add_submodule.sh https://github.com/username/repo.git content/posts
```

*Note: Ensure both Git and GitHub CLI are set up before running the script.*
