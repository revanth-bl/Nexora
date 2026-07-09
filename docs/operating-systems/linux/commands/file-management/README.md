# 📁 File Management Commands

> Learn how to navigate, create, copy, move, rename, and delete files and directories in Linux.

---

## 📖 Overview

File management is one of the most fundamental skills in Linux. Whether you're a beginner exploring the terminal or a DevOps engineer managing production servers, you'll constantly work with files and directories.

This section of Nexora provides practical documentation for the most commonly used Linux file management commands, explaining not only **how** to use them, but also **why**, **when**, and **where** they are used in real-world environments.

---

## 🎯 Learning Objectives

By completing this section, you will learn how to:

- Navigate the Linux filesystem
- Create files and directories
- Copy and move files safely
- Rename files and folders
- Delete files and directories
- View directory contents
- Understand absolute and relative paths
- Follow best practices to avoid accidental data loss

---

# 📚 Commands Covered

| Command | Purpose | Difficulty |
|----------|---------|------------|
| [`ls`](./ls.md) | List files and directories | 🟢 Beginner |
| [`cd`](./cd.md) | Change the current directory | 🟢 Beginner |
| [`pwd`](./pwd.md) | Display the current working directory | 🟢 Beginner |
| [`mkdir`](./mkdir.md) | Create directories | 🟢 Beginner |
| [`touch`](./touch.md) | Create empty files or update timestamps | 🟢 Beginner |
| [`cp`](./cp.md) | Copy files and directories | 🟢 Beginner |
| [`mv`](./mv.md) | Move or rename files and directories | 🟢 Beginner |
| [`rm`](./rm.md) | Remove files and directories | 🟡 Intermediate |

---

# 🧭 Recommended Learning Order

If you're new to Linux, follow this order:

1. `pwd`
2. `ls`
3. `cd`
4. `mkdir`
5. `touch`
6. `cp`
7. `mv`
8. `rm`

Each command builds upon the previous one, helping you develop confidence while working in the terminal.

---

# 🌍 Real-world Applications

These commands are used every day by:

- Linux System Administrators
- DevOps Engineers
- Cloud Engineers
- Backend Developers
- Cybersecurity Professionals
- Site Reliability Engineers (SREs)
- Students learning Linux

Typical tasks include:

- Managing project directories
- Organizing source code
- Deploying applications
- Managing configuration files
- Working with logs
- Automating scripts
- Cleaning temporary files

---

# ⚠️ Common Mistakes

New Linux users often:

- Delete files using `rm` without verifying the path.
- Confuse absolute and relative paths.
- Accidentally overwrite files using `cp` or `mv`.
- Forget hidden files when checking a directory.
- Run destructive commands as the root user without caution.

Understanding these commands thoroughly helps prevent common mistakes that can lead to data loss.

---

# 💡 Best Practices

- Always verify your current location using `pwd`.
- Use `ls -la` before modifying unfamiliar directories.
- Prefer relative paths inside projects for portability.
- Double-check commands before using `rm -rf`.
- Create directories with meaningful names.
- Keep project files organized into logical folders.

---

# 🔗 Related Topics

After completing this section, continue with:

- Linux Filesystem Hierarchy
- File Permissions
- Users and Groups
- Shell Navigation
- Bash Scripting Basics

---

# 📖 Further Reading

- Linux Concepts
- Linux Best Practices
- Linux Cheat Sheets
- Linux Labs

---

# 🚀 What's Next?

Start with the first command:

➡️ **[`pwd`](./pwd.md)** — Learn how to identify your current working directory before navigating the filesystem.

After mastering `pwd`, continue with **`ls`**, the command used to inspect files and directories.

---

> **Remember:** Efficient file management is the foundation of working confidently in Linux. Almost every command you'll learn later depends on understanding the filesystem first.