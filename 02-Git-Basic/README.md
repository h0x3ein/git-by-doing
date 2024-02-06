# Chapter 2: Git Basic Command

Welcome to Chapter 2, where we'll dive deep into the core functionalities of Git. This chapter is designed to provide a solid foundation in Git, starting with basic concepts and moving on to more complex operations. To get a better understanding of how Git tracks changes, it's recommended to start with this article on [git index](https://www.javatpoint.com/git-index).


## 📚 Table of Contents
- [📜 Creating Files](#-creating-files)
- [💎 Staging Files](#-staging-files)
- [🔍 Modifying Content](#-modifying-content)
- [📖 Committing Changes](#-committing-changes)
- [👀 Direct Committing](#-direct-committing)
- [🏃 Removing Files](#-removing-files)
- [📖 Renaming Files](#-renaming-files)
- [🔍 Managing Directories](#-managing-directories)
- [👀 Reviewing Changes](#-reviewing-changes)
- [👀 Viewing History](#-viewing-history)
- [🏃 Undoing Changes](#-undoing-changes)
- [🔍 Restoring Files](#-restoring-files)
- [📝 Tasks](#-tasks)

## 🎯 Learning Objectives

In this chapter, you'll learn the basics of Git through a series of practical tasks. Follow these steps to get hands-on experience with creating, managing, and manipulating files and directories in a Git repository.


### 📜 [Creating Files](#creating-files)

Learn the basics of creating new files within your Git repository, setting the stage for tracking changes.

### 💎 [Staging Files](#staging-files)

Understand how to stage files, preparing them for inclusion in your next commit, a crucial step in version control.

### 🔍 [Modifying Content](#modifying-content)

Discover the process of making changes to your files and how those modifications are tracked by Git.

### 📖 [Committing Changes](#committing-changes)

Master the act of committing staged changes to your repository, marking a snapshot of your project's current state.

### 👀 [Direct Committing](#direct-committing)

Explore the method of committing changes directly, bypassing the staging area for quick updates.

### 🏃 [Removing Files](#removing-files)

Learn how to properly remove files from your repository and stage these deletions for committing.

### 📖 [Renaming Files](#renaming-files)

Understand the process of renaming files in your repository and how Git tracks this as a change.

### 🔍 [Managing Directories](#managing-directories)

Get to grips with managing directories in your Git project, including adding, renaming, and removing directories.

### 👀 [Reviewing Changes](#reviewing-changes)

Discover how to review changes before committing, ensuring that only intended modifications are included.

### 👀 [Viewing History](#viewing-history)

Learn to navigate the commit history of your repository, understanding the evolution of your project over time.

### 🏃 [Undoing Changes](#undoing-changes)

Master techniques for undoing changes, including unstaging files and reverting committed changes.

### 🔍 [Restoring Files](#restoring-files)

Understand how to restore deleted files or revert files to a previous state using Git's powerful version control capabilities.


## 📝 Tasks

### Creating Files

- **Task 1**: Create `file1.txt` and write "hello".
  ```bash
  touch file1.txt && echo "hello" > file1.txt
  ```       

- **Task 2**: Create `file2.txt` and add "hello".
  ```bash 
  touch file2.txt && echo "hello" > file2.txt 
  ```

### Staging Files

- **Task 3**: Add `file1.txt` and `file2.txt` to the staging area.
  ```bash
  git add file1.txt file2.txt
  ```

### Modifying Content

- **Task 4**: Update `file1.txt` to contain "world".
    ```bash
  echo "world" > file1.txt
  ```

- **Task 5**: Stage the updated `file1.txt`.
    ```bash
  git add file1.txt
  ```

### Committing Changes

- **Task 6**: Commit your staged changes.
    ```bash
  git commit -m "Initial commit of file1.txt and file2.txt"
    ```

### Direct Committing

- **Task 7**: Modify `file1.txt` to "test" and commit without staging.
  ```bash
  echo "test" > file1.txt && git commit -am "Updated file1.txt directly"
  ```

### Removing Files

- **Task 8**: Remove `file2.txt` from the repository.
  ```bash
  git rm file2.txt && git commit -m "Removed file2.txt"
  ```

### Renaming Files

- **Task 9**: Rename `file1.txt` to `main.js`.
    ```bash
  git mv file1.txt main.js && git commit -m "Renamed file1.txt to main.js"
    ```

### Managing Directories

- **Task 10**: Create a "logs" directory and add `dev.log`, then ignore it.
  ```bash
  mkdir logs
  echo "hello" > logs/dev.log
  echo "logs/" >> .gitignore
  git add .gitignore
  git commit -m "Added logs to .gitignore"
    ```

- **Task 11**: Create a "bin" directory, add `app.bin`, commit it, then ignore the directory.
  ```bash
  mkdir bin
  echo hello > bin/app.bin
  git add .
  git commit -m "add bin"
  echo bin/ >> .gitignore
  echo world >> bin/app.bin
  git status -> You see `bin/app.bin` was modified
  git rm -r --cached bin/
  git commit -m "Remove accidentally committed bin directory"
  ```
    

### Reviewing Changes

- **Task 12**: View staged and unstaged changes.
  ```bash
  git diff --staged
  git diff
  ```

### Viewing History

- **Task 13**: Check the commit history.
  ```bash
  git log
  git log --oneline
  git log --oneline --reverse
  ```

- **Task 14**: Examine specific commits.
  ```bash
  git show <commit-hash>
  git show HEAD~1
  git show deasdd2
    ```

### Undoing Changes

- **Task 15**: Unstage changes.
  ```bash
  git restore --staged <file-name>
  ```

- **Task 16**: Discard all local changes and restore the repository to the last committed state.
  ```bash
  git restore .
  git clean -fd
  ```

### Restoring Files

- **Task 17**: Remove `file.js`, commit the removal, and then restore it from a previous version.
  ```bash a
  git rm file1.js
  git commit -m "Removed file1.js"
  git restore --source=HEAD~1 file1.js
  ```
