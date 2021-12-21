---
name: "Contribution Guidelines"
about: "We do all of our development [on GitHub](https://github.com/ScoopInstaller/). If you are not familiar with GitHub or pull requests, [here is an excellent guide to get started](https://guides.github.com/activities/hello-world/)."
title: "Contribution Guidelines"
source: "https://github.com/creativecommons/creativecommons.github.io-source/blob/master/content/contributing-code/contents.lr"
---

## Finding an issue

Here's a list of [all our current repositories](https://github.com/orgs/ScoopInstaller/repositories). We use GitHub issues to track the work associated with each repository. That's where you can find things to work on.

We make extensive use of issue labels to designate the priority, status and beginner-friendliness of various issues. 
<!-- 
We have a standard set of labels across all projects, [documented here](/contributing-code/repo-labels/). Here are some of the ones that are most relevant to finding a good issue to work on:

- **Issues available for community contribution:**
  - The following tags mark issues that are open for community contribution:
    - <span class="gh-label friendliness">help-wanted</span> : Open to participation from the community but not necessarily beginner-friendly
    - <span class="gh-label friendliness">good first issue</span> : Open to participation from the community and friendly towards new contributors
  - You do not need our permission to work on one of these issues.
  - You may work on an issue labeled <span class="gh-label friendliness">good first issue</span> even if it's not your first issue.
* **Issues not available for community contribution:**
  - The following tags mark issues that are _not_ open for community contribution:
    - <span class="gh-label friendliness">🔒 staff only</span> : Requires infrastructure access or institutional knowledge that would be impractical to provide to the community
  - Do not work on these.
- **Issues not ready for work:**
  - The following tags mark issues that are _not_ open for community contribution:
    - <span class="gh-label status-neutral">🚧 status: blocked</span>: Blocked by other work that needs to be done first
    - <span class="gh-label status-dark">🧹 status: ticket work required </span>: Needs additional work before it is ready to be taken up
    - <span class="gh-label status-darker">🚦 status: awaiting triage</span>: Has not been triaged by a maintainer
  - Do not work on these.
- **Issues without any of the above labels:**
  - These issues _may_ (or may not) be open for contribution.
  - Please add a comment asking one of the maintainers to triage the issue and label it as appropriate.

You can use our [Issue Finder tool](/contributing-code/issue-finder/) to find a good issue that matches your skills and familiarity with our software and community.
-->

Some helpful saved searches on GitHub than can assist with finding an issue:
- [issues labeled <span class="gh-label friendliness">good first issue</span>](https://github.com/search?q=org%3AScoopInstaller+is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22+-linked%3Apr)
- [issues labeled <span class="gh-label friendliness">help-wanted</span>](https://github.com/search?q=org%3AScoopInstaller+is%3Aissue+is%3Aopen+label%3A%22help-wanted%22+-linked%3Apr)
- [PRs labeled <span class="gh-label friendliness">help-wanted</span>](https://github.com/search?q=org%3AScoopInstaller+is%3Apr+is%3Aopen+label%3A%22help-wanted%22)

Check the issue comments/labels to see whether someone else has indicated that they are working on it. If someone is already working on it and there has been activity within the last 7 days, you may want to find a different issue to work on.

## Contribution process

Once you've found an issue you'd like to work on, please follow these steps to make your contribution:

### For Scoop core:

1. Comment on it and say you're working on that issue. This is to avoid conflicts with others also working on the issue.
2. Fork the repository and create a new branch from the `develop` branch, with an appropriate name.
3. Write your code and run tests to check for regressions.
4. Update the tests (if required) and update documentation.
5. Submit your pull request. For PR titles, follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.2/#commit-message-with-scope).
6. Wait for code review and address any issues raised as soon as you can.

### For Scoop buckets:

1. Comment on it and say you're working on that issue. This is to avoid conflicts with others also working on the issue.
2. Fork the repository and create a new branch from the default branch (usually `master`), with an appropriate name.
3. Write your code. Follow these guidelines for writing manifests:
    * Read the Wiki on how app manifests work - [App Manifests](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests) - and how to create one - [Creating an App Manifest](https://github.com/ScoopInstaller/Scoop/wiki/Creating-an-app-manifest).
    * Follow this general order of fields (whichever exist) in the JSON file:
      - `version`
      - `description`
      - `homepage`
      - `license`
      - `notes`
      - `depends`
      - `suggest`
      - `url`
      - `hash`
      - `extract_dir`
      - `extract_to`
      - `pre_install`
      - `installer`
      - `post_install`
      - `env_add_path`
      - `env_set`
      - `bin`
      - `shortcuts`
      - `persist`
      - `uninstaller`
      - `checkver`
      - `autoupdate`
    * Use a tab width of 4 spaces.
    * Portable configuration is highly preferred (by using `persist`).
    * If the program file is a CLI application, no need to add it in `shortcuts`.
    * If the program file is a GUI application _and_ it doesn't accept any commandline arguments, no need to add it in `bin`.
    * If an array contains only one item, write it as a string.
    * If the application provides _only_ a 32bit download, the `architecture` field is not required. In all other cases, `architecture` field is mandatory.
5. Test your manifest by installing, uninstalling, checking functionality, persistence etc.
6. Confirm that manifest gets updated automatically - see [App Manifest Autoupdate](https://github.com/ScoopInstaller/Scoop/wiki/App-Manifest-Autoupdate).
7. Submit your pull request. Titles should follow these rules:
    * If it's a new manifest, use `<app name>: Add version <version>`.
    * If it's an update to an existing manifest, use `<app name>@<version>: <small description>`.
    * If it's something related to maintenance, use `(chore): <small description>`.
8. Add a comment starting with "/verify" after raising the PR - this will kick in the automatic manifest verifier.
9. Wait for code review and address any issues raised as soon as you can.

**A note on collaboration:** We encourage people to collaborate as much as possible. We especially appreciate contributors reviewing each others pull requests, as long as you are [kind and constructive](https://medium.com/@otarutunde/comments-during-code-reviews-2cb7791e1ac7) when you do so.

## Proposing a new issue

If you want to work on something that there is no GitHub issue for, follow these steps:

1. Create a new GitHub issue associated with the relevant repository and propose your change there. Be sure to include implementation details and the rationale for the proposed change.
    * We are very reluctant to accept random pull requests without a related issue created first.
2. Wait for a project maintainer to evaluate your issue and decide whether it's something that we will accept a pull request for.
3. Once the project maintainer has approved the issue, you may start work on code as described in the **Contribution process** section above.

When in doubt, ask a question in the Discussions tab of the relevant repository.
