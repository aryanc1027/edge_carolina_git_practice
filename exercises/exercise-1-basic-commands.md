# Exercise 1: Basic Git Commands

## Objective
Practice basic Git commands: `git status`, `git add .`, `git commit -m`, and `git restore .`

## ⚠️ IMPORTANT: Always Work on Your Own Branch!
**NEVER work directly on the main branch!** Always create your own branch first.

## Steps

### 1. Create Your Own Branch
```bash
# Create and switch to your own branch (replace 'your-name' with your actual name)
git checkout -b student/your-name-basic-practice
```

### 2. Check Repository Status
```bash
git status
```
**Expected Output**: Shows clean working tree or lists modified files

### 3. Create a New File
Create a new file in the `students/` directory:
```bash
echo "Hello, Git!" > students/my-first-file.txt
```

### 4. Check Status Again
```bash
git status
```
**Expected Output**: Shows `students/my-first-file.txt` as untracked

### 5. Stage All Changes
```bash
git add .
```

### 6. Check Status After Staging
```bash
git status
```
**Expected Output**: Shows files staged for commit

### 7. Commit Changes
```bash
git commit -m "Add my first file to students directory"
```

### 8. Make a Mistake (Practice git restore)
Edit the file you just created:
```bash
echo "This is a mistake!" > students/my-first-file.txt
```

### 9. Restore the File
```bash
git restore students/my-first-file.txt
```

### 10. Verify Restoration
```bash
cat students/my-first-file.txt
```
**Expected Output**: Should show "Hello, Git!" (the original content)

### 11. Push Your Branch (Optional)
```bash
# Push your branch to remote (this is safe - you're on your own branch!)
git push -u origin student/your-name-basic-practice
```

## Key Learning Points
- **ALWAYS create your own branch first** - never work directly on main
- `git status` shows the current state of your repository
- `git add .` stages all changes for commit
- `git commit -m` creates a commit with a message
- `git restore .` can undo uncommitted changes (use carefully!)
- `git push -u origin branch-name` pushes your branch safely to remote

## 🚨 Safety Reminders
- ✅ **DO**: Work on your own branch (`student/your-name-*`)
- ❌ **DON'T**: Work directly on main branch
- ✅ **DO**: Push your branch to remote for backup
- ❌ **DON'T**: Try to push to main (it's protected!)
