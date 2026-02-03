---
description: Update the OutfitMD team status dashboard with latest project info
---

# Update Dashboard Workflow

Use this workflow when the user requests to update the OutfitMD status dashboard.

## Trigger
User says something like:
- "Update the OutfitMD dashboard"
- "Update dashboard. Focus: [topic]"
- "Refresh the status page"

## Steps

### 1. Pull Latest Submodule Changes
// turbo
```bash
cd /Users/leopoldojacobsen/Documents/GitHub/outfit-md-tasks
git submodule update --remote
```

### 2. Get Recent Commits from Each Project
// turbo
```bash
cd /Users/leopoldojacobsen/Documents/GitHub/outfit-md-tasks
git -C outfit-md-onboarding log --oneline -5
git -C outfitmd-n8n-workflows log --oneline -5
```

### 3. Check TODO/Status Files (if needed)
// turbo
```bash
cat outfit-md-onboarding/README.md
cat outfitmd-n8n-workflows/TODO.md
```

### 4. Update index.html
Edit `/Users/leopoldojacobsen/Documents/GitHub/outfit-md-tasks/index.html`:
- Update "Last Updated" timestamp
- Update "Current Focus" section with user's focus
- Update task lists based on recent commits
- Update recent activity section

### 5. Commit and Push
```bash
cd /Users/leopoldojacobsen/Documents/GitHub/outfit-md-tasks
git add index.html
git commit -m "chore: Update dashboard - [current date]"
git push
```

### 6. Notify User
Confirm the dashboard has been updated with a link to:
`https://leopoldojacobsen.github.io/outfit-md-tasks/`
