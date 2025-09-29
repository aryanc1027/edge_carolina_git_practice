# Exercise 3: Writing Good Commit Messages

## Objective
Learn to write clear, descriptive commit messages that follow best practices.

## Good vs Bad Commit Messages

### ❌ Bad Examples
```bash
git commit -m "fix"
git commit -m "update"
git commit -m "changes"
git commit -m "stuff"
git commit -m "WIP"
```

### ✅ Good Examples
```bash
git commit -m "Fix login validation error for empty email field"
git commit -m "Add user authentication middleware"
git commit -m "Update README with installation instructions"
git commit -m "Refactor database connection handling"
git commit -m "Remove unused CSS classes from header component"
```

## Commit Message Format

### Basic Format
```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

### Common Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

## Practice Exercise

### 1. Create Different Types of Changes
```bash
# Feature addition
echo "function newFeature() { return 'Hello World'; }" > students/feature.js
git add students/feature.js
git commit -m "feat: add newFeature function to students module"

# Bug fix
echo "// Fixed: Removed console.log statement" > students/bugfix.js
git add students/bugfix.js
git commit -m "fix: remove debug console.log from students module"

# Documentation
echo "# Updated Documentation" > students/README.md
git add students/README.md
git commit -m "docs: add README to students directory"

# Style change
echo "// Formatted code properly" > students/style.js
git add students/style.js
git commit -m "style: format JavaScript code in students directory"
```

### 2. Multi-line Commit Messages
```bash
echo "Complex feature implementation" > students/complex.js
git add students/complex.js
git commit -m "feat: implement user profile management

- Add user profile creation functionality
- Add profile update capabilities
- Add profile deletion with confirmation
- Include input validation for all fields

Closes #123"
```

## Best Practices

### Do's ✅
- Use imperative mood ("Add feature" not "Added feature")
- Keep first line under 50 characters
- Be specific and descriptive
- Use present tense
- Reference issues/PRs when relevant

### Don'ts ❌
- Don't use vague words like "stuff", "things", "fix"
- Don't write in past tense
- Don't make messages too long for the subject line
- Don't commit without a message
- Don't use emojis in professional repositories

## Advanced: Conventional Commits
Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```bash
# Format: type(scope): description
git commit -m "feat(auth): add OAuth2 login support"
git commit -m "fix(api): resolve timeout issue in user endpoint"
git commit -m "docs(readme): update installation instructions"
```

## Exercise: Practice Session
1. Create 5 different files with different types of changes
2. Write appropriate commit messages for each
3. Use different commit types (feat, fix, docs, style, refactor)
4. Practice both short and multi-line commit messages
