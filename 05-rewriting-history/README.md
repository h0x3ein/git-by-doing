# Chapter 6: Reviewing History
In Chapter 6, "Reviewing History," we turn our focus to the vital task of managing and refining your project's commit history. Building upon the foundational skills acquired in previous chapters on basic Git commands, branching, and merging, this chapter introduces advanced techniques for undoing, amending, and reorganizing commits. Mastering these skills will empower you to maintain a clear and meaningful project history, facilitating better understanding and collaboration.

## Useful Resource 
[Mercury.zip](https://prod-files-secure.s3.us-west-2.amazonaws.com/641efa2f-077c-41dd-b00b-9f40bc8a4811/0859ab07-71c0-406c-94fd-d7cd32d2553c/Mercury.zip)


## 📚 Table of Contents

- [🌿 Undoing Commits](#-undoing-commits)
- [🔍 Reverting Commits](#-reverting-commits)
- [💾 Recovering the Last Commit](#-recovering-the-last-commit)
- [🔀 Amending the Last Commit](#-amending-the-last-commit)
- [⚔️ Accidentally Adding a File to a Commit](#-accidentally-adding-a-file-to-a-commit)
- [🔍 Amending an Earlier Commit](#-amending-the-last-commit)
- [🌿 Drop a Commit](#-drop-a-commit)
- [💾 Rewording Commit Message](#-rewording-commit-message)
- [🛠️ Reordering Commits](#-reordering-commits)
- [💾 Squashing Commits](#-squashing-commits)
- [🍒 Splitting a Commit](#-splitting-a-commit)
- [📝 Tasks](#-tasks)

## 🎯 Learning Objectives

This chapter aims to enhance your proficiency in managing your project's commit history with precision and clarity. You'll learn various methods to undo, revise, and optimize commits to ensure your project history is both accurate and informative.

### 🌿 [Undoing Commits](#undoing-commits)

Explore techniques to undo the effects of previous commits, providing a safety net for correcting mistakes.

### 🔍 [Reverting Commits](#reverting-commits)

Learn how to revert the changes made by past commits, effectively creating new commits that undo previous modifications.

### 💾 [Recovering the Last Commit](#recovering-the-last-commit)

Discover methods to recover the most recent commit if it was accidentally lost or altered.

### 🔀 [Amending the Last Commit](#amending-the-last-commit)

Understand how to amend the latest commit to include overlooked changes or corrections without creating an additional commit.

### ⚔️ [Accidentally Adding a File to a Commit](#accidentally-adding-a-file-to-a-commit)

Find out how to remove an accidentally committed file from your repository, ensuring your commit history remains relevant.

### 🔍 [Amending an Earlier Commit](#amending-an-earlier-commit)

Delve into advanced techniques for amending commits that are not at the top of the history, maintaining a clean and accurate log.

### 🌿 [Drop a Commit](#drop-a-commit)

Master the process of removing specific commits from your history, useful for discarding unnecessary or problematic changes.

### 💾 [Rewording Commit Message](#rewording-commit-message)

Learn how to change the commit messages of previous commits to enhance clarity and convey more meaningful information.

### 🛠️ [Reordering Commits](#reordering-commits)

Understand how to rearrange the order of commits in your project history for better logical grouping and readability.

### 💾 [Squashing Commits](#squashing-commits)

Discover how to combine multiple commits into a single commit, simplifying your project history and consolidating related changes.

### 🍒 [Splitting a Commit](#splitting-a-commit)

Learn the technique of splitting a large commit into smaller, more manageable commits for greater clarity and control over your project history.

## 📝 Tasks
### Undoing Commits

Provides methods to reverse the effects of commits, either by creating a new commit that undoes changes (**`git revert`**) or by resetting the branch pointer to a previous commit (`git reset`).

```bash
# Revert the last commit
git revert HEAD

# Reset to the previous commit (locally)
git reset --hard HEAD~1
```

- **soft**: Removes the commit but keeps changes staged.
- **mixed**: Unstages changes.
- **hard**: Discards local changes.

```bash
bashCopy code
# Soft reset, see changes, and stage them
git reset --soft HEAD~1
git status -sced
git diff --cached
```

### Reverting Commits

Describes how to revert multiple commits, typically when undoing a range of changes in the commit history

```bash
# Revert multiple commits
git revert HEAD~3..HEAD

# Alternatively, reset and revert specific commits
git reset --hard HEAD~3
git revert --no-commit HEAD~3..HEAD
git status -s
# If satisfied, continue
git revert --continue
# If issues, abort the revert
git revert --abort
```

### Recovering the Last Commit

Guides on recovering from a reset or unintentional changes by using the reflog to identify the commit and reset the branch back to it

```bash
# Reset to a previous commit and recover with reflog
git reset --hard HEAD~6
git reflog
git reset --hard HEAD@{1}
git reflog show feature  # Show the history of the feature
```

### Amending the Last Commit

Demonstrates the process of modifying the most recent commit, including adding changes and altering the commit message.

```bash
# Make changes and amend the last commit
echo cafes >> map.txt
git commit -am "X"
vim map.txt  # Change text
git add .
git commit --amend
```

```bash
# Add changes to the previous commit without creating a new one
echo hello > file1.txt
git add .
git commit --amend
git log --oneline  # No new commit added
git show HEAD  # See all changes
```

### Accidentally Adding a File to a Commit

Explains steps to unstage a file from the last commit if it was mistakenly included.

```bash
# Unstage a file from the last commit
git reset --mixed HEAD~1
git status -s
git clean -fd
git add .
git commit -m "A"
```

### Amending an Earlier Commit

Illustrates how to modify an earlier commit, either by changing the commit message or adding additional changes.

```bash
# Show commit information
git show <Commit ID>
git log
git rebase -i <Parent ID>
# Change the last commit from 'pick' to 'edit'
# ...
# Make changes and commit
git rebase --continue
# or
git rebase --abort
```

### Drop a Commit

Guides through the process of removing or dropping a commit from the commit history.

```bash
# Show commit details
git show COMMIT_ID
git log --oneline
git rebase -i COMMIT_ID^  # Use the commit before the one you want to drop
# Change 'pick' to 'drop' or delete lines
git status -s
git mergetool
# Resolve conflicts if needed
git rebase --continue
git rebase -i HEAD~3
# Delete lines for multiple commits
```

### Rewording Commit Message

Explains the steps to change or reword a commit message during a rebase operation.

```bash
# Rebase for rewording a commit message
git rebase -i COMMIT_ID^
# Change 'pick' to 'reword'
# ...
```

### Reordering Commits

Details the process of rearranging the order of commits during a rebase operation.

```bash
# Reorder commits during rebase
git rebase COMMIT_ID^
# Change the order of lines
# ...
```

### Squashing Commits

Introduces the concept of combining multiple commits into a single, more concise commit during a rebase.

```bash
# Squash commits during rebase
git rebase ID
# Change 'pick' to 'squash'
# Alternatively, use 'fixup' to combine without modifying the commit message
git reflog
# Change 'pick' to 'fixup'
```

### Splitting a Commit

Provides steps for dividing a commit into smaller, more manageable commits during a rebase operation.