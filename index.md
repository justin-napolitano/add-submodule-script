---
slug: "github-add-submodule-script"
title: "add-submodule-script"
repo: "justin-napolitano/add-submodule-script"
githubUrl: "https://github.com/justin-napolitano/add-submodule-script"
generatedAt: "2025-11-23T08:10:52.655020Z"
source: "github-auto"
---


+++
title = "Write a Script to add a Submodule to Repo"
author = "Justin Napolitano"
date = "2024-07-05"
categories = ["Tutorials"]
tags = ["scripts", "bash", "git"]
+++

# Write a Script to add a Submodule to Repo

Hey there! Today I want to share a little Bash script I wrote to make adding Git submodules easier and less error-prone. If you’ve ever worked with submodules in Git, you know the process can be a bit tedious and repetitive — especially if you’re managing multiple submodules or want to streamline your workflow.

## Motivation

The main motivation behind this script was to automate the manual steps I was doing every time I needed to add a submodule to a project. Typically, I would:

- Create a new branch
- Add the submodule at a specific location
- Commit the change
- Push the branch
- Open a pull request on GitHub

Doing this manually is not only time-consuming but also prone to mistakes, like forgetting to switch branches or pushing the wrong commit.

## What Problem Does This Solve?

This script takes two arguments: the Git repository link of the submodule and the location within your repo where you want to add it. It then:

1. Extracts the repository name from the link.
2. Creates a new branch named after the submodule repo.
3. Adds the submodule at the specified path.
4. Commits the changes.
5. Pushes the branch to GitHub.
6. Creates a pull request using the GitHub CLI (`gh`).

All in one go! This means less context switching and fewer manual steps.

## How It’s Built

The script is a straightforward Bash script that uses standard Git commands and the GitHub CLI. Here are some interesting implementation details:

- It uses `basename -s .git` to extract the repo name from the URL.
- It checks for missing arguments and prints helpful usage instructions.
- It assumes you have `gh` installed and authenticated, which is crucial for automating the pull request creation.
- It dynamically creates a branch named after the submodule repo, keeping your branches organized and descriptive.

## Usage

Make sure you have Git and GitHub CLI installed and authenticated.

Save the script as `add_submodule.sh` and make it executable:

```bash
chmod +x add_submodule.sh
```

Then run it with:

```bash
./add_submodule.sh <submodule-link> <location>
```

For example:

```bash
./add_submodule.sh https://github.com/username/repo.git content/posts
```

This will add the submodule `repo` inside `content/posts/repo`, create a branch `repo`, push it, and open a PR.

## Why this project matters for my career

Automating repetitive tasks like adding submodules saves me time and reduces errors, which means I can focus on writing better code and shipping features faster. It also demonstrates my ability to streamline workflows using scripting and GitHub automation — skills that are highly valuable in any software development role. Plus, sharing this script publicly helps me build a portfolio of practical tools and shows my commitment to improving developer experience.

Thanks for reading! If you find this script useful, feel free to fork it, suggest improvements, or share your own automation tips.