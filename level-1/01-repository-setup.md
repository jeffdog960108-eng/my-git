# 🚀 Week 1: Repository Setup & Basic Commands

> **Master the fundamentals of Git repository management and basic version control operations!**

---

## 📁 Exercise 1: Initialize a New Git Repository (`git init`)

### 🎯 What it does:
Creates a new Git repository in the current directory, initializing the `.git` folder that tracks all changes.

### 📋 Step-by-step instructions:

#### 1️⃣ Open terminal and navigate to a new directory:
```bash
mkdir my-first-repo
cd my-first-repo
```

#### 2️⃣ Initialize the Git repository:
```bash
git init
```

#### 3️⃣ Verify the repository was created:
```bash
ls -la
```
You should see a `.git` folder.

### ✅ Expected output:
```bash
Initialized empty Git repository in /path/to/my-first-repo/.git/
```

### 🎯 Practice task:
- ✅ Create a new directory called `practice-repo`
- ✅ Initialize it as a Git repository
- ✅ Check that the `.git` folder exists

---

## 📥 Exercise 2: Clone an Existing Repository (`git clone`)

### 🎯 What it does:
Downloads a copy of an existing repository from a remote source (like GitHub) to your local machine.

### 📋 Step-by-step instructions:

#### 1️⃣ Find a repository URL (e.g., from GitHub)

#### 2️⃣ Clone the repository:
```bash
git clone https://github.com/username/repository-name.git
```

#### 3️⃣ Navigate into the cloned directory:
```bash
cd repository-name
```

### ✅ Expected output:
```bash
Cloning into 'repository-name'...
remote: Enumerating objects: 100, done.
remote: Counting objects: 100% (100/100), done.
remote: Compressing objects: 100% (80/80), done.
Receiving objects: 100% (100/100), done.
Resolving deltas: 100% (50/50), done.
```

### 🎯 Practice task:
- ✅ Clone this repository: `https://github.com/octocat/Hello-World`
- ✅ Explore the files in the cloned repository

---

## 📊 Exercise 3: Check Repository Status (`git status`)

### 🎯 What it does:
Shows the current state of your working directory and staging area, including which files are tracked, modified, or staged.

### 📋 Step-by-step instructions:

#### 1️⃣ In your Git repository, create a new file:
```bash
echo "Hello World" > hello.txt
```

#### 2️⃣ Check the status:
```bash
git status
```

#### 3️⃣ Add the file to staging:
```bash
git add hello.txt
```

#### 4️⃣ Check status again:
```bash
git status
```

### ✅ Expected output (before adding):
```bash
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt

nothing added to commit but untracked files present (use "git add" and/or "git commit -a")
```

### ✅ Expected output (after adding):
```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.txt
```

### 🎯 Practice task:
- ✅ Create multiple files with different content
- ✅ Use `git status` to see which files are untracked
- ✅ Add some files and check status again

---

## ➕ Exercise 4: Add Files to Staging Area (`git add`)

### 🎯 What it does:
Moves files from the working directory to the staging area, preparing them for the next commit.

### 📋 Step-by-step instructions:

#### 1️⃣ Create multiple files:
```bash
echo "File 1 content" > file1.txt
echo "File 2 content" > file2.txt
echo "File 3 content" > file3.txt
```

#### 2️⃣ Add specific files:
```bash
git add file1.txt file2.txt
```

#### 3️⃣ Add all files at once:
```bash
git add .
```

#### 4️⃣ Add files by pattern:
```bash
git add *.txt
```

### 🔧 Useful variations:
```bash
git add <filename>          # Add specific file
git add .                   # Add all files in current directory
git add *.txt              # Add all .txt files
git add -A                 # Add all changes (including deletions)
git add -p                 # Interactive add (choose changes)
```

### 🎯 Practice task:
- ✅ Create 5 different files with various extensions (.txt, .md, .js)
- ✅ Add files individually, then in groups
- ✅ Use `git status` to verify what's staged

---

## 💾 Exercise 5: Commit Changes (`git commit`)

### 🎯 What it does:
Creates a snapshot of the staged changes with a descriptive message, permanently recording the changes in Git history.

### 📋 Step-by-step instructions:

#### 1️⃣ Stage your changes:
```bash
git add .
```

#### 2️⃣ Commit with a message:
```bash
git commit -m "Initial commit: Add hello world files"
```

#### 3️⃣ Commit without staging (for tracked files):
```bash
git commit -am "Update existing files"
```

### 📝 Best practices for commit messages:
- **Use present tense** ("Add feature" not "Added feature")
- **Keep first line under 50 characters**
- **Be descriptive and specific**
- **Use imperative mood**

### 💡 Examples of good commit messages:
```bash
feat: add user authentication system
fix: resolve login page crash
docs: update README with installation steps
style: format code according to style guide
```

### 🎯 Practice task:
- ✅ Make several commits with different types of changes
- ✅ Practice writing good commit messages
- ✅ Try both `git commit -m` and `git commit -am`

---

## 📜 Exercise 6: View Commit History (`git log`)

### 🎯 What it does:
Displays the commit history, showing when changes were made, by whom, and what was changed.

### 📋 Step-by-step instructions:

#### 1️⃣ View basic commit history:
```bash
git log
```

#### 2️⃣ View compact history:
```bash
git log --oneline
```

#### 3️⃣ View graph of branches:
```bash
git log --graph --oneline --all
```

#### 4️⃣ View specific number of commits:
```bash
git log -n 5
```

### 🔧 Useful options:
```bash
git log --oneline          # Compact format
git log --graph           # Show branch structure
git log --author="name"   # Filter by author
git log --since="2023-01-01"  # Filter by date
git log -p               # Show changes in each commit
git log --stat           # Show file statistics
```

### 🎯 Practice task:
- ✅ Make several commits with different messages
- ✅ Explore different `git log` formats
- ✅ Try filtering commits by author or date

---

## 📋 Summary Checklist

- [ ] Successfully initialized a new Git repository
- [ ] Cloned an existing repository from GitHub
- [ ] Used `git status` to check repository state
- [ ] Added files to staging area using different methods
- [ ] Created commits with descriptive messages
- [ ] Viewed commit history in different formats
- [ ] Understood the difference between working directory, staging area, and repository

---

## 🚀 Next Steps

Once you've completed all exercises in this file, you're ready to move on to **Week 2: Working with Branches**!

---

> **💡 Pro Tip**: Practice these basic commands regularly until they become second nature. They form the foundation for all advanced Git operations! 🎯
