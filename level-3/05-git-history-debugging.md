# Week 5: Git History & Debugging

## Exercise 1: View Detailed Commit History (`git log --oneline --graph`)

### What it does:
Shows a visual representation of your commit history with branch structure and compact commit information.

### Step-by-step instructions:
1. View basic commit history:
   ```bash
   git log
   ```

2. View compact history:
   ```bash
   git log --oneline
   ```

3. View graph with all branches:
   ```bash
   git log --oneline --graph --all
   ```

4. View graph with decorations:
   ```bash
   git log --oneline --graph --decorate --all
   ```

### Expected output:
```
* e4f5g6h (HEAD -> main) Latest commit message
* a1b2c3d Previous commit message
* 9h8g7f6 Initial commit message
```

### Useful log options:
```bash
git log --oneline                    # Compact format
git log --graph                     # Show branch structure
git log --decorate                  # Show branch and tag names
git log --all                       # Show all branches
git log --author="name"             # Filter by author
git log --since="2023-01-01"       # Filter by date
git log -p                          # Show changes in each commit
git log --stat                      # Show file statistics
```

### Practice task:
- Create multiple branches and commits
- Use different log formats to view history
- Understand the graph visualization

---

## Exercise 2: Checkout Specific Commits (`git checkout <commit-hash>`)

### What it does:
Moves your working directory to a specific commit, allowing you to examine the code at that point in time.

### Step-by-step instructions:
1. Find a commit hash:
   ```bash
   git log --oneline
   ```

2. Checkout a specific commit:
   ```bash
   git checkout a1b2c3d
   ```

3. Return to the latest commit:
   ```bash
   git checkout main
   ```

### Expected output:
```
Note: switching to 'a1b2c3d'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false
```

### Important notes:
- This puts you in "detached HEAD" state
- Any commits you make won't be saved unless you create a new branch
- Use `git checkout main` to return to your main branch

### Practice task:
- Checkout different commits in your history
- Examine the code at different points
- Understand detached HEAD state

---

## Exercise 3: Reset Commits (`git reset`)

### What it does:
Moves the current branch pointer to a different commit, effectively "undoing" commits.

### Step-by-step instructions:
1. View current history:
   ```bash
   git log --oneline
   ```

2. Soft reset (keep changes staged):
   ```bash
   git reset --soft HEAD~1
   ```

3. Mixed reset (keep changes unstaged):
   ```bash
   git reset --mixed HEAD~1
   ```

4. Hard reset (discard all changes):
   ```bash
   git reset --hard HEAD~1
   ```

### Expected output (soft reset):
```
HEAD is now at a1b2c3d Previous commit message
```

### Reset types:
```bash
git reset --soft <commit>   # Move HEAD, keep changes staged
git reset --mixed <commit>  # Move HEAD, unstage changes (default)
git reset --hard <commit>   # Move HEAD, discard all changes
```

### Practice task:
- Try different reset types
- Understand what each type does
- Practice recovering from resets

---

## Exercise 4: Revert Commits (`git revert`)

### What it does:
Creates a new commit that undoes the changes from a specific commit, preserving history.

### Step-by-step instructions:
1. View commit history:
   ```bash
   git log --oneline
   ```

2. Revert a specific commit:
   ```bash
   git revert a1b2c3d
   ```

3. Revert multiple commits:
   ```bash
   git revert a1b2c3d e4f5g6h
   ```

4. Revert without committing:
   ```bash
   git revert --no-commit a1b2c3d
   ```

### Expected output:
```
[main a1b2c3d] Revert "Previous commit message"
 1 file changed, 1 deletion(-)
```

### Revert vs Reset:
- **Revert**: Creates new commit, preserves history, safe for shared branches
- **Reset**: Moves branch pointer, rewrites history, dangerous for shared branches

### Practice task:
- Revert commits in your history
- Understand the difference between revert and reset
- Practice reverting multiple commits

---

## Exercise 5: Use Git Bisect for Debugging

### What it does:
Helps you find the exact commit that introduced a bug by performing a binary search through your commit history.

### Step-by-step instructions:
1. Start bisect process:
   ```bash
   git bisect start
   ```

