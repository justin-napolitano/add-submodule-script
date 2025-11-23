# Add Submodule Script

A simple Bash script to automate adding Git submodules to your repository. It streamlines the process by creating a new branch, adding the submodule at the specified location, committing the changes, pushing the branch to GitHub, and opening a pull request automatically.

## Features

- Adds a Git submodule to a specified directory within your repository.
- Automatically creates a new branch named after the submodule repository.
- Commits and pushes changes to GitHub.
- Creates a pull request using the GitHub CLI (`gh`).

## Tech Stack

- Shell scripting (Bash)
- Git
- GitHub CLI (`gh`)

## Getting Started

### Prerequisites

- Git installed and configured on your system.
- GitHub CLI (`gh`) installed and authenticated. Installation instructions can be found [here](https://cli.github.com/manual/installation).

### Installation & Usage

1. Clone or download this repository.

2. Make the script executable:

```bash
chmod +x add_submodule.sh
```

3. Run the script with the submodule repository link and the target location within your repo:

```bash
./add_submodule.sh <submodule-link> <location>
```

Example:

```bash
./add_submodule.sh https://github.com/username/repo.git content/posts
```

This will add the submodule `repo` into the `content/posts/repo` directory, create a new branch named `repo`, commit the changes, push the branch, and open a pull request against the `main` branch.

## Project Structure

```
add-submodule-script/
├── add_submodule.sh    # Main Bash script to add submodules
├── README.md           # This README file
└── index.md            # Tutorial/blog post explaining the script
```

## Future Work / Roadmap

- Add support for customizing the base branch for pull requests.
- Add error handling for GitHub CLI failures.
- Support for adding multiple submodules in one run.
- Add options for customizing commit messages and PR descriptions.
- Provide more detailed logging and verbose mode.

---

*Note: This script assumes you have the necessary permissions to push branches and create pull requests on the target repository.*