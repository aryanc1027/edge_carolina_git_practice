# Exercise 5: Environment Variables (The Scary Stuff!)

## Objective
Learn about environment variables, .env files, and why they're important for security.

## ⚠️ IMPORTANT: Always Work on Your Own Branch!
**NEVER work directly on the main branch!** Always create your own branch first.

### 1. Create Your Own Branch First
```bash
# Create and switch to your own branch (replace 'your-name' with your actual name)
git checkout -b student/your-name-env-practice
```

## What are Environment Variables?
Environment variables are key-value pairs that store configuration data outside of your code. They're essential for:
- Keeping secrets secure
- Configuring applications for different environments
- Avoiding hardcoded values in your code

## Why Environment Variables Matter

### ❌ Bad Practice - Hardcoded Secrets
```javascript
// DON'T DO THIS!
const databasePassword = "super_secret_password_123";
const apiKey = "sk-1234567890abcdef";
const jwtSecret = "my_secret_key";
```

### ✅ Good Practice - Environment Variables
```javascript
// DO THIS INSTEAD!
const databasePassword = process.env.DB_PASSWORD;
const apiKey = process.env.API_KEY;
const jwtSecret = process.env.JWT_SECRET;
```

## Setting Up Environment Variables

### 1. Create .env File
```bash
# Create .env file (copy from env.example)
cp env.example .env
```

### 2. Edit .env File
```bash
# Edit with your actual values
nano .env
# or
code .env
```

### 3. Add to .gitignore
```bash
echo ".env" >> .gitignore
echo ".env.local" >> .gitignore
echo ".env.*.local" >> .gitignore
```

## Environment Variable Examples

### Basic .env File
```bash
# Database Configuration
DATABASE_URL=postgresql://username:password@localhost:5432/myapp
DB_HOST=localhost
DB_PORT=5432
DB_NAME=myapp
DB_USER=myuser
DB_PASSWORD=mysecretpassword

# API Keys
API_KEY=your_api_key_here
GITHUB_TOKEN=ghp_your_github_token_here

# Application Settings
NODE_ENV=development
PORT=3000
DEBUG=true

# Security
JWT_SECRET=your_super_secret_jwt_key_here
ENCRYPTION_KEY=your_encryption_key_here
```

## Using Environment Variables in Code

### Node.js Example
```javascript
// config.js
const config = {
  database: {
    host: process.env.DB_HOST || 'localhost',
    port: process.env.DB_PORT || 5432,
    name: process.env.DB_NAME || 'myapp',
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD
  },
  api: {
    key: process.env.API_KEY,
    baseUrl: process.env.API_BASE_URL || 'https://api.example.com'
  },
  app: {
    port: process.env.PORT || 3000,
    nodeEnv: process.env.NODE_ENV || 'development',
    debug: process.env.DEBUG === 'true'
  }
};

module.exports = config;
```

### Python Example
```python
import os

# config.py
DATABASE_URL = os.getenv('DATABASE_URL', 'sqlite:///default.db')
API_KEY = os.getenv('API_KEY')
DEBUG = os.getenv('DEBUG', 'False').lower() == 'true'
PORT = int(os.getenv('PORT', 5000))
```

## Security Best Practices

### 1. Never Commit .env Files
```bash
# Add to .gitignore
echo ".env" >> .gitignore
echo ".env.local" >> .gitignore
echo ".env.*.local" >> .gitignore

# Check if .env is already tracked
git status
```

### 2. Use Different Files for Different Environments
```bash
.env                    # Default values
.env.local             # Local development (ignored by git)
.env.development       # Development environment
.env.staging          # Staging environment
.env.production       # Production environment
```

### 3. Validate Required Variables
```javascript
// validate-env.js
const requiredEnvVars = [
  'DATABASE_URL',
  'API_KEY',
  'JWT_SECRET'
];

const missingVars = requiredEnvVars.filter(varName => !process.env[varName]);

if (missingVars.length > 0) {
  console.error('Missing required environment variables:', missingVars);
  process.exit(1);
}
```

## Exercise: Environment Variables Practice

### Step 2: Create a Simple Application
```bash
# Create a simple Node.js app
echo "const express = require('express');
const app = express();

const port = process.env.PORT || 3000;
const apiKey = process.env.API_KEY;
const debug = process.env.DEBUG === 'true';

app.get('/', (req, res) => {
  res.json({
    message: 'Hello from environment variables!',
    port: port,
    hasApiKey: !!apiKey,
    debug: debug
  });
});

app.listen(port, () => {
  console.log(\`Server running on port \${port}\`);
  if (debug) {
    console.log('Debug mode enabled');
  }
});" > students/app.js
```

### Step 3: Create Environment Files
```bash
# Create .env file
echo "PORT=3000
API_KEY=your_secret_api_key_here
DEBUG=true
NODE_ENV=development" > students/.env

# Create .env.example
echo "PORT=3000
API_KEY=your_api_key_here
DEBUG=true
NODE_ENV=development" > students/.env.example
```

### Step 4: Add to .gitignore
```bash
echo ".env" >> .gitignore
echo "node_modules/" >> .gitignore
```

### Step 5: Test Environment Variables
```bash
cd students
node app.js
```

### Step 6: Test with Different Values
```bash
# Test with different port
PORT=4000 node app.js

# Test with debug off
DEBUG=false node app.js
```

## Common Environment Variable Patterns

### 1. Database URLs
```bash
# PostgreSQL
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# MySQL
DATABASE_URL=mysql://user:password@localhost:3306/dbname

# MongoDB
DATABASE_URL=mongodb://localhost:27017/dbname
```

### 2. API Configuration
```bash
# External APIs
GITHUB_TOKEN=ghp_your_token_here
STRIPE_SECRET_KEY=sk_test_your_stripe_key
SENDGRID_API_KEY=SG.your_sendgrid_key

# Internal APIs
INTERNAL_API_URL=https://api.internal.com
API_VERSION=v1
```

### 3. Feature Flags
```bash
# Feature toggles
ENABLE_NEW_FEATURE=true
ENABLE_DEBUG_MODE=false
ENABLE_ANALYTICS=true
```

## Deployment Considerations

### 1. Production Environment
- Use secure secret management (AWS Secrets Manager, Azure Key Vault, etc.)
- Never store secrets in code or configuration files
- Use environment-specific configurations
- Rotate secrets regularly

### 2. Development Environment
- Use .env files for local development
- Never commit .env files
- Use .env.example for documentation
- Use different values for different developers

## Exercise: Complete Environment Setup

1. Create a simple web application that uses environment variables
2. Set up different .env files for different environments
3. Practice switching between environments
4. Learn how to validate required environment variables
5. Understand the importance of never committing secrets
6. Push your branch to remote for backup

### Step 7: Push Your Branch
```bash
# Push your branch to remote (this is safe - you're on your own branch!)
git push -u origin student/your-name-env-practice
```

## 🚨 Safety Reminders
- ✅ **DO**: Work on your own branch (`student/your-name-*`)
- ❌ **DON'T**: Work directly on main branch
- ✅ **DO**: Push your branch to remote for backup
- ❌ **DON'T**: Try to push to main (it's protected!)
- ✅ **DO**: Add .env files to .gitignore
- ❌ **DON'T**: Commit .env files with real secrets

## Security Reminders

⚠️ **NEVER COMMIT THESE:**
- API keys
- Database passwords
- JWT secrets
- Encryption keys
- Personal access tokens
- Any sensitive information

✅ **ALWAYS DO:**
- Use .env files for local development
- Add .env to .gitignore
- Use .env.example for documentation
- Validate required environment variables
- Use secure secret management in production
