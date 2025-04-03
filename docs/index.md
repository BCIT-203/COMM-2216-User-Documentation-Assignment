# Introduction

## Welcome to Git’s World

**Git** is a distributed [version control system (VCS)](./9-glossary.md#version-control-system-vcs) that helps track changes to your codebase, collaborate with other developers, and maintain a history of your project. Whether you’re working solo or with a team, Git is an essential tool for managing your source code efficiently.

## Key Features

1. **Version Control**: Git tracks every change made to a project’s codebase, allowing users to view a complete history of their project.
2. **[Branching](./9-glossary.md#branching) and [Merging](./9-glossary.md#merging)**: Git allows users to create branches (independent lines of development) for different features or fixes, which can later be merged back into the main codebase.
3. [**Distributed System**](./9-glossary.md#distributed-system): Every user has a full copy of the [repository](./9-glossary.md#repository-repo), making it possible to work offline and still have access to the entire project history.
4. **Collaboration**: Git allows multiple developers to work on the same project concurrently, helping them merge their work and avoid conflicts.
5. **Code Integrity**: Git ensures that code remains consistent and protected from accidental changes by creating checkpoints ([commits](./9-glossary.md#commit)) and using checksums to verify data integrity.

## Intended Use

- **Software development**: Managing source code, version tracking, and collaborating in coding projects.
- **Team collaboration**: Helping developers coordinate, merge changes, and prevent code conflicts.
- **Open-source projects**: Facilitating contribution and community-driven development by enabling multiple contributors to work on the same codebase.
- **Backup and recovery**: Storing multiple versions of code to quickly revert or recover previous code states.

## Intended Readers

- **Software Developers**: Both novice and experienced developers who want to manage and collaborate on code projects efficiently.
- **DevOps Engineers**: Professionals who work on automating and managing software development pipelines.
- **Project Managers**: Individuals who oversee software development teams and need to understand version control and collaboration tools.
- **Open-Source Contributors**: Anyone looking to contribute to open-source projects, where Git is commonly used for version control.

## Common Git Commands

Here are some essential Git commands to get started:

| Command | Description |
|---------|------------|
| `git init` | Initialize a new Git repository in a project. |
| `git clone <repo-url>` | Copy an existing remote repository to your local machine. |
| `git status` | Check the status of files in your working directory. |
| `git add <file>` | Stage changes for the next commit. |
| `git commit -m "message"` | Save changes with a descriptive message. |
| `git push origin <branch>` | Upload local commits to a remote repository. |
| `git pull origin <branch>` | Fetch and merge changes from a remote repository. |
| `git branch` | List all branches in the repository. |
| `git checkout <branch>` | Switch to a different branch. |
| `git merge <branch>` | Merge a branch into the current branch. |
| `git log` | View commit history. |
| `git revert <commit>` | Undo a specific commit by creating a new commit. |
| `git reset --hard HEAD` | Discard all uncommitted changes and reset to the last commit. |

By using Git, you’ll be able to track your progress, collaborate effectively with your team, and ensure that your project is always in a stable state. Happy coding!

## Notes and Warning Messages

Throughout the document, you will come across two types of message blocks that provide relevant information: one for warnings and one for notes.

!!! Notes

- Contains relevent information that you should take note of.

!!! Warning

- Contains relevent warnings that should warn you.
