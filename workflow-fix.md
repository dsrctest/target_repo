# GitHub CLI Organization Repository Creation Fix

## Problem
The error shows `unknown flag: --org` when trying to create a repository in an organization.

## Solution
Modern GitHub CLI versions don't use the `--org` flag. Instead, repository names should be specified as `org/repo-name`.

## Correct Syntax:

### ❌ Wrong (Old Syntax):
```bash
gh repo create "$REPO_NAME" \
  --org "dsrctest" \
  --private \
  --description "Description"
```

### ✅ Correct (Modern Syntax):
```bash
gh repo create "$ORG_NAME/$REPO_NAME" \
  --private \
  --description "Description"
```

## Example:
```bash
# Create repository in dsrctest organization
ORG_NAME="dsrctest"
REPO_NAME="my-new-repo"

gh repo create "$ORG_NAME/$REPO_NAME" \
  --private \
  --description "My repository description"
```

This creates `dsrctest/my-new-repo` in the organization.
