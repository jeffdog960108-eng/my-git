# 🌿 Week 2: Working with Branches

> **Master the art of branching and learn how to work on features without affecting your main codebase!**

---

## 🌱 Exercise 1: Create a New Branch (`git branch`)

### 🎯 What it does:
Creates a new branch pointer that points to the current commit, allowing you to work on features without affecting the main codebase.

### 📋 Step-by-step instructions:

#### 1️⃣ First, ensure you have some commits in your repository:
```bash
echo "Main content" > main-file.txt
git add main-file.txt
git commit -m "Add main file"
```

#### 2️⃣ Create a new branch:
```bash
git branch feature-branch
```

#### 3️⃣ Verify the branch was created:
```bash
git branch
```

### ✅ Expected output:
```bash
* main
  feature-branch
```
The asterisk (*) indicates your current branch.

### 🎯 Practice task:
- ✅ Create 3 different branches with descriptive names
- ✅ Use `git branch` to list all branches
- ✅ Understand which branch you're currently on

---

## 🔄 Exercise 2: Switch Between Branches (`git checkout`)

### 🎯 What it does:
Moves your working directory to a different branch, changing which files you see and can modify.

### 📋 Step-by-step instructions:

#### 1️⃣ Switch to the feature branch:
```bash
git checkout feature-branch
```

#### 2️⃣ Verify you're on the new branch:
```bash
git branch
```

#### 3️⃣ Switch back to main:
```bash
git checkout main
```

### ✅ Expected output when switching:
```bash
Switched to branch 'feature-branch'
```

### ⚠️ Important notes:
- **Your working directory changes** when you switch branches
- **Files that exist in one branch but not another** will appear/disappear
- **Uncommitted changes may prevent switching** (Git will warn you)

### 🎯 Practice task:
- ✅ Switch between different branches
- ✅ Create files on different branches
- ✅ Observe how files change when switching branches

---

## ⚡ Exercise 3: Create and Switch in One Command (`git checkout -b`)

### 🎯 What it does:
Combines creating a new branch and switching to it in a single command, which is very common in practice.

### 📋 Step-by-step instructions:

#### 1️⃣ Create and switch to a new branch:
```bash
git checkout -b new-feature
```

#### 2️⃣ Verify you're on the new branch:
```bash
git branch
```

#### 3️⃣ Make some changes and commit:
```bash
echo "Feature content" > feature-file.txt
git add feature-file.txt
git commit -m "Add feature file"
```

### ✅ Expected output:
```bash
Switched to a new branch 'new-feature'
```

### 🎯 Practice task:
- ✅ Create multiple feature branches using `git checkout -b`
- ✅ Make commits on each branch
- ✅ Switch between branches to see different states

---

## 📋 Exercise 4: List All Branches (`git branch -a`)

### 🎯 What it does:
Shows all branches, including local branches and remote branches that your local repository knows about.

### 📋 Step-by-step instructions:

#### 1️⃣ List local branches:
```bash
git branch
```

#### 2️⃣ List all branches (local and remote):
```bash
git branch -a
```

#### 3️⃣ List remote branches only:
```bash
git branch -r
```

### ✅ Expected output:
```bash
* main
  feature-branch
  new-feature
  remotes/origin/main
  remotes/origin/feature-branch
```

### 🔧 Useful options:
```bash
git branch              # List local branches
git branch -a           # List all branches (local + remote)
git branch -r           # List remote branches only
git branch -v           # List with last commit info
git branch --merged     # List branches merged into current
git branch --no-merged  # List branches not merged
```

### 🎯 Practice task:
- ✅ Create several branches
- ✅ Use different branch listing options
- ✅ Understand the difference between local and remote branches

---

## 🗑️ Exercise 5: Delete Branches (`git branch -d`)

### 🎯 What it does:
Removes a branch pointer from your local repository. The commits are still there but no longer accessible through that branch name.

### 📋 Step-by-step instructions:

#### 1️⃣ Switch to main branch first:
```bash
git checkout main
```

