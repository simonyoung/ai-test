# Claude Code Project Configuration

This file contains important project information and commands for AI assistants working on this codebase.

## Repository Setup

This project is connected to GitHub repository: https://github.com/simonyoung/ai-test

### Branch Protection Rules

The main branch has the following protections configured:
- Requires pull requests before merging
- Requires 1 approving review before merge
- Dismisses stale reviews when new commits are pushed
- Blocks direct pushes to main branch
- Prevents force pushes and branch deletion

**Important**: Always create feature branches and submit pull requests for changes. Direct pushes to main are not allowed.

### Commands for Branch Protection Setup

If branch protection needs to be reconfigured, use:

```bash
# Create branch protection configuration
cat > branch_protection.json << 'EOF'
{
  "required_status_checks": null,
  "enforce_admins": false,
  "required_pull_request_reviews": {
    "required_approving_review_count": 1,
    "dismiss_stale_reviews": true,
    "require_code_owner_reviews": false
  },
  "restrictions": null
}
EOF

# Apply branch protection
gh api repos/simonyoung/ai-test/branches/main/protection --method PUT --input branch_protection.json

# Clean up
rm branch_protection.json
```

## Development Workflow

1. Create a new branch for features: `git checkout -b feature/your-feature-name`
2. Make your changes and commit them
3. Push the branch: `git push -u origin feature/your-feature-name`
4. Create a pull request for review
5. After approval, merge via GitHub interface