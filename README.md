# Shared Documentation Sync

[![Sync Docs](https://github.com/erifyc1/CREATE-shared/actions/workflows/sync-docs.yml/badge.svg)](https://github.com/erifyc1/CREATE-shared/actions/workflows/sync-docs.yml)

This repository automatically syncs the `documentation/` folder into multiple repositories using GitHub Actions.

## How it works

-   On any change inside `documentation/`, the GitHub Action runs.
-   It clones each repo listed in `repos.txt`.
-   It removes the old `documentation/` folder.
-   It copies the updated `documentation/` folder.
-   It commits and pushes the changes.

## Repository structure

.  
├── .github/workflows/sync-docs.yml  
├── documentation/  
├── repos.txt  
└── README.md

## Setup

1. Add repository names (one per line) to `repos.txt`.
2. Create a GitHub secret `GH_TOKEN` with repo write access.

Example `repos.txt`:

```
repo-one
repo-two
repo-three
```

## Notes

-   Old `documentation/` folders are fully replaced.
-   No commit is made if there are no changes.
-   The GitHub token must have permission to push to the target repositories.

---

## Ignore cloned repos during local testing (.gitignore)

```
repo-one/
repo-two/
repo-three/
```
