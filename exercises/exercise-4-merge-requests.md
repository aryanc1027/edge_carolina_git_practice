# Exercise 4: Merge Requests (Pull Requests)

## Objective
Learn how to create, review, and manage merge requests/pull requests.

## ⚠️ IMPORTANT: Always Work on Your Own Branch!
**NEVER work directly on the main branch!** Always create your own branch first.

### 1. Create Your Own Branch First
```bash
# Create and switch to your own branch (replace 'your-name' with your actual name)
git checkout -b student/your-name-mr-practice
```

## What is a Merge Request?
A Merge Request (MR) or Pull Request (PR) is a way to propose changes to a repository. It allows:
- Code review before merging
- Discussion about changes
- Testing before integration
- Collaboration between team members

## Creating a Merge Request

### 2. Prepare Your Branch
```bash

git checkout student/your-name-mr-practice

# Create a feature branch from your student branch
git checkout -b feature/my-new-feature

# Make your changes
echo "This is my new feature!" > students/new-feature.txt
git add .
git commit -m "feat: add new feature implementation"
```

### 3. Push Your Branch
```bash
git push -u origin feature/my-new-feature
```

### 4. Create MR on GitHub/GitLab
1. Go to your repository on GitHub/GitLab
2. You'll see a banner: "feature/my-new-feature had recent pushes"
3. Click "Compare & pull request" or "Create merge request"
4. **IMPORTANT**: Set the base branch to your student branch, NOT main!
   - Base: `student/your-name-mr-practice` ← (your student branch)
   - Compare: `feature/my-new-feature` ← (your feature branch)
5. Fill in the MR details:
   - **Title**: Clear, descriptive title
   - **Description**: Explain what changes you made and why
   - **Reviewers**: Assign team members to review
   - **Labels**: Add relevant labels (bug, feature, etc.)

### 5. Good MR Description Template
```markdown
## Description
Brief description of what this MR does.

## Changes Made
- Added new feature X
- Fixed bug Y
- Updated documentation Z

## Testing
- [ ] Tested locally
- [ ] All tests pass
- [ ] No breaking changes

## Screenshots (if applicable)
[Add screenshots of UI changes]

## Related Issues
Closes #123
```

## Reviewing a Merge Request

### As a Reviewer
1. **Read the description** - Understand what's being changed
2. **Check the files changed** - Look at the diff
3. **Test the changes** - If possible, test locally
4. **Leave constructive feedback**:
   - Point out issues clearly
   - Suggest improvements
   - Ask questions if something is unclear
   - Approve when ready

### Review Checklist
- [ ] Code follows project conventions
- [ ] No obvious bugs or issues
- [ ] Tests are included (if applicable)
- [ ] Documentation is updated
- [ ] No sensitive information exposed
- [ ] Performance considerations addressed

## MR Workflow Exercise

### Step 1: Create a Feature Branch from Your Student Branch
```bash
# Make sure you're on your student branch
git checkout student/your-name-mr-practice

# Create feature branch from your student branch
git checkout -b feature/user-profile
```

### Step 2: Make Changes
```bash
# Create a user profile feature
mkdir -p students/features
echo "class UserProfile {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
  
  getDisplayName() {
    return this.name;
  }
}" > students/features/user-profile.js

# Add tests
echo "// Tests for UserProfile class
// TODO: Add actual test cases" > students/features/user-profile.test.js

# Update documentation
echo "# User Profile Feature

This feature allows users to manage their profile information.

## Usage
\`\`\`javascript
const profile = new UserProfile('John Doe', 'john@example.com');
console.log(profile.getDisplayName()); // 'John Doe'
\`\`\`" > students/features/README.md
```

### Step 3: Commit Changes
```bash
git add .
git commit -m "feat: add user profile management feature

- Add UserProfile class with constructor
- Add getDisplayName method
- Add placeholder test file
- Add documentation with usage examples"
```

### Step 4: Push and Create MR
```bash
git push -u origin feature/user-profile
```

### Step 5: Create MR Description
**IMPORTANT**: When creating the MR, set:
- **Base branch**: `student/your-name-mr-practice` (your student branch)
- **Compare branch**: `feature/user-profile` (your feature branch)
- **NOT main branch!**
```markdown
## Description
Adds a new UserProfile class to manage user profile information.

## Changes Made
- Added UserProfile class with constructor
- Added getDisplayName method
- Added placeholder test file
- Added documentation with usage examples

## Testing
- [x] Code compiles without errors
- [x] Basic functionality works
- [ ] Unit tests need to be implemented

## Related Issues
Part of user management system implementation
```

## Best Practices for MRs

### Do's ✅
- Keep MRs small and focused
- Write clear descriptions
- Include tests when possible
- Update documentation
- Use descriptive branch names
- Respond to feedback promptly

### Don'ts ❌
- Don't create massive MRs with many unrelated changes
- Don't merge without review (unless it's your own repo)
- Don't ignore feedback
- Don't commit directly to main branch
- Don't leave MRs open indefinitely

## Advanced MR Features

### Draft MRs
Create draft MRs for work-in-progress:
```bash
# Push your branch
git push -u origin feature/work-in-progress

# Create as draft MR
# Mark as "Ready for review" when done
```

### MR Templates
Create `.github/pull_request_template.md`:
```markdown
## Description
<!-- Describe your changes -->

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] I have tested these changes
- [ ] All tests pass
```

## Exercise: Practice MR Workflow
1. Create a new feature branch from your student branch
2. Make some changes (add files, modify existing ones)
3. Commit with good commit messages
4. Push the branch
5. Create an MR with proper description (base: your student branch, NOT main!)
6. Practice reviewing your own MR
7. Merge the MR into your student branch
8. Delete the feature branch

## 🚨 Safety Reminders
- ✅ **DO**: Create feature branches from your student branch
- ❌ **DON'T**: Create branches directly from main
- ✅ **DO**: Set MR base to your student branch
- ❌ **DON'T**: Set MR base to main (it's protected!)
- ✅ **DO**: Merge MRs into your student branch
- ❌ **DON'T**: Try to merge directly to main
