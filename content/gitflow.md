---
title: Gitflow overview
mermaid: true
---

Gitflow is the most used Git branching model that involves the use of feature branches and multiple primary branches. Compared to trunk-based development, Giflow has numerous, longer-lived branches and larger commits. 
Under this model, developers create a feature branch and delay merging it to the main trunk branch until the feature is complete. These long-lived feature branches require more collaboration to merge and have a higher risk of deviating from the trunk branch. They can also introduce conflicting updates.

**Gitflow can be used for projects that have a scheduled release cycle and for the DevOps best practice of continuous delivery.** This workflow doesn’t add any new concepts or commands beyond what has been already discussed.
In essence **Gitflow assigns very specific roles to different branches and defines how and when they should interact.**
It uses individual branches for preparing, maintaining, and recording releases. 
Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.

## Summary

The overall flow is as follow :
- **A develop branch is created from master.**
- **A release branch is created from develop**.
- **Feature, Fix, Doc, Test and Build branches are created from develop.**
- **When a feature is complete it is merged into the develop branch.**
- **When the release branch is done it is merged into develop then master on release date.**
- **If an issue in master is detected a hotfix branch is created from master.**
- **Once the hotfix is complete it is merged to both master and develop.**

Here is a Gitflow chart to summarize the method : 

{{<mermaid>}}
  gitGraph
    commit tag: "v1.0.0"

    branch release order: 3
    branch develop order: 5

    checkout develop
    commit

    branch bugfix_1 order: 6
    branch feature_1 order: 7

    checkout main
    commit
    branch hotfix_1 order: 2
    checkout hotfix_1
    commit
    checkout main
    merge hotfix_1 tag: "v1.0.1"

    checkout bugfix_1
    commit

    checkout feature_1
    commit

    checkout develop
    merge main

    branch feature_2 order: 8

    checkout bugfix_1
    commit

    checkout develop
    merge bugfix_1

    checkout feature_2
    commit

    checkout feature_1
    commit
    checkout develop
    merge feature_1

    checkout release
    merge develop tag: "v1.1.0-alpha"

    checkout release
    commit

    checkout feature_2
    commit
    checkout develop
    merge feature_2

    checkout release
    branch bugfix2 order: 4
    commit
    checkout release
    merge bugfix2

    checkout main
    merge release tag: "v1.1.0"
    checkout develop
    merge main
{{</mermaid>}}
