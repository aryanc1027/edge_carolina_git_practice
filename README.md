# Branch Protection Setup Guide

## Overview
This guide explains how to set up branch protection rules for the main branch to prevent students from pushing directly to main.

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
