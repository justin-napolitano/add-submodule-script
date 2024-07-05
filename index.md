
# Add Submodule Script

This script is designed to add a submodule to a Git super project by passing only the link to the submodule. It will create a new branch with the repository name and add the submodule to the specified path.

## Usage

### Prerequisites

Ensure you have Git installed and configured on your system.

### Running the Script

1. Save the script to a file, e.g., `add_submodule.sh`.

2. Make the script executable:
    ```bash
    chmod +x add_submodule.sh
    ```

3. Run the script with the submodule link as an argument:
    ```bash
    ./add_submodule.sh <submodule-link>
    ```

### Example

To add a submodule with the link `https://github.com/username/repo.git`, run:
```bash
./add_submodule.sh https://github.com/username/repo.git
```

## Script Details

### `add_submodule.sh`

```bash
#!/bin/bash

# Get the submodule link from the first argument
submodule_link=$1

# Check if the submodule link was provided
if [ -z "$submodule_link" ]; then
    echo "Error: No submodule link provided."
    echo "Usage: $0 <submodule-link>"
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
git submodule add "$submodule_link" "content/posts/$repo_name"

echo "Submodule $repo_name added successfully to content/posts/$repo_name"
```

### How It Works

1. **Get the submodule link**: The script takes the submodule link as the first argument.
2. **Check if the link is provided**: If no link is provided, it shows an error message and exits.
3. **Extract the repo name**: The script extracts the repository name from the provided link.
4. **Check if the repo name was extracted successfully**: If not, it shows an error message and exits.
5. **Checkout a new branch**: It creates a new branch with the repository name.
6. **Add the submodule**: Finally, it adds the submodule to the specified path.

## License

This script is provided "as is" without any warranty. You can modify and distribute it as needed.
