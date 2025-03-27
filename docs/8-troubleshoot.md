# Troubleshooting guide

## TL;DR

- **Check Git Status**: Use git status frequently to see the state of your repository and any potential issues.
- **Use Git Log**: If you need to investigate the history of commits, use git log to review past changes and pinpoint issues.
- **Backup Your Work**: If you are unsure about any operation (like a merge), create a backup branch:

```powershell
git branch backup-branch
```

## Purpose of this Troubleshooting Guide

- This guide helps resolve some of the common issues that developers may face when using Git, particularly for beginners and intermediate users.
- Each issue is explained in a way that allows users to identify the problem, apply the correct solution, and continue their work with minimal interruptions.

## 1. **"fatal: not a git repository" Error**

### Problem

You might encounter the error message:

```powershell
fatal: not a git repository (or any of the parent directories): .git
```

This occurs when you try to run a Git command (like `git status`) outside of a Git repository.

### Solution

- Make sure you are in the correct directory. A Git repository is identified by a hidden `.git` folder. If you’re not inside a repository, navigate to the correct folder where the repository is initialized or cloned.
- If you’re sure you should be in a repository but `.git` is missing, you might need to reinitialize the Git repository by running:

```powershell
git init
```

## 2. Merge Conflicts

### Problem

When trying to merge branches (e.g., with git merge branch-name), you may encounter conflicts:

```powershell
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
```

### Solution

1. **Identify and Resolve Conflicts**: Git will mark the conflicting sections of the file using conflict markers (<<<<<<<, =======, >>>>>>>). Open the conflicted file and manually resolve the differences.

2. **Stage the Resolved Files**: Once you’ve resolved the conflict, stage the changes:

```powershell
git add file.txt
```

3. **Complete the Merge**: After resolving all conflicts, commit the changes to complete the merge:

```powershell
git commit
```

## 3. "Detached HEAD" State

### Problem

You might find yourself in a "detached HEAD" state if you check out a specific commit instead of a branch. This results in the following message:

You are in 'detached HEAD' state. You can look around, make experimental changes and commit them, but you are not on a branch.

### Solution

- If you want to return to your branch, simply run:

```powershell
git checkout main   # or the name of your branch
```

- If you want to create a new branch from your current commit:

```powershell
git checkout -b new-branch-name
```

## 4. Untracked Files (Files Not Being Tracked by Git)

### Problem

You see untracked files when you run git status, and you don’t want to commit them yet:

```powershell
Untracked files:
  (use "git add <file>..." to include in what will be committed)
    file1.txt
```

### Solution

- To Ignore Specific Files: If you don’t want to track certain files, you can add them to a .gitignore file. For example, add file1.txt to .gitignore:

```powershell
file1.txt
```

After adding files to .gitignore, run:

```powershell
git rm --cached file1.txt
```

- To Track Files: If you want to track the untracked files, simply add them to the staging area:

```powershell
git add file1.txt
```

## 5. Push Rejected Due to Non-Fast-Forward Updates

### Problem

When trying to push your changes, you might encounter an error like:

```powershell
! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to '<https://github.com/username/repo.git>'
```

This happens when your local branch is behind the remote branch and doesn’t include changes that have been pushed by others.

### Solution

1. **Pull the Latest Changes**: Before pushing, you need to pull the latest changes from the remote repository:

```powershell
git pull origin main   # or the relevant branch
```

2. **Resolve Any Merge Conflicts**: If there are conflicts, resolve them as described in the "Merge Conflicts" section above.

3. **Push Again**: After resolving the conflicts and committing the changes, push your changes again:

```powershell
git push origin main
```
