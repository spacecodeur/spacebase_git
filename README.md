# spacebase_git

## Overview

**spacebase_git** is a lightweight Git configuration base meant to be easily integrated into both new and existing projects.  
It provides ready-to-use Git hooks and conventions — such as commit message validation — to enforce a clean and consistent Git history across your team or projects.  
The goal is to simplify setup while encouraging good development practices from day one.

---

## How to integrate `spacebase_git` into your project

Follow the steps below to integrate `spacebase_git` into an existing Git repository.

### 1. Add `spacebase_git` as a remote

Replace the URL with the actual location of the `spacebase_git` repository.

```bash
git remote add spacebase_git git@github.com:spacecodeur/spacebase_git.git
```

### 2. Fetch the latest `spacebase_git` changes

```bash
git fetch spacebase_git
```

### 3. Merge `spacebase_git` into your project (while keeping your files safe)

Use the --allow-unrelated-histories flag to allow merging two unrelated repositories (your project and spacebase_git):

```bash
git merge spacebase_git/main --allow-unrelated-histories
```

This will prompt you to resolve any conflicts if they arise, but your existing files will remain untouched unless there are naming overlaps.

### 4. Commit the merge

```bash
git commit -m "Merge spacebase_git configuration"
```

## [Important] Enable Git hooks

To activate the Git hooks provided by this base (like commit message validation), configure Git to use the custom hooks path:

```bash
git config core.hooksPath .git-hooks
```

This command should be executed from the root of your project, after merging.

## [Optional] Bypass hooks if needed

In some edge cases (e.g., emergency fixes or experimenting), you may want to commit without triggering any Git hooks.
Use the `--no-verify` flag to bypass them:

```bash
git commit --no-verify -m "your message"
```

Use this sparingly, as it disables useful checks designed to keep your Git history clean and consistent.

