---
title: Branches
---

- **master** | **main**: For production releases.
- **develop**: For next release development.
- Available branch prefixes for developers :
  - **feat**: For new feature to develop. Or anything else which do not fit into other prefixes below. 
  - **release**: When release cycle is over. Features ready to ship are kept here. Freeing develop branch for next cycle.
  - **fix**: For new bug to fix or hotfix required on master branch.
  - **doc**: To improve or update developer documentation.
  - **test**: To add or update unit tests or E2E tests.

Each branch must link to a work item in your ticketing system. Except for "release" which must link to a version of the application.

## Feature branch

From : **develop**

Each new feature should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When a feature is complete and tested, it gets merged back into develop. Features never interact directly with master.

When a feature is way behind develop because of a long development process, merge develop into the feature branch to stay tuned.

```bash
git checkout develop
git pull
git checkout -b feat/#245/csv-export
```

## Release branch

From : **develop**

Once develop has acquired enough features for a release or a predetermined release date is approaching, you fork a release branch off of develop.

Creating this branch starts the next release cycle, so no new features can be added after this point, only bug fixes, documentation generation, and other release-oriented tasks should go in this branch.

Once it's ready to ship, the release branch gets merged into master and tagged with a version number. In addition, it should be merged back into develop, which may have progressed since the release was initiated.

Using a dedicated branch to prepare releases makes it possible for one team to polish the current release while another team continues working on features for the next release. It also creates well-defined phases of development.

The release version name must follow the [Semantic versionning rules](../semantic-versioning/)

```bash
git checkout develop
git pull
git checkout -b release/0.1.0
```

## Bugfix branch

From : **develop**

Each new bug fix should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When a bug fix is complete and tested, it gets merged back into develop. Bugfixes never interact directly with master.

```bash
git checkout develop
git pull
git checkout -b fix/#456/export-button-color
```

## Hotfix branch

From : **master**

Used to quickly patch production critical issues.

This is the only branch that should fork directly off of master. As soon as the fix is complete, it should be merged into master, develop and the current release branch if there is one. Then master should be tagged with an updated version number.

Having a dedicated line of development for hotfixes lets your team address issues without interrupting the rest of the workflow or waiting for the next release cycle.

```bash
git checkout master
git pull
git checkout -b fix/#344/wrong-email-regex
```

## Refactor branch

From : **develop**

Technical debt reduction, linter/SonarQube/security improvements.

Each refactor should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When refactor is complete and tested, it gets merged back into develop. Tests never interact directly with master.

```bash
git checkout develop
git pull
git checkout -b feat/#426/export-csv-class
```

## Doc branch

From : **develop**

Each documentation update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

Doc branch is only for developer documentation in order to improve collaboration in the team.
User documentation update has to be developed in a feature branch.

When documentation is complete, it gets merged back into develop. Documentations never interact directly with master.

```bash
git checkout develop
git pull
git checkout -b doc/#112/user-erd
```

## Test branch

From : **develop**

Each test update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When test is complete, it gets merged back into develop. Tests never interact directly with master.

```bash
git checkout develop
git pull
git checkout -b test/#821/csv-export
```

## Build branch

From : **develop**

Each build update should reside in its own branch, which can be pushed to the central repository for backup and collaboration.

When build is complete and tested, it gets merged back into develop. Builds never interact directly with master.

```bash
git checkout develop
git pull
git checkout -b feat/#514/gitbranchvalidator
```
