# semantic-basic

Extended semantic-release environment

# Branching strategy

Branching strategy is [Trunk Based Development](https://trunkbaseddevelopment.com/) [short-lived feature branches](https://trunkbaseddevelopment.com/short-lived-feature-branches/):

```mermaid
gitGraph
    commit
    commit
    branch release-1
    checkout release-1
    commit
    branch feature
    checkout feature
    commit
    commit
    checkout release-1
    merge feature
    branch fix
    checkout fix
    commit
    checkout release-1
    merge fix
    commit
    commit
    checkout main
    merge release-1
    commit
```

Notes:

- Use squash and merge strategy (all commits from child branch are squashed into single one) for feature and fix branches to merge into release branch
- Use rebase and merge strategy (all commits from release branch are moved to upstream branch, e.g. like fast-forward merge) for release branches
- Don't create next release branch until current release branch is merged to upstream (otherwise you'll need to rebase next release branch from time to time)  
