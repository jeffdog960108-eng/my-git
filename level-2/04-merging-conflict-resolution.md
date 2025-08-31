# Week 4: Merging & Conflict Resolution

## Exercise 1: Merge Branches (`git merge`)

### What it does:
Combines changes from one branch into another, creating a new commit that represents the combined work.

### Step-by-step instructions:
1. Start on the target branch (usually main):
   ```bash
   git checkout main
   ```

2. Merge a feature branch:
   ```bash
   git merge feature-branch
   ```

3. Merge with specific strategy:
   ```bash
   git merge --no-ff feature-branch
   ```

### Expected output (fast-forward merge):
```
Updating a1b2c3d..e4f5g6h
Fast-forward
 feature-file.txt | 1 +
 1 file changed, 1 insertion(+)
```

### Expected output (merge commit):
```
Merge made by the 'recursive' strategy.
 feature-file.txt | 1 +
 1 file changed, 1 insertion(+)
```

### Merge strategies:
```bash
git merge feature-branch          # Default recursive strategy
git merge --no-ff feature-branch  # Always create merge commit
git merge --ff-only feature-branch # Only fast-forward merges
git merge --squash feature-branch  # Combine all changes into one commit
```

### Practice task:
- Create two branches with different changes
- Merge them using different strategies
- Understand when each strategy is appropriate

---

## Exercise 2: Resolve Merge Conflicts

### What it does:
When Git can't automatically merge changes, you need to manually resolve conflicts by choosing which changes to keep.

### Step-by-step instructions:
1. Create conflicting changes on two branches:
   ```bash
   # On main branch
   echo "Main branch content" > conflict.txt
   git add conflict.txt
   git commit -m "Add main content"
   
   # On feature branch
   git checkout -b feature-branch
   echo "Feature branch content" > conflict.txt
   git add conflict.txt
   git commit -m "Add feature content"
   ```

2. Try to merge (this will create a conflict):
   ```bash
   git checkout main
   git merge feature-branch
   ```

3. View the conflict:
   ```bash
   git status
   cat conflict.txt
   ```

4. Resolve the conflict by editing the file:
   ```bash
   # Edit conflict.txt to resolve the conflict
   # Remove conflict markers and choose content
   ```

5. Mark as resolved and complete merge:
   ```bash
   git add conflict.txt
   git commit -m "Resolve merge conflict"
   ```

### Conflict markers in files:
```
<<<<<<< HEAD
Main branch content
=======
Feature branch content
>>>>>>> feature-branch
```

### Practice task:
- Intentionally create merge conflicts
- Practice resolving them manually
- Use different resolution strategies

---

## Exercise 3: Use Merge Strategies

### What it does:
Different merge strategies handle conflicts and history differently, each with their own advantages.

### Step-by-step instructions:
1. Fast-forward merge (when possible):
   ```bash
   git merge --ff-only feature-branch
   ```

2. No-fast-forward merge:
   ```bash
   git merge --no-ff feature-branch
   ```

3. Squash merge:
   ```bash
   git merge --squash feature-branch
   git commit -m "Squashed feature branch changes"
   ```

4. Octopus merge (multiple branches):
   ```bash
   git merge branch1 branch2 branch3
   ```

### When to use each strategy:
- **Fast-forward**: When feature branch is ahead of main
- **No-fast-forward**: Always preserve feature branch history
- **Squash**: Combine multiple commits into one
- **Octopus**: Merge multiple branches at once

### Practice task:
- Try each merge strategy
- Understand the resulting commit history
- Know when to use each approach

---

## Exercise 4: Abort Merge Operations (`git merge --abort`)

### What it does:
Cancels an in-progress merge and returns to the state before the merge began.

### Step-by-step instructions:
1. Start a merge that creates conflicts:
   ```bash
   git merge feature-branch
   ```

2. When conflicts occur, abort the merge:
   ```bash
   git merge --abort
   ```

3. Verify you're back to the original state:
   ```bash
   git status
   ```

### Expected output:
```
fatal: merge is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and commit the result.
```

After abort:
```
On branch main
nothing to commit, working tree clean
```

### Practice task:
- Start a merge with conflicts
- Practice aborting the merge
- Verify the repository state is restored

---

## Exercise 5: Rebase Branches (`git rebase`)

### What it does:
Replays commits from one branch on top of another, creating a linear history.

### Step-by-step instructions:
1. Start on the feature branch:
   ```bash
   git checkout feature-branch
   ```

2. Rebase onto main:
   ```bash
   git rebase main
   ```

3. Interactive rebase:
   ```bash
   git rebase -i main
   ```

