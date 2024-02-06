# Basic Configuration 
Before diving into Git's features, it's important to set up some basic configurations. These initial settings are simple but essential for a smooth Git experience.

## 📚 Table of Contents
- [🔍 The Git config command](#-the-git-config-command)
- [👣 Setting Username](#-setting-username)
- [👾 Set Your Email Address](#-set-your-email-address)
- [📜 Set Your Preferred Editor](#-set-your-preferred-editor)
- [⚙️ Accessing Git Configuration](#-accessing-git-configuration)
### 🔍 The Git config command

The `git config` command is your gateway to setting up Git's behavior on your system. These configurations include your **username** and **email**, which are important because they are **included** in your `commit messages` and are visible when you push changes.

**Configuration levels:**

- **System**: Settings apply to `all users` on the machine.
- **Global**: Settings apply to `all of your repositories`.
- **Local**: Settings apply only to `the current repository`.

### 👣 Setting Username

```bash
git config --global user.name "Your Name"
```
Replace `Your Name` with your actual name. This name will be attached to your commits and tags.

### 👾 Set Your Email Address

```bash
git config --global user.email "your_email@example.com"
```
Use the email address you want to associate with your Git commits.

### 📜 Set Your Preferred Editor

```bash
git config --global core.editor "code --wait"
```
This command sets Visual Studio Code as the default editor for Git. Replace `code --wait` with the command for your preferred editor.

### ⚙️ Accessing Git Configuration
To review or modify your Git configuration, use the following command to open the configuration file in your default editor:

```bash
git config --global -e
```
