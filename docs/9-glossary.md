# Glossary

## Version Control System (VCS)

   A **Version Control System** is a tool used to track changes in files over time, especially in software development. It makes it easier for developers to collaborate and revert the source code.

## Distributed System

   A **Distributed System** refers to a system that has multiple copies available on different machines.

## Branching

   **Branching** allows developers to create separate lines of development within the same project. Branches are independent of each other, and changes can be merged into each other. Branching helps organize features, bug fixes, and experiments without affecting others.

## Merging

   **Merging** integrates changes from one branch into another, so that the entire team benefits from the updates.

## Commit

   A **Commit** is a snapshot of changes made to the codebase. When a developer makes changes to files and saves them in Git, they can "commit" those changes with a message describing what was done. Each commit is uniquely identified by a hash and represents a point in the project’s history.

## Repository (Repo)

   A **Repository** is a storage location for a project’s code and its version history. A repository contains all the files and the metadata (commit history, branches, etc.) that Git tracks. A repository can be local (on your machine) or remote (hosted on a server like GitHub or GitLab).

## Clone

   **Cloning** is the process of creating a copy of a remote repository on your local machine. When you clone a repository, you get the entire project history, including all branches and commits, allowing you to work on the project locally and push changes back to the remote repository.

## Push

   A **Push** is the action of sending your local commits to a remote repository, making your changes available to other team members. Pushing is essential for collaboration as it shares your progress with others and syncs your local changes with the remote version of the repository.

## Pull

   A **Pull** is the action of fetching changes from a remote repository and merging them into your local copy of the repository. It ensures that your local repository is up to date with the latest changes made by other contributors.

## Fork

   **Forking** is a process used in open-source projects where a developer creates a personal copy of someone else’s repository. This allows them to make changes to the codebase independently, and later propose their changes (via a pull request) to be merged into the original project.

## Conflict

   A **Conflict** occurs when two developers make changes to the same part of a file (or the same file) in different branches. Git cannot automatically merge these changes, and the developer must manually resolve the conflict before proceeding.

## Checkout

   **Checkout** is a command used in Git to switch between different branches or to restore a file to a specific version. When you `checkout` a branch, you tell Git to update your working directory to reflect the contents of that branch.

## Tag

   A **Tag** is a reference to a specific point in Git’s history, often used to mark release versions (e.g., `v1.0`). Tags are like commits, but they are usually meant to mark important milestones in the development lifecycle, such as releases.

## Merge Conflict

   A **Merge Conflict** happens when Git is unable to automatically reconcile differences between two branches during the merge process. This typically occurs when two developers modify the same line of code in a file, and Git cannot decide which version to keep. Developers must manually resolve these conflicts.
