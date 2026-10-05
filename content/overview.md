---
title: Getting Started
---

## Create a repo

In a new folder on your computer type :

```bash
git init
```

This will create a hidden .git folder inside your current folder — this is the "repository" (or repo) where git stores all of its internal tracking data.
Any changes you make to any files within the original folder will now be possible to track.

The original folder is now referred to as your **working directory**, as opposed to the repository (the .git folder) that tracks your changes. You work in the working directory.

## Clone an existing repo

```bash
git clone https://github.com/xxx/xxxx.git
```

This will download a .git repository from the internet (GitHub) to your computer and extract the latest snapshot of the repo (all the files) to your working directory. By default it will all be saved in a folder with the same name as the repo.

The URL you specify here is called the **remote origin**. The place where the files were originally downloaded from.

## Status of your project

```bash
git status
```

Or the short version if you added [aliases from this documentation](../alias)

```bash
git s
```

This will print current state information of the branch, such as which files have recently been modified.

Here is the list of possible outputs for a file :   

| Name | Description |
|------|-------------|
| M | Modified |
| T | File type changed (regular file, symbolic link or submodule) |
| A | Added |
| D | Deleted |
| R | Renamed |
| C | Copied |
| U | Updated but unmerged |

You should check your status anytime you are about to do git commands.

## Fetch the latest info about a repo

```bash
git fetch
```

Retrieve the latest meta-data info from the remote repository. It does not transfer any file. It only checks if changes are available on all the different branches stored in the remote.

## Pull the latest changes

```bash
git pull
```

Incorporates changes from a remote repository into the current local branch. If the current branch is behind the remote, then by default it will fast-forward the current branch to match the remote. If the current branch and the remote have diverged, `git pull` runs `git fetch` and then depending on configuration options or command line flags, will call either `git rebase` or `git merge` to reconcile diverging branches.

## Checkout a branch

Switch to an existing branch

```bash
git checkout <existing-branch-name>
git pull
```

or

```bash
git switch <existing-branch-name>
git pull
```

You can think of this as “resuming” from an existing checkpoint. All your files will be reset to whatever state they were on that particular branch.

Any uncommitted change in your working directory will prevent you from switching branch. See git stash for a simple way to avoid unwanted commits.

You can use the -b flag as a shortcut if you want to create the new branch while checking it out in one step:

```bash
git pull
git checkout -b <new-branch-name>
```

## Create a new branch

For more information about proper naming of branches please refer to the [Gitflow/branch](../branch) chapter.

You can think of this as creating a local “checkpoint” and giving it a name. It is similar to File > Save as… in a text editor; the new branch created is a reference to the current state of your repository. The branch name can then be used in various other commands.

When working on a project, every time you start a new feature, a bug fix or anything else, you start by creating a new branch from "develop", "release" or "master". The choice of the branch you start from depends on the work you have to do. It usually is "develop".

The following commands will update the state of your local repository from the remote, then create a new branch.

```bash
git pull
git branch <new-branch-name>
```

Or

```bash
git pull
git checkout -b <new-branch-name>
```

You are now working on the new branch.

## Difference between checkpoints

After editing some files, you can simply type git diff to view a list of the changes you have made. This is a good way to double-check your work before committing it:

```bash
git diff <branch-name> <other-branch-name>
```

For each group of changes, you will see what the file used to look like (prefixed with - and colored red), followed by what it looks like now (prefixed with + and colored green).

## Stage your changes

Tell Git which files should be included in your next commit:

```bash
git add <files>
```

After editing some files, this command will mark any changes you’ve made as “staged” (or “ready to be committed”).

If you then go and make more changes, those new changes will not automatically be staged, even if you’ve changed the same files as before. This is useful for controlling exactly what you commit, but also a major source of confusion for newcomers.

If you’re ever unsure, just type git status again to see what’s going on. You’ll see “Changes to be committed:” followed by file names in green. Below that you’ll see “Changes not staged for commit:” followed by file names in red. These are not yet staged.

As a shortcut, you can use wildcards just like with any other terminal command. For example:

```bash
git add README.md app/*.txt
```

This will add the file README.md, as well as every file in the app folder that ends in .txt. 

You can also add everything that’s changed like this :

```bash
git add .
```

## Commit your staged changes

A commit records changes to the repository.

It will add a checkpoint locally. The name of the commit will be a random-looking hash of numbers and letters such as *e093542*. This hash can then be used in various other commands just like branch names.

The commit message is important to help other people understand what was changed and why you changed it. The chapter about [conventional commits](../conventional-commit/) explains how to write useful commit messages.

You must use the -m flag to write a message. For example:

```bash
git commit -m "<conventional-commit-message>"
```

Or use the short version if you added [aliases from this documentation](../alias)

```bash
git c "<conventional-commit-message>"
```

## Push your branch on the server

This will upload your branch to the remote origin (the URL defined initially during clone).
After a successful push, your teammates will then be able to pull your branch to view your commits.

```bash
git push
```

Or the short version if you added [aliases from this documentation](../alias)

```bash
git ph
```

## Merge changes from somebody else

```bash
git checkout <other-branch-name>
git pull
git checkout <current-branch-name>
git merge <other-branch-name>
```

This will take all commits that exist on the other branch and integrate them into your own current branch.
You should do it every morning from develop.
This uses whatever branch data is stored locally, so make sure you have run "git pull" first to download the latest info of the branch you want to merge.
For a deeper understanding of how merging works and how conflicts are resolved [see the merge page](../merge/).
