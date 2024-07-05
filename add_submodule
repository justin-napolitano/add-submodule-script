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

echo "Submodule $repo_name added successfully to $location/$repo_name"
