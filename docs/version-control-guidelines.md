# Version Control, Branch Naming & Jira Integration Guidelines

This document defines the complete workflow for version control, branch naming conventions, Jira integration, and pull request procedures for the DreamTale project.

---

## 🌿 Branch Naming Conventions

All branches **must follow this naming format**.  
This rule is enforced using a GitHub workflow.

```
<type>/<JIRA-KEY>-short-description
```

### Allowed Types

- `story` – New functionality or user stories
- `task` – Setup, refactoring, documentation
- `bugfix` – Bug fixes

### Jira Key Format

```
DREAM-<number>
```

### Valid Examples

```
story/DREAM-12-world-creation-ui
task/DREAM-08-setup-supabase
bugfix/DREAM-21-fix-auth-error
story/DREAM-15-character-progression
task/DREAM-03-configure-github-actions
```

### Invalid Examples

```
story/world-ui                    ❌ Missing Jira key
fix-login                         ❌ Wrong type and missing Jira key
DREAM-12-story                    ❌ Wrong format (type must come first)
feature/DREAM-10-add-ui           ❌ 'feature' is not an allowed type
story/DREAM-12_world_creation     ❌ Use hyphens, not underscores
```

Branches that do not follow this format will fail the GitHub workflow check and cannot be merged.

---

## 🔗 Jira–GitHub Integration

- Jira is integrated with GitHub for full traceability
- Every branch must map to **exactly one Jira Story, Task, or Bug**
- Jira issue keys in branch names enable automatic linking
- Untracked or unlinked work is not allowed

This ensures:

- Clear sprint visibility
- Strong alignment between planning and implementation
- Professional collaboration practices
- Automatic updates from GitHub to Jira
- Complete audit trail from planning to deployment

---

## 🔀 Pull Request (PR) Rules

All PRs must:

- Originate from a `story/`, `task/`, or `bugfix/` branch
- Target the `dev` branch
- Reference the related Jira issue
- Pass all automated checks

### PR Description Must Include

- Jira issue key (e.g., `DREAM-12`)
- Brief summary of changes
- Key technical details
- Testing notes
- Any relevant notes for reviewers

### Review & Merge Policy

- PRs are reviewed by the **Team Lead**
- Only approved PRs may be merged
- Direct commits to `main` or `dev` are **strictly prohibited**
- All work must go through the PR process

---

## 🔄 Detailed Branch Workflow

### Creating a New Branch

```bash
# Ensure you're on dev and have latest changes
git checkout dev
git pull origin dev

# Create new branch following naming convention
git checkout -b story/DREAM-12-world-creation-ui
```

### Working on a Branch

```bash
# Make your changes
git add .
git commit -m "DREAM-12: Add world creation UI components"

# Push to remote
git push origin story/DREAM-12-world-creation-ui
```

### Creating a Pull Request

1. Push your branch to GitHub
2. Navigate to the repository on GitHub
3. Click "Pull Request"
4. Select `dev` as the base branch
5. Fill out the PR description completely
6. Submit for review

### After PR Approval

```bash
# Merge via GitHub interface or command line
git checkout dev
git pull origin dev
git merge --no-ff story/DREAM-12-world-creation-ui
git push origin dev

# Delete the branch
git branch -d story/DREAM-12-world-creation-ui
git push origin --delete story/DREAM-12-world-creation-ui
```

---

## 📅 Sprint Merge & Release Flow

### During Sprint

- All work happens on story/task/bugfix branches
- Completed work is merged to `dev` after PR approval
- `dev` branch contains all in-progress sprint work

### End of Sprint

Team Lead responsibilities:

1. Verify all sprint stories are complete in `dev`
2. Test the `dev` branch thoroughly
3. Create PR from `dev` to `main`
4. Review final changes with team
5. Merge `dev` into `main`
6. Tag the release with sprint number

```bash
# Tag the release
git checkout main
git pull origin main
git tag -a v1.0-sprint1 -m "Sprint 1 Release"
git push origin v1.0-sprint1
```

### Release Naming Convention

```
v<major>.<minor>-sprint<number>
```

Examples: `v1.0-sprint1`, `v1.0-sprint2`, `v1.1-sprint3`

---

## 🚫 Prohibited Actions

The following actions are strictly forbidden:

- Direct commits to `main` branch
- Direct commits to `dev` branch
- Pushing without creating a PR
- Merging your own PR without approval
- Creating branches with incorrect naming format
- Working on branches not linked to Jira issues
- Bypassing the review process
- Committing secrets or API keys
- Force pushing to shared branches

---

## ✅ Best Practices

### Commit Messages

Use clear, descriptive commit messages:

```bash
# Good examples
git commit -m "DREAM-12: Add world creation form with validation"
git commit -m "DREAM-08: Configure Supabase authentication"
git commit -m "DREAM-21: Fix login error handling"

# Avoid
git commit -m "updates"
git commit -m "fix"
git commit -m "wip"
```

### Branch Lifecycle

- Create branch from latest `dev`
- Keep branches focused and small
- Regularly pull `dev` to avoid conflicts
- Delete branch after merge
- Keep branch lifespan short (ideally within one sprint)

### Code Review

- Review promptly to avoid blocking others
- Provide constructive feedback
- Test changes locally when possible
- Check for code quality, not just functionality
- Verify Jira issue alignment

---

## 🛠️ GitHub Workflow Automation

A GitHub Action automatically validates branch names on every push.

Format validated: `<type>/<JIRA-KEY>-description`  
Allowed types: `story`, `task`, `bugfix`  
Jira key format: `DREAM-<number>`

Every PR triggers:

- Branch name validation
- Code linting
- Unit tests (when implemented)
- Build verification

---

## 📬 Questions & Support

For questions about these guidelines:

1. Check this document first
2. Ask in the team communication channel
3. Contact the Team Lead for clarification

---

**Maintained by:** DreamTale Team Lead  
**Last Updated:** Sprint 1