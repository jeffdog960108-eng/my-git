# Week 6: Stashing & Advanced Features

## Exercise 1: Stash Changes (`git stash`)

### What it does:
Temporarily saves your uncommitted changes so you can switch branches or perform other operations without committing incomplete work.

### Step-by-step instructions:
1. Make some changes to files:
   ```bash
   echo "Work in progress" > work.txt
   git add work.txt
   ```

2. Stash the changes:
   ```bash
   git stash
   ```

3. Verify the stash:
   ```bash
   git status
   ```

4. List all stashes:
   ```bash
   git stash list
   ```

### Expected output:
```
Saved working directory and index state WIP on main: a1b2c3d Latest commit
```

### Stash options:
```bash
git stash                    # Stash all changes
git stash push -m "message"   # Stash with custom message
git stash -u                 # Stash including untracked files
git stash -a                 # Stash including ignored files
```

### Practice task:
- Make changes and stash them
- Switch branches and verify changes are gone
- List your stashes

---

## Exercise 2: Apply Stashed Changes (`git stash pop`)

### What it does:
Restores your stashed changes to the working directory and removes the stash from the stash list.

### Step-by-step instructions:
1. Apply the most recent stash:
   ```bash
   git stash pop
   ```

2. Apply a specific stash:
   ```bash
   git stash pop stash@{1}
   ```

3. Apply without removing from stash:
   ```bash
   git stash apply stash@{0}
   ```

### Expected output:
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   work.txt

no changes added to commit (use "git add" and/or "git commit" to commit them)
Dropped refs/stash@{0} (a1b2c3d...)
```

### Stash management commands:
```bash
git stash pop              # Apply and remove from stash
git stash apply            # Apply but keep in stash
git stash drop             # Remove from stash
git stash clear            # Remove all stashes
git stash show             # Show stash contents
git stash show -p          # Show stash diff
```

### Practice task:
- Apply stashed changes
- Use different stash commands
- Handle conflicts when applying stashes

---

## Exercise 3: Cherry-pick Commits (`git cherry-pick`)

### What it does:
Applies a specific commit from one branch to another branch, creating a new commit with the same changes.

### Step-by-step instructions:
1. Find a commit to cherry-pick:
   ```bash
   git log --oneline
   ```

2. Cherry-pick a specific commit:
   ```bash
   git cherry-pick a1b2c3d
   ```

3. Cherry-pick multiple commits:
   ```bash
   git cherry-pick a1b2c3d e4f5g6h
   ```

4. Cherry-pick without committing:
   ```bash
   git cherry-pick --no-commit a1b2c3d
   ```

### Expected output:
```
[main a1b2c3d] Original commit message
 1 file changed, 1 insertion(+)