### Expected output:
```
First, rewinding head to replay your work on top of it...
Applying: Add feature content
```

### Rebase vs Merge:
- **Rebase**: Creates linear history, rewrites commit history
- **Merge**: Preserves branch history, creates merge commits

### Interactive rebase options:
```bash
pick   # Use commit as-is
reword # Edit commit message
edit   # Edit commit content
squash # Combine with previous commit
fixup  # Combine but discard message
drop   # Remove commit
```

### Practice task:
- Rebase a feature branch onto main
- Use interactive rebase to clean up commits
- Understand when to use rebase vs merge

---

## Exercise 6: Resolve Rebase Conflicts

### What it does:
When rebasing encounters conflicts, you need to resolve them and continue the rebase process.

### Step-by-step instructions:
1. Start a rebase that will have conflicts:
   ```bash
   git checkout feature-branch
   git rebase main
   ```

2. When conflicts occur, resolve them:
   ```bash
   # Edit conflicted files
   # Remove conflict markers
   ```

3. Mark as resolved and continue:
   ```bash
   git add resolved-file.txt
   git rebase --continue
   ```

4. Or skip the commit:
   ```bash
   git rebase --skip
   ```

5. Or abort the rebase:
   ```bash
   git rebase --abort
   ```

### Practice task:
- Create conflicts during rebase
- Practice resolving them
- Use continue, skip, and abort options

---

## Exercise 7: Advanced Merge Techniques

### What it does:
Learn advanced techniques for handling complex merge scenarios.

### Step-by-step instructions:
1. Merge with specific commit:
   ```bash
   git merge <commit-hash>
   ```

2. Merge specific files:
   ```bash
   git checkout feature-branch -- specific-file.txt
   ```

3. Use merge tools:
   ```bash
   git mergetool
   ```

4. Merge with custom message:
   ```bash
   git merge feature-branch -m "Custom merge message"
   ```

### Useful merge options:
```bash
git merge --strategy=ours feature-branch    # Prefer our changes
git merge --strategy=theirs feature-branch  # Prefer their changes
git merge --strategy-option=patience        # More patient diff algorithm
```

### Practice task:
- Use different merge strategies
- Practice selective merging
- Use merge tools for complex conflicts

---

## Exercise 8: Complete Merge Workflow

### What it does:
Demonstrates a complete workflow for handling merges in a real project scenario.

### Step-by-step instructions:
1. Start with clean main branch:
   ```bash
   git checkout main
   git pull origin main
   ```

2. Create feature branch:
   ```bash
   git checkout -b feature/user-profile
   ```

3. Make changes and commit:
   ```bash
   echo "User profile feature" > profile.js
   git add profile.js
   git commit -m "feat: add user profile component"
   ```

4. Update main branch (simulate other changes):
   ```bash
   git checkout main
   echo "Updated main content" >> main-file.txt
   git add main-file.txt
   git commit -m "docs: update documentation"
   git push origin main
   ```

5. Rebase feature branch:
   ```bash
   git checkout feature/user-profile
   git rebase main
   ```

6. Resolve any conflicts and continue:
   ```bash
   # If conflicts occur, resolve them
   git add .
   git rebase --continue
   ```

7. Push feature branch:
   ```bash
   git push -f origin feature/user-profile
   ```

### Practice task:
- Follow the complete workflow
- Handle conflicts during rebase
- Understand when to force push

---

## Summary Checklist

- [ ] Successfully merged branches using different strategies
- [ ] Resolved merge conflicts manually
- [ ] Used different merge strategies appropriately
- [ ] Aborted merge operations when needed
- [ ] Performed rebase operations
- [ ] Resolved conflicts during rebase
- [ ] Used advanced merge techniques
- [ ] Completed full merge workflow
- [ ] Understood when to use merge vs rebase

## Common Merge Workflows

### Feature Branch Workflow:
1. **Create feature branch**: `git checkout -b feature-name`
2. **Make changes and commit**: `git add . && git commit -m "message"`
3. **Update main**: `git checkout main && git pull`
4. **Rebase feature**: `git checkout feature-name && git rebase main`
5. **Push and create PR**: `git push -f origin feature-name`

### Merge Strategies Decision Tree:
- **Fast-forward possible?** → Use `git merge --ff-only`
- **Want to preserve history?** → Use `git merge --no-ff`
- **Want linear history?** → Use `git rebase`
- **Want to combine commits?** → Use `git merge --squash`

## Next Steps

Once you've completed all exercises in this file, you're ready to move on to Level 3: Advanced Git Operations!
