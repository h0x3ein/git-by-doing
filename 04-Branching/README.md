# Chapter 4: Git Branching

Branching in Git allows you to diverge from the main development line, enabling independent work without affecting the main branch. This chapter provides a comprehensive guide to branching, including creating, renaming, merging branches, and resolving conflicts.

## 📚 Table of Contents

- [🌿 Creating and Switching Branches](#-creating-and-switching-branches)
- [🔍 Modifying Files in a Branch](#-modifying-files-in-a-branch)
- [💾 Comparing Branches](#-comparing-branches)
- [🔀 Stashing Changes](#-stashing-changes)
- [⚔️ Merging Branches](#-merging-branches)
  - [Fast-forward Merges](#fast-forward-merges)
  - [3-way Merges](#3-way-merges)
  - [Disable Fast Forward](#disable-fast-forward)
  - [Three-way Merge](#three-way-merge)
- [🔍 Viewing merge branch](#viewing-merge-branch)
- [🔀 Merge Conflicts](#-merge-conflicts)
- [🌿 Aborting and Undoing Merges](#-aborting-and-undoing-merges)
- [💾 Undoing a faulty merge](#-undoing-a-faulty-merge)
- [🛠️ Squash Merging](#-squash-merging)
- [💾 Rebasing](#-rebasing)
  - [Rebase Conflicts](#rebase-conflicts)
- [🍒 Cherry Picking](#-cherry-picking)
- [⚔️ Picking file from another branch](#-picking-file-from-another-branch)
- [📝 Tasks](#-tasks)

## 🎯 Learning Objectives

In this chapter, you'll learn the essentials of branching in Git. Through practical tasks, gain hands-on experience with creating, managing, and merging branches, as well as handling conflicts and employing advanced branching strategies.

### 🌿 [Creating and Switching Branches](#creating-and-switching-branches)

Learn how to create new branches for feature development and switch between them to manage multiple workstreams.

### 🔍 [Modifying Files in a Branch](#modifying-files-in-a-branch)

Understand the process of making changes to files in a branch, staging, and committing those changes to track your work.

### 💾 [Comparing Branches](#comparing-branches)

Discover how to compare the differences between branches, including commit history and file changes, to understand branch divergences.

### 🔀 [Stashing Changes](#stashing-changes)

Master the technique of temporarily shelving changes so you can switch branches without committing in-progress work.

### ⚔️ [Merging Branches](#merge-conflicts)

Combine the work from different branches into a single branch to integrate features or resolve development paths.

#### [Fast-forward Merges](#fast-forward-merges-1)

Fast-forward merges occur when the target branch's tip is behind the source branch's tip, allowing for a linear history.

#### [3-way Merges](#3-way-merges-1)

When branches have diverged, a 3-way merge is used, creating a new merge commit to integrate the changes.

#### [Disable Fast Forward](#disable-fast-forward-1)

Learn how to disable fast-forward merges to ensure a merge commit is always created for a more descriptive history.

#### [Three-way Merge](#three-way-merge-1)

Three-way merges involve creating a new commit that has two parents, allowing for the integration of divergent branch histories.

### 🔍 [Viewing merge branch](#viewing-merge-branch)

Check which branches have been merged into the current branch and which haven't, aiding in branch management and cleanup.

### 🔀 [Merge Conflicts](#merge-conflicts)

Resolve conflicts that occur when merging branches with divergent changes to the same parts of files.

### 🌿 [Aborting and Undoing Merges](#aborting-and-undoing-merges)

Learn how to abort ongoing merge operations and undo merges that have been completed but need to be reversed.

### 💾 [Undoing a faulty merge](#undoing-a-faulty-merge)

Use Git's reset and revert commands to undo merges that have introduced errors or unwanted changes.

### 🛠️ [Squash Merging](#squash-merging)

Combine multiple commits from a branch into a single commit during the merge, keeping the target branch's history clean.

### 💾 [Rebasing](#rebasing)

Rebase a branch to change its base commit, integrating changes from one branch into another while maintaining a linear history.

#### [Rebase Conflicts](#rebase-conflicts-1)

Handle conflicts that arise during a rebase operation, resolving differences to continue the rebase process.

### 🍒 [Cherry Picking](#cherry-picking)

Selectively apply specific commits from one branch to another, allowing for precise control over the changes you integrate.

### ⚔️ [Picking file from another branch](#picking-file-from-another-branch)

Fetch and apply changes to specific files from another branch without merging the entire branch, useful for isolated changes.


## 📝 Tasks
### Creating and Switching Branches

```bash
# Create a new branch
git branch bugfix

# Switch to the bugfix branch (recommended)
git switch bugfix

# Alternatively, change to the bugfix branch
git checkout bugfix

# Change the branch name
git branch -m bugfux bugfix-sign
```

### Modifying Files in a Branch

Modify the audience.txt file

```
# Line 1: Modification
# Line 2: Addition
# Line 3: Deletion
```

```
  1 WHO THIS cource is 
  2 =============================
  3 This course is for anyone who wants to learn Git.
                       
```

```bash
# Stage and commit changes
git add .
git commit -m "Fix the signup Bug"

# View commit history
git log --oneline

# Switch back to the master branch
git switch master

# Check the original format of audience.txt 
# ->  It doesn't show commit in head of latest commit in master Branch
git log --oneline
```

```bash
# Delete the bugfix branch
git branch -d bugfix

# If not fully merged, force delete the branch
git branch -D bugfix
```

### Comparing Branches

Check commits and differences between branches

```bash
# Show commits in bugfix that don't exist in master
git log master..bugfix

# Show detailed differences
git diff master..bugfix

# Show differences between branches
git diff bugfix

# See affected files
git diff --name-status bugf
```

### Stashing Changes

Stash changes to switch branches or temporarily store modifications.

```bash
#change auidence.txt
vim auidence.txt

# change to another branch
git switch bugfix -> you should see an error

# Stash changes before switching branches
git stash push -m "new tax rules"
```

```bash
# Untracked files are not included in the stash
echo hello > newfile.txt

# Stash changes with a message
git stash -am ""

# List stashes
git stash list

# Switch to the 'bugfix' branch
git switch bugfix

# Switch to the 'master' branch
git switch master

# Show changes in a specific stash
git stash show 1

# Apply changes from a specific stash
git stash apply

# Drop a specific stash
git stash drop 1

# Clear all stashes
git stash clear
```

### Merging Branches

```bash
# Display a compact log with one-line entries, showing all branches in a graph
git log --oneline --all --graph
```

#### Fast-forward Merges

Merge changes when branches have diverged and can be fast-forwarded.

```bash
# Perform a fast-forward merge
git merge bugfix
```

```bash
Updating a642e12..1bde44c
Fast-forward
 audience.txt | 5 ++---
 1 file changed, 2 insertions(+), 3 deletions(-)
```

#### 3-way Merges

Merge branches with divergent changes using a 3-way merge.

```bash
# Create a new branch and make changes
git switch -C bug/login
vim toc.txt
git add .
git commit -m "update toc.txt"

# Switch back to master and perform a 3-way merge
git switch master
git merge --no-ff bug/login
```

#### Disable Fast Forward

Disable fast-forward merges to preserve branch history

```bash
# Disable fast forward in the current repository
git config ff no

# Disable fast forward globally
git config --global ff no
```

#### Three-way Merge

```bash
# Create a new branch and make changes
git switch -C feature/change-password
echo hello > change-password.txt
git commit -am "XX"

# Switch back to master and make conflicting changes
git switch master
vim objective.txt
git commit -am "XX"

# Perform a three-way merge
git merge feature/change-password
```

### Viewing merge branch

Check branches that are merged or not merged.

```bash
# View branches that are merged
git branch --merged

# View branches that are not merged
git branch --no-merged
```

### Merge Conflicts

Resolve conflicts when merging branches.

```bash
# Create a conflict scenario
git switch -C bug/changepass
vim change.txt
git add .
git commit -m "X"

# Switch back to master and make conflicting changes
git switch master
vim change.txt
git add .
git commit -m "X"

# Attempt to merge with conflicts
git add .
git commit -m "X"
```

### Aborting and Undoing Merges

Stop an ongoing merge operation.

```bash
# Abort the current merge
git merge --abort
```

### Undoing a faulty merge

Revert or reset to undo a merge.

remove the last commit (just used when You haven't shared with others yet)

```
git reset --hard HEAD~1

```

- **soft** → just change to last commit
- **mixed** → change to last commit and change staging area
- **hard** → change to last commit and change staging area and change working directory
- `revert` the last commit (shared with others)

```bash
# Revert the last commit (shared with others)
git revert HEAD~1
git revert -m1 HEAD~1
```

### Squash Merging

**Combining Commits into One**: Merge multiple commits into a single commit.

```bash
# Create a new branch and make multiple commits
git switch -C photo
echo bugfix >> audience.txt
git commit -am "X"
echo bugfix >> toc.txt
git commit -am "X"

# Switch back to master and perform a squash merge
git switch master
git merge --squash photo
git status -s
git commit -m "fix the bug on the photo branch"
```

> note when you add `git merge --sqush` is supper important to remove your get branch beacause it doesen't in merged branched
> 

### Rebasing

Rebase a branch onto another, usually to update it with the latest changes.

```bash
# Create a new branch and make changes
git switch -C shopping
echo hello > cart.txt
git add .
git commit -m "X"

# Switch back to master and make changes
git switch master
echo hello >> toc.txt
git commit -m "X"

# Rebase the shopping branch onto master
git switch shopping  #target branch
git rebase master    # change the base of yhis branch to last commit on master
git switch master
git merge shopping
```

#### Rebase Conflicts

Resolve conflicts during a rebase.

```bash
# Create a conflict scenario during rebase
echo ocean > toc.txt
git commit -am "Update toc.txt"
git switch shopping
echo mountain > toc.txt
git commit -am "Update toc.txt"
git rebase master        # we have confilict
git rebase --continue    # Apply the next commit on top of the master branch
git rebase --skip        # Skip this commit and move on to the next commit during rebase
git rebase --abort       # Go back to the previous state before starting the rebase
```

### Cherry Picking

Apply selected commits from one branch to another.

if one commit in another branch has interesting file, but we aren't ready for merge all branch

```bash
# Cherry pick a specific commit from another branch
git cherry-pick <COMMIT ID>
git status -s
git commit -m "X"
```

### Picking file from another branch

Integrate changes from one branch into another for specific files

```bash
# Create a new branch and make changes
git switch -C sendEmail
echo river > toc.txt
git commit -am "update toc.txt"

# Switch back to master and pick a file from the sendEmail branch
git switch master
git restore --source=sendEmail -- toc.txt
git status -s
git add .
git commit -m "X"
```