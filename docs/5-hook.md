# How to Use Different Git Hooks

## Overview

Git hooks are a powerful feature that allow you to automate various actions within a Git repository. They are scripts that can be triggered at different points in the Git workflow, such as before a commit is made, before pushing code to a remote repository, or after a merge. By using hooks, developers can enforce coding standards, run tests, and automate repetitive tasks, enhancing collaboration and reducing manual errors.

In this guide, we will explore how to use various Git hooks and give you detailed steps on setting them up to improve your development workflow.

## Types of Git Hooks

Git provides several hooks that can be used to automate tasks. Some of the most commonly used hooks are:

- **Pre-commit Hook**: Runs before a commit is made. It can be used for tasks like linting or running tests.
- **Commit-msg Hook**: Runs after a commit message is entered but before the commit is finalized. It is typically used for checking the format of commit messages.
- **Pre-push Hook**: Runs before pushing changes to a remote repository. You can use this to run tests or prevent pushing broken code.
- **Post-merge Hook**: Runs after a merge operation is completed. It can be used to run additional setup tasks, like installing dependencies.

## Setting Up Git Hooks

Git hooks are stored in the `.git/hooks` directory of your Git repository. This directory contains sample scripts for each hook, which you can customize for your needs.

### Step 1: Navigate to the `.git/hooks` Directory

1. Open your terminal.
2. Navigate to the root directory of your Git repository:

   ```bash
   cd /path/to/your/repository
   ```

3. Change to the `.git/hooks` directory:

   ```bash
   cd .git/hooks
   ```

### Step 2: Identify the Hook You Want to Use

In the `.git/hooks` directory, you'll find sample hook scripts, such as `pre-commit.sample`, `post-merge.sample`, etc. These files are templates that you can modify and use.

### Step 3: Create or Edit the Hook Script

1. Choose the hook you want to implement (e.g., `pre-commit`).
2. Rename the sample file by removing the `.sample` extension:

   ```bash
   mv pre-commit.sample pre-commit
   ```

3. Open the script in your favorite text editor and modify it based on the task you want to automate.

### Step 4: Make the Script Executable

Git hooks are shell scripts, so they need to be executable in order to run. Make the script executable with the following command:

```bash
chmod +x pre-commit
```

### Step 5: Add Custom Logic to the Hook Script

For instance, let's add a simple logic to the `pre-commit` hook to run a linter before every commit. Edit the `pre-commit` file and add the following script:

```bash
#!/bin/sh
# Run a linter before every commit
echo \"Running linter...\"
eslint . || exit 1
```

### Step 6: Test the Hook

Once the hook is set up, test it by making a commit. If the hook works correctly, the linter will run before the commit is finalized. If the linter fails, the commit will be blocked.

### Step 7: Automate Multiple Hooks

You can set up multiple hooks, such as `pre-push`,`commit-msg`, and`post-merge`, to automate different tasks.

For example, to prevent commits with messages that don't follow a specific pattern, you can modify the `commit-msg` hook:

```bash
#!/bin/sh
# Ensure commit message follows the pattern \"JIRA-123: Message\"
if ! grep -qE \"^JIRA-[0-9]+: .+\" \"$1\"; then
  echo \"Error: Commit message must follow the format 'JIRA-123: Message'\"
  exit 1
fi
```

### Step 8: Use Hook Templates

If you want to reuse the same hooks across multiple repositories, consider storing the hook scripts in a shared directory and linking them to your Git repository.

### Step 9: Share Hooks with Your Team

If you're working in a team, you may want to share Git hooks with your team members. Since hooks are not versioned by default, you can add the scripts to a shared directory and have all team members link to the same hook files.

1. Create a `hooks/` directory in your project.
2. Place the hook scripts inside this directory.
3. Use symbolic links to link them into `.git/hooks/`.

### Step 10: Use Third-Party Tools

There are several third-party tools, such as **Husky** or **lint-staged**, which can help automate Git hook management, especially for JavaScript projects. These tools simplify the process of setting up and managing multiple hooks.

## Notes, Cautions, and Warnings

- **Ensure Hooks Do Not Block Development**: Make sure your hooks do not impede development. If a hook takes too long to execute or fails on common actions, it can slow down the development process.
- **Be Careful with Team-Wide Hooks**: When sharing Git hooks, make sure all team members are using the same scripts, as hooks are local to each repository.
- **Debugging Hooks**: If your hook isn't working as expected, you can add debugging output (e.g., `echo` statements) to help diagnose issues.

## Conclusion

Git hooks are a fantastic way to automate tasks and enforce best practices in your development workflow. By using hooks such as `pre-commit`, `commit-msg`, and `pre-push`, you can automate repetitive tasks, ensure quality, and streamline the development process.

Remember to make your scripts as efficient as possible and share them with your team to ensure consistency across your projects. With the right setup, Git hooks can save time, prevent errors, and make collaboration much smoother.

---

### Graphics

You could include graphics here such as:

1. **A flowchart of Git hook execution**: A simple diagram showing when each Git hook gets triggered in the Git lifecycle.
2. **Code snippets**: Example scripts for common hooks like `pre-commit` or `commit-msg`.
3. **Team collaboration**: Diagram showing how shared hooks can be used across different repositories or team members.
