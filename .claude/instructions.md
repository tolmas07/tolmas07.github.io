# Instructions for AI Assistants

## Two-Branch Workflow (MANDATORY)

This repository uses a two-branch deployment system:

- **`main`** → Production site at https://tolmas07.github.io/
- **`test-improvements`** → Preview site at https://tolmas07.github.io/test/

### Rules

1. **ALWAYS** work on the `test-improvements` branch first
2. **NEVER** push directly to `main` without explicit user approval
3. After pushing to `test-improvements`, tell the user the preview URL
4. Only merge to `main` when the user explicitly says it's OK (e.g. "мерджим", "переводи в main", "looks good, merge it")

### Workflow

```
git checkout test-improvements
# make changes
git add -A
git commit -m "description"
git push origin test-improvements
# tell user to check https://tolmas07.github.io/test/
# WAIT for user approval
git checkout main
git merge test-improvements --no-edit
git push origin main
```

### Deployment

Both branches deploy automatically via GitHub Actions (`.github/workflows/static.yml`).
The workflow assembles both branches: main at root, test-improvements at `/test/`.

### Environment Protection

The `github-pages` environment allows deployments from both `main` and `test-improvements` branches.
