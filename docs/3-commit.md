# How to Do, Undo, Revert, Redo, and Edit Previous Commits

## Overview

During the development process, you may need to undo, revert, redo, or even edit previous commits. Whether you need to fix a mistake in your commit history, modify a commit message, or discard unnecessary commits, Git provides several tools to help you achieve this.

In this guide, we will explore how to do, undo, revert, redo, and edit previous commits in Git, with clear steps and explanations for each operation.

---

## How to Do a Commit

Before diving into how to undo, revert, redo, or edit a commit, let’s first review how to perform a commit in Git.

### Step-by-Step Instructions

#### 1. **Stage Your Changes**

Before committing, make sure you’ve added the changes you want to include in the commit to the staging area.

```bash
git add .
```

This command stages all modified and new files. Alternatively, you can stage specific files using:

```bash
git add <file_name>
```

#### 2. **Commit Your Changes**

Once your changes are staged, you can commit them:

```bash
git commit -m "Your commit message"
```

This will commit the changes with a descriptive message. Make sure your commit messages are clear and concise to keep your history clean.

---

## How to Undo a Commit in Git

Sometimes, you might commit prematurely or make a mistake. Git allows you to undo commits in several ways.

### Step-by-Step Instructions

#### 1. **Undo the Last Commit (Keep Changes)**

If you want to undo the last commit but keep the changes you made in your working directory, you can use:

```bash
git reset --soft HEAD~1
```

This command moves the `HEAD` back one commit but keeps the changes staged for the next commit.

#### 2. **Undo the Last Commit (Discard Changes)**

If you want to completely discard the last commit and its changes, use:

```bash
git reset --hard HEAD~1
```

This command removes the last commit and all associated changes, including the working directory modifications.

#### 3. **Undo Multiple Commits (Keep Changes)**

To undo multiple commits but retain your changes in the staging area, you can specify the number of commits to go back:

```bash
git reset --soft HEAD~3
```

This will undo the last three commits and leave the changes staged.

#### 4. **Undo Multiple Commits (Discard Changes)**

To undo multiple commits and discard the changes entirely, use:

```bash
git reset --hard HEAD~3
```

This will completely remove the last three commits and their changes from both the repository and your working directory.

---

## How to Revert a Commit in Git

Unlike `git reset`, `git revert` creates a new commit that undoes the changes from a previous commit, preserving the commit history.

### Step-by-Step Instructions

#### 1. **Revert a Single Commit**

To revert a specific commit, use its commit hash (which you can find with `git log`):

```bash
git revert <commit_hash>
```

This command creates a new commit that undoes the changes introduced by the specified commit.

#### 2. **Revert a Range of Commits**

You can revert multiple commits by specifying a commit range:

```bash
git revert <commit_hash_1>^..<commit_hash_n>
```

This will revert all the commits in the range from `<commit_hash_1>` to `<commit_hash_n>`.

#### 3. **Revert All Changes Made by a Commit**

To revert all changes made by a commit but not affect the history of commits after it, use:

```bash
git revert --no-commit <commit_hash>
```

This will stage the changes to be committed later, without automatically creating a commit.

---

## How to Redo a Commit in Git

If you’ve undone a commit but want to redo it, Git offers a couple of ways to recover lost commits or redo changes.

### Step-by-Step Instructions

#### 1. **Recover Lost Commits Using `git reflog`**

Git keeps a log of all the changes to `HEAD` (reference log), even if those commits were lost due to a `reset` or other operations. You can use `git reflog` to find lost commits.

```bash
git reflog
```

This will show you the history of `HEAD` movements. Find the commit you want to recover and use its reference to reset or checkout to it.

```bash
git reset --hard <reflog_commit_hash>
```

#### 2. **Redo a Commit Using `git cherry-pick`**

If you want to reapply a commit that was removed or discarded (e.g., during a reset), use the `git cherry-pick` command:

```bash
git cherry-pick <commit_hash>
```

This command creates a new commit with the changes from the specified commit, applying it to the current branch.

---

## How to Edit Previous Commits in Git

Editing a previous commit can be useful for fixing commit messages or adding changes that were missed in an earlier commit.

### Step-by-Step Instructions

#### 1. **Edit the Last Commit**

To modify the last commit, either to change the commit message or add new changes, use:

```bash
git commit --amend
```

This opens the commit editor, allowing you to change the commit message. If you want to add changes to the last commit, stage the changes first, and then run the `--amend` command.

#### 2. **Edit an Older Commit Using Interactive Rebase**

To edit a commit that isn’t the most recent, use `git rebase -i`:

```bash
git rebase -i HEAD~3
```

This command allows you to edit commits from the last 3 commits. When the editor opens, change `pick` to `edit` next to the commit you want to modify, then save and close the editor.

Git will pause at the commit you want to edit. You can then modify the commit message or make changes, and when you’re done, you can use:

```bash
git commit --amend
git rebase --continue
```

This will apply the changes to the commit and continue the rebase process.

## Notes, Cautions, and Warnings

- **Avoid Rewriting History in Shared Repositories**: If you’ve already pushed commits to a shared repository, using `git reset` or `git rebase` can rewrite history, causing problems for your collaborators. In these cases, prefer using `git revert` instead to maintain a clean history.

- **Be Careful with `git reset --hard`**: The `--hard` option removes both commits and changes in your working directory. Always double-check before using this command to avoid data loss.

- **Back Up Important Changes**: Before doing operations like `git reset --hard` or rebasing, it’s a good idea to create a backup branch in case you need to recover your changes later:

  ```bash
  git checkout -b backup-branch
  ```

## Conclusion

Git provides various commands to undo, revert, redo, and edit previous commits, making it a highly flexible tool for version control. Whether you need to fix a mistake, alter commit messages, or recover lost commits, Git’s powerful commands like `git reset`, `git revert`, `git rebase`, and `git cherry-pick` offer the solutions you need.

By understanding the difference between these commands and when to use them, you can manage your repository’s history effectively and avoid making irreversible mistakes. Always be mindful when altering commit history, especially in shared repositories, and ensure you have backups when performing potentially destructive actions.
