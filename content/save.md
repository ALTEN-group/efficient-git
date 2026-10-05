---
title: Save
---

Git is not meant to be used as a backup device.

But let's be pragmatic here as not every company has a proper way of backing up developers work every day.

As said before the core function of Git is to save checkpoints. Thus, if used properly, Git is a powerful backup application for developers and can save you from losing several days of work in case of problem.

## Overview

This backup routine should be done every evening when you leave work.
And every morning when you start your day in order to recover your work as you left it the day before. 

Note that you only need to do this if your current work is sufficiently started since the last commit you have pushed and the current state is not mature enough for a proper intermediary conventional commit.

**If you can commit properly just do it and push.** This is the simplest way to backup your work.

## Step 1: Save your work

You are leaving for the day and started to work on a new branch. Your job is not finished yet, nothing is working yet so an intermediate commit would not be right.
It is then time to backup your work in case your computer does not start tomorrow morning.

*These commands only work if it is the first time you are saving your work on this branch. If it is not the case please jump to step 4.*

```bash
git status
git add .
git commit -m "WIP"
git push
```

or the short version if you added [aliases from this documentation](../alias)

```bash
git s
git a .
git c "WIP"
git ph
```

Your work is safe now.


## Step 2: Retrieve your backup

If your computer died during the night and is not starting up anymore, you can pull your save to another computer and work as if nothing happened. The backup saved you from starting from scratch again.

Hopefully, most of the time, you will not have any issue during the night. You can work on your task as usual.

## Step 3 (Optional): clean your branch on the remote repository

The next morning you may want to reset your commit on your local branch so you can keep seeing your modifications in your IDE:

```bash
git reset HEAD~1
```
Now your backup commit is reset in the local repository. This also means your local branch diverged compared to the remote branch.
Thus you want to get your remote branch up to date. To do so you need to pull the remote in order to revert it:

```bash
git stash
git pull 
git revert HEAD
git push
git stash apply
```

Now your "WIP" commit is reverted in the remote branch head but still exists in the remote as an older commit if needed.

## Step 4: Save your work again after a previous backup

This is the end of the second day working on this feature.
You want to backup again before leaving for the day.

Repeat step 1.

## Step 5: Finish your work

Once this feature is done, commit it and create your merge request with the squash option checked, because we only want to see one commit per user story in the development branch.