2. Mark current commit as bad:
   ```bash
   git bisect bad
   ```

3. Mark a known good commit:
   ```bash
   git bisect good a1b2c3d
   ```

4. Test the current commit and mark it:
   ```bash
   # Test your code here
   git bisect bad  # or git bisect good
   ```

5. Continue until you find the bad commit:
   ```bash
   # Git will checkout different commits
   # Test and mark each one
   ```

6. Reset bisect when done:
   ```bash
   git bisect reset
   ```

### Expected output:
```
Bisecting: 3 revisions left to test after this (roughly 2 steps)
[commit-hash] Commit message
```

### Practice task:
- Create a simple bug in your code
- Use bisect to find when it was introduced
- Practice the bisect workflow

---

## Exercise 6: Advanced Log Filtering

### What it does:
Filter commit history by various criteria to find specific commits or understand code changes.

### Step-by-step instructions:
1. Filter by author:
   ```bash
   git log --author="Your Name"
   ```

2. Filter by date range:
   ```bash
   git log --since="2023-01-01" --until="2023-12-31"
   ```

3. Filter by file:
   ```bash
   git log -- path/to/file.txt
   ```

4. Filter by commit message:
   ```bash
   git log --grep="bug fix"
   ```

5. Show commits that changed specific lines:
   ```bash
   git log -L 1,10:file.txt
   ```

### Practice task:
- Use different log filters
- Find commits by specific criteria
- Understand how to search through history

---

## Exercise 7: Git Blame (`git blame`)

### What it does:
Shows who last modified each line of a file and when.

### Step-by-step instructions:
1. View blame for a file:
   ```bash
   git blame file.txt
   ```

2. View blame with line numbers:
   ```bash
   git blame -n file.txt
   ```

3. View blame for specific lines:
   ```bash
   git blame -L 10,20 file.txt
   ```

### Expected output:
```
a1b2c3d (Your Name 2023-01-15 10:30:00 +0000 1) First line
e4f5g6h (Your Name 2023-01-16 14:20:00 +0000 2) Second line
```

### Practice task:
- Use blame to understand code changes
- Find who modified specific lines
- Understand when changes were made

---

## Exercise 8: Git Show (`git show`)

### What it does:
Shows detailed information about a specific commit, including the changes it introduced.

### Step-by-step instructions:
1. Show commit details:
   ```bash
   git show a1b2c3d
   ```

2. Show only the changes:
   ```bash
   git show --stat a1b2c3d
   ```

3. Show changes in a specific file:
   ```bash
   git show a1b2c3d -- file.txt
   ```

4. Show commit message only:
   ```bash
   git show --format=fuller a1b2c3d
   ```

### Expected output:
```
commit a1b2c3d
Author: Your Name <your.email@example.com>
Date:   Mon Jan 15 10:30:00 2023 +0000

    Commit message

diff --git a/file.txt b/file.txt
index 1234567..abcdefg 100644
--- a/file.txt
+++ b/file.txt
@@ -1 +1 @@
-Old content
+New content
```

### Practice task:
- Examine different commits with show
- Understand the diff output
- Practice analyzing commit changes

---

## Summary Checklist

- [ ] Successfully viewed detailed commit history
- [ ] Checked out specific commits
- [ ] Used different reset types
- [ ] Reverted commits safely
- [ ] Used git bisect for debugging
- [ ] Filtered commit history
- [ ] Used git blame to track changes
- [ ] Examined commits with git show
- [ ] Understood the difference between reset and revert

## Common Debugging Workflows

### Finding a Bug:
1. **Start bisect**: `git bisect start`
2. **Mark bad commit**: `git bisect bad`
3. **Mark good commit**: `git bisect good <commit>`
4. **Test and mark**: Test code, then `git bisect good/bad`
5. **Reset when done**: `git bisect reset`

### Examining History:
1. **View history**: `git log --oneline --graph`
2. **Checkout commit**: `git checkout <commit>`
3. **Examine changes**: `git show <commit>`
4. **Return to main**: `git checkout main`

## Next Steps

Once you've completed all exercises in this file, you're ready to move on to Week 6: Stashing & Advanced Features!
