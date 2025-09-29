# Branch Protection Setup Guide

## Overview
This guide explains how to set up branch protection rules for the main branch to prevent students from pushing directly to main.

## GitHub Branch Protection Rules

### 1. Navigate to Repository Settings
1. Go to your repository on GitHub
2. Click on "Settings" tab
3. Click on "Branches" in the left sidebar

### 2. Add Branch Protection Rule
1. Click "Add rule" or "Add branch protection rule"
2. In "Branch name pattern", enter: `main`
3. Configure the following settings:

#### Required Settings:
- ✅ **Require a pull request before merging**
  - ✅ Require approvals: 1
  - ✅ Dismiss stale PR approvals when new commits are pushed
  - ✅ Require review from code owners (if you have a CODEOWNERS file)

- ✅ **Require status checks to pass before merging**
  - ✅ Require branches to be up to date before merging

- ✅ **Require conversation resolution before merging**

- ✅ **Require signed commits**

- ✅ **Require linear history**

- ✅ **Include administrators** (this applies the rules to everyone, including admins)

- ✅ **Restrict pushes that create files larger than 100 MB**

#### Optional Settings:
- ✅ **Restrict pushes that create files larger than 100 MB**
- ✅ **Do not allow bypassing the above settings**

### 3. Save the Rule
Click "Create" or "Save changes"

## What This Achieves

### ✅ Students CAN:
- Create their own branches (`student/name-*`)
- Push to their own branches
- Create pull requests from their branches
- Work on feature branches
- Practice all Git commands safely

### ❌ Students CANNOT:
- Push directly to main branch
- Merge directly to main branch
- Bypass pull request requirements
- Push without proper review process

## Student Workflow with Protection

### 1. Student Creates Branch
```bash
git checkout -b student/john-doe-practice
```

### 2. Student Makes Changes
```bash
# Make changes
echo "My practice work" > students/john-work.txt
git add .
git commit -m "Add practice file"
```

### 3. Student Pushes to Their Branch
```bash
# This works - they're pushing to their own branch
git push -u origin student/john-doe-practice
```

### 4. Student Tries to Push to Main (Will Fail)
```bash
# This will fail - main is protected
git checkout main
git merge student/john-doe-practice
git push origin main
# ERROR: Protected branch - cannot push directly
```

### 5. Student Creates Pull Request
- Go to GitHub repository
- Click "Compare & pull request"
- Set base branch to their student branch (not main)
- Create pull request for review

## Benefits of Branch Protection

### 🛡️ Security
- Prevents accidental pushes to main
- Ensures code review process
- Maintains repository integrity

### 📚 Learning
- Students learn proper Git workflow
- Practice with pull requests
- Understand code review process
- Learn about branch management

### 🎯 Best Practices
- Enforces professional development practices
- Teaches proper collaboration workflow
- Prevents merge conflicts on main
- Maintains clean project history

## Troubleshooting

### If Students Get Errors:
1. **"Protected branch" error**: They're trying to push to main - redirect them to their own branch
2. **"Permission denied"**: They need to create their own branch first
3. **"Branch not found"**: They need to push their branch first: `git push -u origin branch-name`

### Common Student Mistakes:
- Working directly on main branch
- Trying to push to main without pull request
- Not creating their own branch first
- Forgetting to push their branch before creating PR

## Alternative: Repository Permissions

If you want even more control, you can:
1. Set repository to "Private" (students need to be added as collaborators)
2. Use "Restrict pushes that create files larger than 100 MB"
3. Set up CODEOWNERS file for automatic reviewer assignment

## Summary

Branch protection ensures that:
- ✅ Students can practice safely on their own branches
- ✅ Main branch stays clean and protected
- ✅ Students learn proper Git workflow
- ✅ Code review process is enforced
- ✅ Repository integrity is maintained

This setup allows students to learn Git commands while protecting the main branch from accidental or malicious changes.
