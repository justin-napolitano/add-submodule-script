
# Add Submodule Script

This script is designed to add a submodule to a Git super project by passing the link to the submodule and the location where it should be added. It also pushes the new branch to GitHub and creates a pull request.

## Usage

### Prerequisites

1. Ensure you have Git installed and configured on your system.
2. Ensure you have the GitHub CLI (`gh`) installed and authenticated. You can install it following the instructions [here](https://cli.github.com/manual/installation).

### Running the Script

1. Save the script to a file, e.g., `add_submodule.sh`.

2. Make the script executable:
    ```bash
    chmod +x add_submodule.sh
    ```

3. Run the script with the submodule link and location as arguments:
    ```bash
    ./add_submodule.sh <submodule-link> <location>
    ```

### Example

To add a submodule with the link `https://github.com/username/repo.git` to the `content/posts` directory, run:
```bash
./add_submodule.sh https://github.com/username/repo.git content/posts
```

## Script Details

### `add_submodule.sh`

```bash
#!/bin/bash

# Get the submodule link from the first argument
submodule_link=$1

# Get the location from the second argument
location=$2

# Check if the submodule link was provided
if [ -z "$submodule_link" ]; then
    echo "Error: No submodule link provided."
    echo "Usage: $0 <submodule-link> <location>"
    exit 1
fi

# Check if the location was provided
if [ -z "$location" ]; then
    echo "Error: No location provided."
    echo "Usage: $0 <submodule-link> <location>"
    exit 1
fi

# Extract the repo name from the submodule link
repo_name=$(basename -s .git "$submodule_link")

# Check if the repo name was extracted successfully
if [ -z "$repo_name" ]; then
    echo "Error: Could not extract repo name from the link."
    exit 1
fi

# Checkout a new branch with the repo name
git checkout -b "$repo_name"

# Add the submodule
git submodule add "$submodule_link" "$location/$repo_name"

# Commit the changes
git add .
git commit -m "Add submodule $repo_name"

# Push the new branch to GitHub
git push -u origin "$repo_name"

# Create a pull request using GitHub CLI
gh pr create --title "Add submodule $repo_name" --body "This PR adds the submodule $repo_name to $location" --base main --head "$repo_name"

echo "Submodule $repo_name added successfully to $location/$repo_name"
echo "Branch $repo_name pushed to GitHub and pull request created."
```

### How It Works

1. **Get the submodule link**: The script takes the submodule link as the first argument.
2. **Get the location**: The script takes the location as the second argument.
3. **Check if the submodule link and location are provided**: If either is not provided, the script shows an error message and exits.
4. **Extract the repo name**: The script extracts the repository name from the provided link.
5. **Check if the repo name was extracted successfully**: If not, the script shows an error message and exits.
6. **Checkout a new branch**: It creates a new branch with the repository name.
7. **Add the submodule**: Finally, it adds the submodule to the specified location.
8. **Commit the changes**: Adds and commits the changes to the new branch.
9. **Push the new branch to GitHub**: Pushes the new branch to GitHub.
10. **Create a pull request**: Uses the GitHub CLI to create a pull request with the specified title and body.

## License

This script is provided "as is" without any warranty. You can modify and distribute it as needed.