#### 2️⃣ Delete a branch (safe delete):
```bash
git branch -d feature-branch
```

#### 3️⃣ Force delete a branch (even if not merged):
```bash
git branch -D feature-branch
```

### ✅ Expected output (safe delete):
```bash
Deleted branch feature-branch (was a1b2c3d).
```

### ✅ Expected output (if branch not merged):
```bash
error: The branch 'feature-branch' is not fully merged.
If you are sure you want to delete it, run 'git branch -D feature-branch'.
```

### ⚠️ Important safety notes:
- **`-d` (lowercase)** = safe delete (only if merged)
- **`-D` (uppercase)** = force delete (even if not merged)
- **You cannot delete the branch you're currently on**
- **Deleted branches can be recovered** if you know the commit hash

### 🎯 Practice task:
- ✅ Create branches with different states (merged vs unmerged)
- ✅ Try safe delete on merged branches
- ✅ Try force delete on unmerged branches
- ✅ Understand when each type of delete is appropriate

---

## 🔄 Exercise 6: Branch Management Workflow

### 🎯 What it does:
Demonstrates a complete workflow for working with branches in a real project scenario.

### 📋 Step-by-step instructions:

#### 1️⃣ Start on main branch:
```bash
git checkout main
```

#### 2️⃣ Create a feature branch:
```bash
git checkout -b user-login-feature
```

#### 3️⃣ Make changes on the feature branch:
```bash
echo "User login functionality" > login.js
git add login.js
git commit -m "feat: add user login component"
```

#### 4️⃣ Switch back to main and make changes:
```bash
git checkout main
echo "Updated main content" >> main-file.txt
git add main-file.txt
git commit -m "docs: update main documentation"
```

#### 5️⃣ Switch back to feature branch:
```bash
git checkout user-login-feature
```

#### 6️⃣ Merge main into feature (to get latest changes):
```bash
git merge main
```

### 🎯 Practice task:
- ✅ Follow the complete workflow above
- ✅ Create multiple feature branches
- ✅ Practice switching between branches
- ✅ Understand how branches isolate work

---

## 📝 Exercise 7: Branch Naming Conventions

### 📋 Best practices for branch names:
- **Use descriptive names** that explain the purpose
- **Use lowercase letters and hyphens**
- **Include the type of work** (feature, bugfix, hotfix, etc.)

### 💡 Examples of good branch names:
```bash
feature/user-authentication
bugfix/login-error
hotfix/security-patch
docs/api-documentation
refactor/database-connection
```

### 📋 Step-by-step instructions:

#### 1️⃣ Create branches following naming conventions:
```bash
git checkout -b feature/user-dashboard
git checkout -b bugfix/button-styling
git checkout -b docs/readme-update
```

#### 2️⃣ List all branches to see the naming pattern:
```bash
git branch
```

### 🎯 Practice task:
- ✅ Create branches using different naming conventions
- ✅ Practice switching between them
- ✅ Understand why good naming is important

---

## 📋 Summary Checklist

- [ ] Successfully created new branches
- [ ] Switched between branches using `git checkout`
- [ ] Used `git checkout -b` to create and switch in one command
- [ ] Listed all branches (local and remote)
- [ ] Deleted branches safely and forcefully
- [ ] Followed a complete branch workflow
- [ ] Used proper branch naming conventions
- [ ] Understood how branches isolate work

---

## 🔄 Common Branch Workflow

1. **Start on main**: `git checkout main`
2. **Create feature branch**: `git checkout -b feature-name`
3. **Make changes and commit**: `git add . && git commit -m "message"`
4. **Switch back to main**: `git checkout main`
5. **Merge feature**: `git merge feature-name`
6. **Delete feature branch**: `git branch -d feature-name`

---

## 🚀 Next Steps

Once you've completed all exercises in this file, you're ready to move on to **Level 2: Collaboration & Remote Operations**!

---

> **💡 Pro Tip**: Branching is one of Git's most powerful features! Practice creating and managing branches until it becomes second nature. This skill will be essential for collaborative development! 🌿
