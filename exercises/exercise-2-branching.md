# Exercise 2: Branching and Switching

## Objective
Practice creating branches, switching between them, and pushing changes.

## ⚠️ IMPORTANT: Always Work on Your Own Branch!
**NEVER work directly on the main branch!** Always create your own branch first.

## Steps

### 1. Create Your Own Branch First
```bash
# Create and switch to your own branch (replace 'your-name' with your actual name)
git checkout -b student/your-name-branching-practice
```

### 2. Check Current Branch
```bash
git branch
```
**Expected Output**: Shows `* student/your-name-branching-practice` (your current branch)

### 3. Create and Switch to New Branch (Method 1)
```bash
git checkout -b feature/my-new-feature
```

### 4. Verify Branch Switch
```bash
git branch
```
**Expected Output**: Shows `* feature/my-new-feature` (current branch)

### 5. Make Changes on New Branch
```bash
echo "This is a new feature!" > students/feature-file.txt
git add .
git commit -m "Add feature file to new branch"
```

### 6. Switch Back to Your Student Branch
```bash
git checkout student/your-name-branching-practice
```

### 7. Verify File Doesn't Exist on Your Student Branch
```bash
ls students/
```
**Expected Output**: Should not show `feature-file.txt`

### 8. Create Another Branch (Method 2)
```bash
git switch -c bugfix/important-fix
```

### 9. Make Changes on Bugfix Branch
```bash
echo "This fixes a critical bug!" > students/bugfix-file.txt
git add .
git commit -m "Add bugfix file"
```

### 10. Switch Between Branches
```bash
git switch student/your-name-branching-practice
git switch feature/my-new-feature
git switch bugfix/important-fix
```

### 11. Push Your Branches to Remote
```bash
# Push your student branch
git switch student/your-name-branching-practice
git push -u origin student/your-name-branching-practice

# Push your feature branch
git switch feature/my-new-feature
git push -u origin feature/my-new-feature

# Push your bugfix branch
git switch bugfix/important-fix
git push -u origin bugfix/important-fix
```

## Key Learning Points
- **ALWAYS create your own branch first** - never work directly on main
- `git checkout -b` creates and switches to a new branch
- `git switch -c` is the modern way to create and switch branches
- `git switch` is the modern way to switch between existing branches
- Each branch maintains its own set of files and commits
- `git push -u origin branch-name` pushes a new branch to remote

## Branch Management Tips
- Use descriptive branch names: `student/your-name-*`, `feature/user-authentication`, `bugfix/login-error`
- Create branches for each new feature or bug fix
- Keep main branch clean and stable (it's protected!)
- Delete branches after merging: `git branch -d branch-name`

## 🚨 Safety Reminders
- ✅ **DO**: Work on your own branch (`student/your-name-*`)
- ❌ **DON'T**: Work directly on main branch
- ✅ **DO**: Push your branches to remote for backup
- ❌ **DON'T**: Try to push to main (it's protected!)
- ✅ **DO**: Create feature branches from your student branch
- ❌ **DON'T**: Create branches directly from main
