### README.md

````markdown
# Clarity Project Automation Scripts

This repository contains a set of Bash scripts designed to streamline and automate the entire workflow for developing Clarity smart contracts on Replit. These scripts handle everything from initial project setup and Git configuration to routine development tasks like checking code and making commits.

---

### Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
  - [1. Initial Setup](#1-initial-setup)
  - [2. Everyday Workflow](#2-everyday-workflow)
- [Scripts Overview](#scripts-overview)
- [Configuration](#configuration)

---

### Features

- **Automated Project Creation:** Instantly scaffold a new Clarity project using `clarinet new`, including automatic handling of the initial setup prompts.
- **Git Integration:** Automates Git initialization, remote repository setup, and the initial commit and push.
- **Secure Authentication:** Utilizes Replit Secrets to securely handle your GitHub Personal Access Token (PAT), preventing sensitive data from being hardcoded in your scripts.
- **Workflow Scripts:** Includes two utility scripts for common development tasks: one for checking and committing code, and another for quick commits and pushes.
- **Project Hygiene:** Automatically adds the utility scripts to the `.gitignore` file to ensure they are not tracked by Git, keeping your repository clean.

---

### Prerequisites

Before using these scripts, you must have the following set up in your Replit workspace:

1.  **Clarity and Clarinet:** Ensure the Clarity CLI (`clarinet`) is installed and accessible from your shell.
2.  **Replit Secret:** Your GitHub Personal Access Token (PAT) must be stored as a Replit Secret.
    -   Go to the **Secrets** tab (lock icon) in the Replit sidebar.
    -   Add a new secret with the **key** `GITHUB_PAT` and your token as the **value**.

---

### Usage

This workflow is broken into two main parts: the one-time initial setup and the day-to-day development loop.

#### 1. Initial Setup

Use the `full_clarity_setup.sh` script to create a new project from scratch. This script takes three arguments: the project name, the branch name, and the initial contract name.

```bash
# Example
./full_clarity_setup.sh <project_name> <branch_name> <contract_name>
````

**Example:**

```bash
./full_clarity_setup.sh my-stx-app feature-new-contract my-first-contract
```

After running this command, a new project directory will be created, fully configured with Git, and the `ClarCommit.sh` and `FinCommit.sh` scripts will be placed inside.

#### 2\. Everyday Workflow

Once your project is set up, navigate into your project directory to use the utility scripts.

  - **To Check Code and Start a Custom Commit:**
    This script runs `clarinet check` and then opens a text editor for you to write a custom commit message.

    ```bash
    ./ClarCommit.sh
    ```

  - **To Commit a `README.md` Update:**
    This script is for quick, specific commits. It stages all changes, commits with a predefined "README.md file updated" message, and pushes to the current branch.

    ```bash
    ./FinCommit.sh
    ```

-----

### Scripts Overview

#### `full_clarity_setup.sh`

The primary script for project initialization. It handles:

  - Argument validation.
  - `clarinet new` with a secure prompt handler.
  - Git repository initialization and remote setup.
  - Initial commit and push to `main`.
  - Branch creation.
  - Contract creation.
  - Copying `ClarCommit.sh` and `FinCommit.sh` into the new project.
  - Adding the scripts to `.gitignore`.

#### `ClarCommit.sh`

A development utility script that performs:

  - `clarinet check` to validate your code.
  - `git add .` to stage all changes.
  - `git commit` to open a text editor for a detailed commit message.

#### `FinCommit.sh`

A quick utility for specific commits, performing:

  - `git add .` to stage changes.
  - `git commit -m "README.md file updated"` for a standardized commit message.
  - `git push` to upload changes to your branch.

-----

### Configuration

The `full_clarity_setup.sh` script is configured with your GitHub username. You can easily modify the following variables in the script if needed:

  - `GITHUB_USERNAME="ImmaObong"`

Remember that your `GITHUB_PAT` is not hardcoded and is securely managed as a Replit Secret.

```
```