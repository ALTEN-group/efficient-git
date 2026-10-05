---
title: Teamwork
---

## Commit your work


### Description

A commit contains the current contents of the index and the given log message describing the changes.

The new commit is a direct child of HEAD, usually the tip of the current branch, and the branch is updated to point to it (unless no branch is associated with the working tree, in which case HEAD is "detached").

### When

When you finish a sub task. 
It is a good practice to commit several times a day, every time it feels logical to you. It helps keeping commits short, easy to understand and easy for you to describe in a commit message.
It also helps create several checkpoints so in case of issue you have several moment you can go back to or read.

The commit message is important to help other people understand what was changed and why you changed it. There’s a brief guide [here](../conventional-commit/) explaining how to write useful commit messages.

### How

Usually you want to commit all your changes. If not you can add only the files you want to using "git add <file-name>".
After your commit is done you can push it on the remote branch : 

```bash
git status
git add .
git commit -m "<conventional-commit-message>"
git push
```

Or the short version if you added [aliases from this documentation](../alias)

```bash
git s
git a .
git c "<conventional-commit-message>"
git ph
```

## Stay up to date

Pull the trunk into your branch every morning to stay up to date with the rest of the team and fix small conflicts early.
It prevents massive conflicts or bugs if you wait too long before updating your branch.
It also lets you react quickly if the work submitted the day before is not compatible with what you are working on.

```bash
git checkout develop
git pull
git checkout <current-branch-name>
git merge develop
```


## Submit your changes

After working on a new feature for the team you have your changes ready and tested on a branch.
It is time to get them back onto the trunk as part of the “official” codebase.

**Once you’ve tested your changes**, you’ll do this via a pull request (PR) or a merge request (MR) — they’re the same thing, the term just depends on what software you’re using (e.g. GitHub/Bitbucket/GitLab). You’re requesting that your changes be pulled in and merged.

A merge request is done via the application used in the project : Github or Gitlab

Your team will be happy to receive new PRs, even if the code needs a bit of work before being accepted. PRs are an important part of the open-source ecosystem.

It is good practice to open the PR as a draft (WIP) as soon as you create your branch, so your team can follow along. Remove the "WIP" mention and ask for a review when you are ready.

The main thing to remember is to include a clear explanation of why you’re making the changes in order to give context.

### Discussing and revising

Once you submit your PR, someone else on the team will need to look it over and leave feedback. They can ask questions and comment on specific lines of code, or they can give more general feedback about your changes. In some cases they may push their own changes directly to your branch, but usually they’ll ask you to make the changes yourself.

**If you want to make changes based on the feedback, simply add more commits to your existing branch and push it to origin again. The PR will update automatically to reflect your changes.**

## Stale branch

If some time goes by before your PR is accepted, it might get “stale”, meaning it’s based on an older version of the trunk. Your changes may have worked a week ago, but there’s no guarantee that they still work alongside other, more recent changes to the trunk.

To get up to date, “merge in” the trunk changes into your branch:

```bash
git checkout develop
git pull
git checkout <current-branch-name>
git merge develop
```

This will apply any new changes from the trunk on top of your work.

You are effectively just moving your branch up to the top of the trunk to stay up to date with the latest code.

Some people may prefer "rebase" method; **it is safer and easier to merge.**

## Deal with conflicts

When merging, you will occasionally run into conflicts. This means you changed a line of code that someone else also changed, and git doesn’t know which version to keep.

Note that this is a normal behaviour and you should not be afraid or annoyed by conflict. Fix them safely, and ask for help if you have doubts.

When conflicts happens the output from git has weird >>>>>>> ======= <<<<<<< symbols.

In essence, you just need to remove those weird symbols and manually combine the code in between them.

For example, the line:

print "Hello"
Might be changed on two separate branches, leading to the conflict:

```bash
>>>>>>>
print "Hello, world"
=======
print "Hello!"
<<<<<<<
```

Which, when resolved, might become:

```bash
print "Hello, world!"
```

After manually merging the conflicting lines together — keeping both the “world” and the “!”, which had each been added separately.

## Accepting your changes

Once all of the PR comments have been addressed and any conflicts have been resolved, your branch is ready to be merged!

An administrator of the codebase can accept the PR by merging your branch into the trunk — simply by pressing a button on GitHub/GitLab — thus making your changes official.

## Squash merge

Squash merging is a merge option that allows you to condense the Git history of topic branches when you complete a pull request. Instead of each commit on the topic branch being added to the history of the default branch, a squash merge adds all the file changes to a single new commit on the default branch.

When you merge using Gitlab or Github there is a checkbox to squash all the commits into one. It is highly recommanded to use it in order to keep a clean history on the default branch.

A simple way to think about this is that squash merge gives you just the file changes, and a regular merge gives you the file changes and the commit history.

When squash merging, it's a good practice to delete the source branch. Deleting the source branch prevents confusion as the topic branch itself doesn't have a commit merging it into the default branch.