```

### Cherry-pick options:
```bash
git cherry-pick <commit>           # Cherry-pick single commit
git cherry-pick --no-commit <commit> # Cherry-pick without committing
git cherry-pick --continue         # Continue after resolving conflicts
git cherry-pick --abort            # Abort cherry-pick operation
git cherry-pick --skip             # Skip current commit
```

### Practice task:
- Cherry-pick commits between branches
- Handle conflicts during cherry-pick
- Use different cherry-pick options

---

## Exercise 4: Create Tags (`git tag`)

### What it does:
Creates a named reference to a specific commit, commonly used for marking releases or important points in history.

### Step-by-step instructions:
1. Create a lightweight tag:
   ```bash
   git tag v1.0.0
   ```

2. Create an annotated tag:
   ```bash
   git tag -a v1.0.0 -m "Release version 1.0.0"
   ```

3. Tag a specific commit:
   ```bash
   git tag -a v0.9.0 -m "Pre-release version" a1b2c3d
   ```

4. List all tags:
   ```bash
   git tag
   ```

### Expected output:
```
v1.0.0
v0.9.0
```

### Tag types and options:
```bash
git tag v1.0.0                    # Lightweight tag
git tag -a v1.0.0 -m "message"   # Annotated tag
git tag -d v1.0.0                 # Delete tag
git tag -l "v1.*"                 # List tags matching pattern
git show v1.0.0                   # Show tag details
```

### Practice task:
- Create different types of tags
- Tag specific commits
- List and manage tags

---

## Exercise 5: Use Git Hooks

### What it does:
Git hooks are scripts that run automatically at certain points in the Git workflow, allowing you to customize Git's behavior.

### Step-by-step instructions:
1. Navigate to hooks directory:
   ```bash
   cd .git/hooks
   ```

2. Create a pre-commit hook:
   ```bash
   cat > pre-commit << 'EOF'
   #!/bin/sh
   echo "Running pre-commit checks..."
   # Add your checks here
   exit 0
   EOF
   ```

3. Make the hook executable:
   ```bash
   chmod +x pre-commit
   ```

4. Test the hook:
   ```bash
   cd ../..
   echo "test" > test.txt
   git add test.txt
   git commit -m "Test commit"
   ```

### Common hook types:
```bash
pre-commit          # Runs before commit
post-commit         # Runs after commit
pre-push            # Runs before push
post-merge          # Runs after merge
pre-rebase          # Runs before rebase
```

### Practice task:
- Create a simple pre-commit hook
- Test the hook functionality
- Understand when hooks run

---

## Exercise 6: Git Submodules

### What it does:
Allows you to include other Git repositories as subdirectories within your main repository.

### Step-by-step instructions:
1. Add a submodule:
   ```bash
   git submodule add https://github.com/username/repo.git submodule-name
   ```

2. Initialize submodules:
   ```bash
   git submodule init
   ```

3. Update submodules:
   ```bash
   git submodule update
   ```

4. Clone repository with submodules:
   ```bash
   git clone --recursive https://github.com/username/repo.git
   ```

### Expected output:
```
Cloning into 'submodule-name'...
remote: Enumerating objects: 100, done.
remote: Counting objects: 100% (100/100), done.
remote: Compressing objects: 100% (80/80), done.
Receiving objects: 100% (100/100), done.
Resolving deltas: 100% (50/50), done.
Submodule 'submodule-name' (https://github.com/username/repo.git) registered for path 'submodule-name'
```

### Submodule commands:
```bash
git submodule add <url> <path>    # Add submodule
git submodule init                 # Initialize submodules
git submodule update               # Update submodules
git submodule foreach <command>    # Run command in each submodule
```

### Practice task:
- Add a submodule to your repository
- Update and manage submodules
- Understand submodule workflow

---

## Exercise 7: Git Worktree

### What it does:
Allows you to have multiple working directories for the same repository, useful for working on different branches simultaneously.

### Step-by-step instructions:
1. Create a new worktree:
   ```bash
   git worktree add ../feature-branch-worktree feature-branch
   ```

2. List worktrees:
   ```bash
   git worktree list
   ```

3. Remove a worktree:
   ```bash
   git worktree remove ../feature-branch-worktree
   ```

### Expected output:
```
Preparing worktree (new branch 'feature-branch')
HEAD is now at a1b2c3d Latest commit
```

### Worktree commands:
```bash
git worktree add <path> <branch>  # Add worktree
git worktree list                  # List worktrees
git worktree remove <path>         # Remove worktree
git worktree prune                 # Remove stale worktrees
```

### Practice task:
- Create multiple worktrees
- Work on different branches simultaneously
- Manage worktrees

---

## Exercise 8: Advanced Git Configuration

### What it does:
Customize Git behavior through configuration options for better workflow and productivity.

### Step-by-step instructions:
1. Set up aliases:
   ```bash
   git config --global alias.co checkout
   git config --global alias.br branch
   git config --global alias.ci commit
   git config --global alias.st status
   ```

2. Configure default editor:
   ```bash
   git config --global core.editor "code --wait"
   ```

3. Set up credential helper:
   ```bash
   git config --global credential.helper cache
   ```

4. Configure merge tools:
   ```bash
   git config --global merge.tool vscode
   git config --global mergetool.vscode.cmd 'code --wait $MERGED'
   ```

### Useful configurations:
```bash
git config --global alias.lg "log --oneline --graph --decorate"
git config --global core.autocrlf input
git config --global init.defaultBranch main
git config --global pull.rebase false
```

### Practice task:
- Set up useful Git aliases
- Configure your preferred editor
- Customize Git behavior

---

## Summary Checklist

- [ ] Successfully stashed and applied changes
- [ ] Used cherry-pick to apply specific commits
- [ ] Created and managed tags
- [ ] Set up and used Git hooks
- [ ] Worked with Git submodules
- [ ] Used Git worktrees
- [ ] Configured Git for better workflow
- [ ] Understood advanced Git features

## Advanced Workflows

### Stashing Workflow:
1. **Make changes**: Edit files
2. **Stash changes**: `git stash push -m "message"`
3. **Switch branches**: `git checkout other-branch`
4. **Apply changes**: `git stash pop`

### Cherry-pick Workflow:
1. **Find commit**: `git log --oneline`
2. **Cherry-pick**: `git cherry-pick <commit>`
3. **Resolve conflicts**: Edit files if needed
4. **Continue**: `git cherry-pick --continue`

### Tagging Workflow:
1. **Create tag**: `git tag -a v1.0.0 -m "Release"`
2. **Push tag**: `git push origin v1.0.0`
3. **List tags**: `git tag -l`

## Next Steps

Congratulations! You've completed all levels of the Git practice program. You're now proficient in advanced Git operations and ready to use Git effectively in real-world projects!
