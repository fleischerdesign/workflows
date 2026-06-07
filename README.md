# workflows

Reusable GitHub Actions workflows.

## Workflows

### merge-back

Automatically merges changes from a head branch into a base branch via pull request.
Uses GitHub's native auto-merge — the PR is merged automatically once all required
status checks pass.

**Inputs**

| Input | Default | Description |
|-------|---------|-------------|
| `base-branch` | `develop` | Branch to merge into |
| `head-branch` | `main` | Branch to merge from |
| `pr-title` | `chore: sync develop with main` | Pull request title |
| `pr-body` | `Automated merge-back after push to main.` | Pull request body |

**Usage**

```yaml
name: Merge Back

on:
  push:
    branches: [main]

jobs:
  sync:
    uses: fleischerdesign/workflows/.github/workflows/merge-back.yml@v1
    secrets: inherit
```

**Custom branches**

```yaml
jobs:
  sync:
    uses: fleischerdesign/workflows/.github/workflows/merge-back.yml@v1
    with:
      base-branch: staging
      head-branch: develop
    secrets: inherit
```
