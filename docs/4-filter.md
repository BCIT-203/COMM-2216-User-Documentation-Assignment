# How to  `git-filter-branch` and `git-filter-repo`

## Overview

When working with Git repositories, there are scenarios where you might need to rewrite history, such as removing sensitive data, editing commit messages, or cleaning up large files. Git provides two powerful tools for this task: `git-filter-branch` and `git-filter-repo`. While`git-filter-branch` is widely used, `git-filter-repo` is a more modern, faster, and more efficient alternative. Both tools allow you to rewrite commit history, but they differ in performance and flexibility.

In this guide, we will walk through detailed examples of using both tools to filter and rewrite Git history, breaking down the steps into more than 10 specific actions.

---

## Backup Repository Before Filtering

Before running any filtering operations, it’s essential to back up your repository to prevent data loss. You can create a backup by cloning the repository:

```bash
git clone --mirror <repository-url> <backup-directory>
```

1. This creates a full backup of your repository in `<backup-directory>`.
2. Ensure you test any filtering operations on the backup repository first.

!!! warning
    Always back up your repository before using `git-filter-branch` or `git-filter-repo`, as these operations rewrite history and can result in permanent data loss.

!!! warning
    Both `git-filter-branch` and `git-filter-repo` rewrite Git history. This means commit hashes will change, and this can cause issues if others have cloned or forked the repository. Rewriting history can disrupt collaboration, so it should only be done on private branches or with careful coordination.

!!! danger
    After filtering, you will need to **force push** (`git push --force`) to update the remote repository. This can cause conflicts for other contributors, so it’s best to communicate changes clearly.

!!! warning
    Running `git-filter-branch` or `git-filter-repo` on large repositories can take time. Always run the filter on a clone of the repository to test the process before applying it to the main repository.

---

## `git-filter-branch` Overview

`git-filter-branch` is an older but still commonly used tool in Git to rewrite commit history. It is particularly useful for tasks like removing sensitive files from the history or modifying commit messages. However, it can be slow on large repositories.

### Remove a Specific File from Entire History

You can use `git-filter-branch` to remove a file, such as a sensitive configuration file, from the entire history of your Git repository.

#### Instruction

Run the following command to remove a specific file from the history:

```bash
git filter-branch --tree-filter 'rm -f path/to/your/file' -- --all
```

Replace `path/to/your/file` with the file you want to remove.
This command will rewrite all commits and remove the specified file from every commit.

!!! note
    This will rewrite all branches (`--all`) and affect the entire commit history.

!!! note
    Be sure to make a backup before running this command, as it will permanently remove the file from history.

---

### Modify Commit Messages

If you need to update the commit messages (for example, to correct typos or reword them), `git-filter-branch` can help.

#### Instruction

Run the following command to filter commit messages:

    ```bash
    git filter-branch --msg-filter 'sed "s/old-text/new-text/"' -- --all
    ```

Replace `old-text` and `new-text` with the text you want to change.
This will replace the specified text in all commit messages across all branches.

!!! warning
    Modifying commit messages will rewrite commit history and affect all branches.

!!! warning
    Ensure that you do this carefully, especially if you’ve shared the history with others.

---

### Replace an Author Name and Email Across All Commits

If you need to change the author’s name or email address in the commit history:

#### Instruction

Run the following command to update the author’s name and email:

    ```bash
    git filter-branch --env-filter '
    if [ "$GIT_AUTHOR_NAME" = "Old Name" ];
    then
        export GIT_AUTHOR_NAME="New Name"
        export GIT_AUTHOR_EMAIL="new-email@example.com"
        export GIT_COMMITTER_NAME="New Name"
        export GIT_COMMITTER_EMAIL="<new-email@example.com>"
    fi' -- --all
    ```

Replace `Old Name` with the current author name and `New Name` with the new name.
This will update both the author and committer information for all commits.

!!! warning
    This action rewrites history and should be done with caution, especially if the repository is shared with others.

---

### Remove Large Files from Git History

To remove a large file (e.g., a `.zip` file or image) that was accidentally committed, use `git-filter-branch` with the `--tree-filter` option.

#### Instruction

Run the following command to remove the file:

```bash
git filter-branch --tree-filter 'rm -f path/to/largefile' -- --all
```

Replace `path/to/largefile` with the path to the file you want to remove.
This will delete the file from all commits, reducing repository size.

!!! warning
    Removing large files will reduce the repository size, but it will also rewrite the history.

---

## `git-filter-repo` Overview

`git-filter-repo` is a more efficient and flexible tool designed to handle large repositories and more complex filtering tasks. It is faster than `git-filter-branch` and is recommended for more advanced users. It’s also easier to install and use.

### Install `git-filter-repo`

#### Instruction

Before using `git-filter-repo`, you need to install it. Run the following command:

```bash
pip install git-filter-repo
```

Alternatively, you can install it directly from [GitHub](https://github.com/newren/git-filter-repo).

---

### Remove a File from Repository History with `git-filter-repo`

You can remove a file from the entire history of the repository using.

#### Instruction

Run the following command:

```bash
git filter-repo --invert-paths --path secret.txt
```

This command will remove `secret.txt` from every commit.
The `--invert-paths` option tells Git to exclude (filter out) the specified file.

!!! note
    `git-filter-repo` is faster and more efficient than `git-filter-branch`, especially on large repositories.

---

### Change the Author of Specific Commits

You can modify the author’s name for specific commits using `git-filter-repo`. For example, to change the author for commits by a specific person:

#### Instruction

Run the following command:

```bash
git filter-repo --commit-callback '
if commit.author_name == "Old Author":
      commit.author_name = "New Author"
'
```

This will update all commits made by `Old Author` and change the name to `New Author.`

---

### Remove Multiple Files from History

You can remove multiple files.

#### Instruction

Run the following command:

```bash
git filter-repo --invert-paths --path secret.txt --path config.json
```

This command will remove both files, `secret.txt` and `config.json`, from the entire repository history.

---

### Replace a String in Commit Messages

YOu can replace a specific string across all commit messages.

#### Instruction

Run the following command:

```bash
git filter-repo --message-callback '
if "old-text" in commit.message:
    commit.message = commit.message.replace("old-text", "new-text")
'
```

This command replaces `old-text` with `new-text` in all commit messages.

---

## Conclusion

Both `git-filter-branch` and `git-filter-repo` are powerful tools for rewriting Git history. While `git-filter-branch` is useful for simpler tasks, `git-filter-repo` is more efficient and suited for larger repositories.

Always back up your repository before using these tools, and communicate with collaborators if you’re working in a shared repository. With the right precautions, you can clean up your Git history and improve your repository management effectively.
