# Gitflow

The key premise of Gitflow is that each commit to your primary branch (main) represents a release and a secondary branch, develop, is used for ongoing development. New features are built on feature branches and then reviewed and merged into the develop branch. When changes are ready to be released, a release branch is created, and when the release is complete that branch is merged into the primary branch.

Gitflow is most effective for teams that follow an extensive release management process that prevents continuous deployment, particularly if multiple stakeholders need to approve a release before it goes live. The release branch acts as a gatekeeper.

It however no longer alignes with the modern, continuous delivery based development.

# Trunk Based Development (TBD)

In trunk based development, developers merge small, frequent updates to the primary or "trunk" branch. Idiomatic trunk based development has developers committing directly to the primary branch, however it is common for teams to use short lived feature branches to support code reviews and automated checks prior to merging, this variant can sometimes be referred to as scaled trunk based development or feature branch workflow. Releases are done directly from the primary branch and since you are already deploying on all commits to the primary branch, fixes to deployed code is treated no different from any other code change.

This workflow is ideal for teams that utilise continuous deployment