---
title: Commit messages
---

*This is a simplifed version of the original conventional commits.*

Following those rules to write your commit messages will bring great advantages to a project :

- Readable nature of changes to teammates, the public, and other stakeholders.
- Automatic trigger of build and publish processes.
- Easier contribution to the project for new developers, by allowing them to explore a more structured commit history.
- Automatic changelogs capability.
- Automatic semantic version bump (based on the types of commits landed).

The message is structured as follows:

```
<type>(<scope>): [<#ticket>] <description>

```

## Types

They are based on the [Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines) and must be one of the following:

- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
- **doc**: Documentation only changes
- **feat**: A new feature
- **fix**: A bug fix
- **perf**: A code change that improves performance
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- **test**: Adding missing tests or correcting existing tests
- **chore**: Changes to the build process or auxiliary tools and libraries
- **revert**: Revert a previous commit. In this case it should begin with "revert:", followed by the header of the reverted commit. In the body it should say: This reverts commit <hash>., where the hash is the SHA of the commit being reverted.

## Scope

The scope should be the name of the updated component.

## #ticket

The id of the ticket you are working on in this commit. Each commit must link to a work item in your ticketing system.

## Description

A succinct description of the change:

- Use the imperative, present tense: "change" not "changed" nor "changes"
- Don't capitalize letters
- No dots (.)

## Additional Rules

- **fix:** Patches a bug in your codebase (this correlates with PATCH in semantic versioning).
- **feat:** Introduces a new feature to the codebase (this correlates with MINOR in semantic versioning, or MAJOR in case of a BREAKING CHANGE).
- **Additional types:** are not mandated by the conventional commits specification, and have no implicit effect in semantic versioning (unless they include a BREAKING CHANGE).
- **Breaking change:** A commit that start with "BREAKING!" in the description introduces a breaking API change (correlating with MAJOR in semantic versioning). A BREAKING CHANGE can be part of commits of any type.

## Examples

```bash
git commit -m "feat(lang): [#346] add polish language"
git commit -m "feat(parser): [#546] add ability to parse arrays"
git commit -m "feat(config): [neo-118] BREAKING! allow provided config object to extend other configs"
```

## AI-Assisted Commit Messages with GitHub Copilot

GitHub Copilot in Visual Studio Code can generate commit messages from your staged changes. Review the suggestion and make sure it follows the [Conventional Commits](https://www.conventionalcommits.org/) rules above.

Benefits:

- Reduces the time spent writing commit messages.
- Maintains consistency with the Conventional Commit format.

### How to use Copilot for Conventional Commits

1. **Stage your changes.** Open the **Source Control** panel in VS Code (`Ctrl+Shift+G` on Windows/Linux or `⌘+Shift+G` on macOS) and stage your files.
2. **Generate a commit message.** In the commit message field at the top, click the **Copilot icon**. Copilot suggests a message based on your changes.
3. **Check the format.** If necessary, adjust the type (`feat:`, `fix:`, `doc:`, etc.) and make sure the message is concise and descriptive. For example: `feat(auth): [#123] implement email verification during signup`
4. **Commit and push.** Commit with `Ctrl+Enter` / `Cmd+Enter`, then run `git push`.

### Tips

- To encourage Copilot to follow the convention, start typing with the correct type (e.g. `feat: `) before invoking suggestions.
- In `settings.json`, make sure Copilot is enabled for the Source Control input field:

```json
"github.copilot.enable": {
  "*": true,
  "plaintext": true,
  "scminput": true
}
```
