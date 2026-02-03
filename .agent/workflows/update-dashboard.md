---
description: Update the OutfitMD team status dashboard with latest project info
---

# Update Dashboard Workflow

Use this workflow when the user requests to update the OutfitMD status dashboard.

## Trigger
User says something like:
- "Update the OutfitMD dashboard"
- "/update-dashboard"
- "Update dashboard. Focus: [topic]"
- "Refresh the status page"

## Private Repo Locations
The source repos are stored separately (not in the dashboard repo to allow GitHub Pages):
- **Onboarding**: `/Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfit-md-onboarding/`
- **Workflows**: `/Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfitmd-n8n-workflows/`

## Steps

### 1. Pull Latest from Private Repos
// turbo
```bash
cd /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfit-md-onboarding && git pull
cd /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfitmd-n8n-workflows && git pull
```

### 2. Get Recent Commits
// turbo
```bash
git -C /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfit-md-onboarding log --oneline -5
git -C /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfitmd-n8n-workflows log --oneline -5
```

### 3. Read Key Context Files
// turbo
```bash
cat /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfit-md-onboarding/.agent/CHANGELOG.md
cat /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfitmd-n8n-workflows/TODO.md
cat /Users/leopoldojacobsen/Documents/GitHub/outfitmd-private/outfitmd-n8n-workflows/CONTEXT.md
```

### 4. Update index.html
Edit `/Users/leopoldojacobsen/Documents/GitHub/outfit-md-tasks/index.html`:
- Update "Last Updated" timestamp
- Update "Current Focus" section with user's focus
- Update task lists based on CHANGELOG and TODO
- Update recent changes section
- Update dependency status if changed

### 5. Commit and Push
```bash
cd /Users/leopoldojacobsen/Documents/GitHub/outfit-md-tasks
git add index.html styles.css
git commit -m "chore: Update dashboard - [current date and summary]"
git push
```

### 6. Notify User
Confirm the dashboard has been updated with a link to:
`https://leopoldojacobsen.github.io/outfit-md-tasks/`
