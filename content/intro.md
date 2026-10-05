---
title: What is Git
mermaid: true
---

**Git** is the most popular Version Control System.  
It tracks file changes in a project.  
You can determine exactly what changed, who changed it, and why.

## Checkpoints

**The core function of git is to create checkpoints and share them with other people**. Everything in Git revolves around this concept.
If you’ve ever created a checkpoint to something, you’ll be able to get back to it later as long as your .git folder is intact.

**It is mandatory for coordinating work among multiple people on a project**, and for tracking progress over time by saving those checkpoints. 

Here’s a list of the different types of checkpoint :

```
HEAD, e.g. a ref that points to the tip (latest commit) of a branch
<branch-name>, e.g. a branch name like master or develop
<commit-hash>, e.g. a commit hash like e093542d01d11c917c316bfaffd6c4e5633aba58 (or e093542 for short)
<tag-name>, e.g. a release version : v1.0.0
```

Checkpoints are represented as circles in the diagram below : 

{{<mermaid>}}
    gitGraph
        commit
        commit tag: "1.0.0"
        branch develop
        commit
        branch feature_1
        commit
        checkout develop
        commit
        branch feature_2
        commit
        checkout feature_1
        commit
        checkout feature_2
        commit
        checkout develop
        commit
        checkout main
        commit
        commit tag: "1.0.1"
{{</mermaid>}}

## Tree

Every time you add a change, the tree grows. Even if you delete code, it is still considered a change and causes the tree to grow.
The main codebase is the trunk of a tree.

### Trunk

Git, by default, calls the trunk main or master. You can call it whatever you want; there’s nothing special about these words other than that it’s conventional.

You can travel up and down the trunk — equivalent to going forward and backward in time — by checking out specific “checkpoints” as described in [the overview](../gitflow).

### Branches

Projects have a backlog of new features to add and bugs to fix. When you want to address one of these issues, one way would be to grow the tree taller and commit directly to the trunk (master).

This works fine for small projects of one or two people making changes, but if more people are working at the same time, you will get in each other’s way and end up with conflicting changes.

The solution is branching. Instead of committing to the trunk, you [create your own branch](../branch) and work from there. Now, with each commit, you are growing your branch taller instead of the trunk.

While you were working on your branch from the trunk (e.g. "develop"), someone else may have merged new code from their branch to develop. 
Those commits are not in your branch yet; your branch is thus out of date but isolated and safe from possible issues.

You can see branch visualization by typing :

```bash
git log --all --decorate --oneline --graph
```

or the short version if you added [aliases from this documentation](../alias)

```bash
git l
```
