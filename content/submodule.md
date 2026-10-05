---
title: Git Submodules
---

Git submodules are a powerful way to leverage git as an external dependency management tool.
They allow a git repository to get other repositories as subdirectories. Git submodules are simply a reference to another repository at a particular snapshot in time. Git submodules enable a Git repository to incorporate and track version history of external code.

## When to use

- When working in a multi-repositories project
- When using the same libraries in several projects

## Workflow

If you want to launch a project on your local environment, clone the parent project (ie. the one with all the submodules inside).
The repository downloads the other ones, after that, you can work on the service you want by clicking the subdirectory of the service.
You can also launch the project on your local environment by reading the documentation in the parent repository.

When working with submodules, a common pattern of confusion is forgetting to push updates for remote users.
When you commit changes to a service in the parent repository, don't forget to update the child repository as well.
