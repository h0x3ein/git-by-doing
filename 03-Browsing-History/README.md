# **Chapter 3: Browsing History in Git**

In this chapter, we explore Git's powerful features for navigating and understanding the history of your project. Learn how to view, filter, and format commit logs, work with aliases for efficiency, inspect changes in commits, and more. This chapter aims to provide you with comprehensive tools for effective version control and collaboration.

## 📚 Learning Objectives
  - [🔍 Viewing the History](#-viewing-the-history)
  - [💾 Filtering the History](#-filtering-the-history)
  - [📖 Formatting the Log Output](#-formatting-the-log-output)
  - [⚙️ Creating Aliases](#-creating-aliases)
  - [👁️ Viewing a Commit](#-viewing-a-commit)
  - [🔍 Viewing Changes Across Commits](#-viewing-changes-across-commits)
  - [🕰️ Checking Out a Commit](#-checking-out-a-commit)
  - [🐛 Finding a Bug with Bisect](#-finding-a-bug-with-bisect)
  - [🏷️ finding contributes Using Shortlog](#-finding-contributions-using-shortlog)
  - [♻️ Restoring a Deleted File](#-restoring-a-deleted-file)
  - [🔎 Using `git blame` to Identify Changes](#-using-git-blame-to-identify-changes)
  - [🏷️ Working with Tags](#-working-with-tags)
  - [📝 Tasks](#-tasks)
  

## 🎯 Learning Objectives

In this chapter, you'll learn the intricacies of navigating and manipulating your project's history in Git through a series of practical tasks. Follow these steps to gain hands-on experience with reviewing past changes, managing versions, and ensuring efficient project tracking.

### 🔍 [Viewing the History](#viewing-the-history)

Learn how to use **`git log`** and other commands to review the commit history, providing insights into the evolution of your project.

### 💾 [Filtering the History](#filtering-the-history)

Discover how to filter the commit log based on criteria like author, date, or keywords to find specific changes or contributions.

### 📖 [Formatting the Log Output](#formatting-the-log-output)

Explore customizing the appearance of the commit history using formatting options for better readability and information extraction.

### ⚙️ [Creating Aliases](#creating-aliases)

Understand how to create shorthand commands, or aliases, for complex Git commands to streamline your workflow.

### 👁️ [Viewing a Commit](#viewing-a-commit)

Learn the details of inspecting individual commits, including the changes made and metadata associated with each commit.

### 🔍 [Viewing Changes Across Commits](#viewing-changes-across-commits)

Master the technique of comparing changes between different commits or branches to understand the evolution of specific parts of your project.

### 🕰️ [Checking Out a Commit](#checking-out-a-commit)

Discover how to navigate your project's history by checking out specific commits, allowing you to review or build previous states of your project.

### 🐛 [Finding a Bug with Bisect](#finding-a-bug-with-bisect)

Learn to use **`git bisect`** to perform a binary search through your project's history to identify the commit that introduced a bug.

### 🏷️ [Finding Contributions Using Shortlog](#finding-contributes-using-shortlog)

Understand how to summarize git log output with **`git shortlog`** to see contributions by each author, aiding in project management and collaboration.

### ♻️ [Restoring a Deleted File](#restoring-a-deleted-file)

Discover the process for restoring files that were deleted in previous commits, effectively recovering lost work.

### 🔎 [Blaming](#blaming)

Learn to use **`git blame`** to trace changes in a file back to specific commits, helping identify who made certain changes and why.

### 🏷️ [Tagging](#tagging)

Master the practice of tagging specific commits in your history, typically used for marking release points like v1.0, v2.0, etc.


## 📝 Tasks

### Viewing the history

**Summary of all commits**

  ```bash 
   git log
  ```

**Summary of all commits in one line**

```bash
git log --oneline
```

**List files changed in a commit**

```bash
git log --oneline --stat
```

**Detailed information about each commit**

```bash
git log --stat
```

**See actual changes in each commit**

```bash
git log --oneline --patch
```

### Filtering the history

**See last three commits**

```bash
git log --oneline -3
```

**Filter commits by author**

```bash
git log --oneline --author="Hossein"
```

**Filter commits by date (before or after a specific date)**

```bash
git log --oneline --before="2020-08-17" or git log --oneline --after="2020-08-17"
```

**Filter commits by relative date (e.g., yesterday, two weeks ago)**

```bash
git log --oneline --after="yesterday" 
or 
git log --oneline --after="two weeks ago"
```

**Filter commits by submit message (commit message contains specific text)**

```bash
git log --oneline --grep="GUI"
```

**Filter commits by changes in a specific function (add or remove)**

```bash
git log --oneline -S"OBJECTIVES"
```

**See actual changes in a specific commit**

```bash
git log --oneline --patch -S"OBJECTIVES"

```

**Filter commit history by a range of commits**

```bash
git log --oneline fb034ss..edb3595
```

**Find all commits that modified a specific file**

```bash
git log --oneline toc.txt
or 
git log --oneline -- toc.txt
```

<aside>
💡 The double hyphen (`--`) is typically used to separate the Git command options from the filenames when there is a possibility of ambiguity.

</aside>


**See actual changes in a specific file**

```bash
git log --oneline --patch toc.txt
```

### Formatting the Log Output

**Display author name in a specific format**

```bash
git log --pretty=format:"hello %an"
```

**See author name and full hash for each commit**

```bash
git log --pretty=format:"%an committed %H"
```

**See author name and abbreviated hash for each commit.**

```bash
git log --pretty=format:"%an committed %h"
```

**See author name, abbreviated hash, and commit date for each commit**

```bash
git log --pretty=format:"%an committed %h on %cd"
```

**Change the color of the author name to green**

```bash
git log --pretty=format:"%Cgreen%an committed %h on %cd"
```
**Change the color of the author name to green and reset to default color**

```bash
git log --pretty=format:"%Cgreen%an%Creset committed %h on %cd"
```

### Creating Aliases

**Add an alias to see the log**

```bash
git config --global alias.lg "log --pretty=format:'%an committed %h'"
```

**View the Git configuration file**

```bash
git config --global -e
```

**Add an alias to** `unstage` **files**

```bash
git config --global alias.unstage "restore --staged ."
```

### Viewing a Commit

**View the changes in a commit, two steps back from HEAD**

```bash
git show HEAD~2
```

**View the changes in a specific file from a commit two steps back from HEAD**

```bash
git show HEAD~2:sections/creating-snapshots/staging-changes.txt
```

**List all files modified, deleted, or added in a commit two steps back from HEAD**

```bash
git show HEAD~2 --name-only
```

**Show the status (modified, deleted, or added) of each file in a commit two steps back from HEAD**

```bash
git show HEAD~2 --name-status
```

### Viewing changes across Commits

**Compare the changes between the commit two steps back from HEAD and the most recent commit**

```bash
git diff HEAD~2 HEAD
```

**Compare the changes in a specific file between the commit two steps back from HEAD and the most recent commit**

```bash
git diff HEAD~2 HEAD audience.txt
```

**Compare the changes in all files between the commit two steps back from HEAD and the most recent commit**

```bash
git diff HEAD~2 HEAD --name-only
```

**Compare the changes in all files with their change type between the commit two steps back from HEAD and the most recent commit**

```bash
git diff HEAD~2 HEAD --name-status
```

### Checking out a commit

**Checkout a specific commit by its hash ID**

```bash
git checkout <HASH ID>
```

**Checkout the master branch**

```bash
git checkout master
```

### Finding a bug with bisect

**Start the Git bisect process**

```bash
git bisect start
```

**Mark the current state as a bad (faulty) point**

```bash
git bisect bad
```

**Mark a known good commit as a reference point**

```bash
git bisect good <good commit id>
```

**Mark the current state as a good (working) point**

```bash
git bisect good
```

**Continue the bisect process by marking the current state as good**

```bash
git bisect good
```

**Continue the bisect process by marking the current state as bad**

```bash
git bisect bad
```

**Observe the changes in the identified problematic commit**

```bash
git bisect bad
```

**Reset and exit the bisect process**

```bash
git bisect reset
```

### finding contributes Using **Shortlog**

**View a summary of contributors to the repository**

```bash
git shortlog
```

**Get help on using the git** `shortlog` **command**

```bash
git shortlog --help
```

```
git shortlog -> see who contribute to this repository
git shortlog --help

```

### Restoring a Deleted File

Remove the file `toc.txt` from the repository

```bash
git rm toc.txt
```

**Commit the removal of** `toc.txt`

```bash
git commit -m "Remove toc.txt"
```

**View the commit history for** `toc.txt`

```bash
git log --oneline -- toc.txt
```

**Restore the content of** `toc.txt` **to a specific commit**

```bash
git checkout <Parent Commit ID>
```
**Switch to a specific commit by its hash ID**

```bash
git checkout a642e12
```

**Commit the restoration of** `toc.txt`

```bash
git commit -m "Restore toc.txt"
```

### Blaming

**Identify the commit and author responsible for each line of the file** `audience.txt`

```bash
git blame audience.txt
```

**View the email addresses of the authors responsible for each line of the file** `audience.txt`

```bash
git blame -e audience.txt
```

**View the commit and author information for a specific range of lines in the file** `audience.txt`

```bash
git blame -e -L 1,3 audience.txt
```

### Tagging

**Create a new tag named** `v1.0` **at an earlier commit**

```bash
git tag v1.0 <Earlier commit ID>
```

**Checkout a specific tag,** `v1.0`

```bash
git checkout v1.0
```

**View all tags in the repository**

```bash
git tag
```
**Create an annotated tag `v1.1` with a descriptive message**

```bash
git tag -a v1.1 -m "My new version 1.1"
```
**View tags along with their associated messages**

```bash
git tag -n
```

**View detailed information about a specific tag,** `v1.1`

```bash
git show v1.1
```