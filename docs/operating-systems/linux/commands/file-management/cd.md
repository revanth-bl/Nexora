# cd

> Changes the current working directory, allowing you to navigate the Linux filesystem.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | File Management |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 5 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

The `cd` (Change Directory) command is used to move between directories in the Linux filesystem.

Unlike commands that display or manipulate files, `cd` changes your shell's current working directory. Nearly every Linux workflow begins with navigating to the correct location.

- **What does it do?** Changes the current working directory.
- **Why does it exist?** Allows users to navigate the filesystem efficiently.
- **When is it commonly used?** Before creating files, editing projects, running scripts, or managing system resources.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Navigate between directories
- Understand absolute and relative paths
- Return to your home directory
- Move to the previous directory
- Avoid common navigation mistakes

---

# ⚙️ Syntax

```bash
cd [directory]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `directory` | The destination directory. | No |

If no directory is provided, `cd` takes you to your home directory.

---

# 🔧 Common Usage

| Command | Description |
|---------|-------------|
| `cd` | Go to the home directory |
| `cd ~` | Go to the home directory |
| `cd ..` | Move up one directory |
| `cd ../..` | Move up two directories |
| `cd -` | Return to the previous directory |
| `cd /` | Go to the root directory |
| `cd /path/to/folder` | Navigate using an absolute path |

---

# 💻 Basic Examples

## Example 1

```bash
cd Documents
```

Moves into the `Documents` directory.

---

## Example 2

```bash
cd ..
```

Moves to the parent directory.

---

## Example 3

```bash
cd ~
```

Returns to your home directory.

---

## Example 4

```bash
cd -
```

Returns to the previously visited directory.

---

## Example 5

```bash
cd /var/log
```

Moves directly to the `/var/log` directory.

---

# 📤 Example Output

```text
$ pwd
/home/revanth

$ cd Documents

$ pwd
/home/revanth/Documents
```

The current working directory changes after executing `cd`.

---

# 🌍 Real-world Use Cases

- Navigating to a project folder before running Git commands.
- Moving into `/var/log` to inspect system logs.
- Switching between project directories during development.
- Accessing configuration directories before editing files.
- Returning to the previous directory using `cd -`.

---

# 🧠 How It Works

Every shell session keeps track of its current working directory.

When you run `cd`, the shell updates this location. Since the current directory is a property of the shell itself, `cd` is implemented as a **shell builtin** rather than a standalone program.

---

# ⚠️ Common Mistakes

❌ Forgetting to quote directory names containing spaces.

Incorrect:

```bash
cd My Folder
```

Correct:

```bash
cd "My Folder"
```

---

❌ Using the wrong path.

Verify your location first:

```bash
pwd
ls
```

---

❌ Confusing absolute and relative paths.

Example:

```bash
cd /etc
```

Absolute path.

```bash
cd etc
```

Relative path.

---

# ✅ Best Practices

- Use `pwd` frequently to verify your location.
- Prefer tab completion instead of typing long directory names.
- Use `cd -` to switch quickly between two directories.
- Organize projects so navigation remains simple.

---

# 🔒 Security Considerations

The `cd` command itself does not modify data.

However, navigating to the wrong directory before executing commands like `rm`, `mv`, or `chmod` can lead to accidental data loss.

Always verify your location using:

```bash
pwd
```

---

# 🚀 Performance Notes

`cd` executes almost instantly because it only changes the shell's current working directory.

Performance is generally unaffected by directory size.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `pwd` | Displays the current directory |
| `ls` | Lists the contents of a directory |
| `mkdir` | Creates directories |
| `find` | Searches for directories |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `cd` | Changes your location |
| `pwd` | Displays your current location |
| `ls` | Displays contents of the current location |

---

# 🧪 Practice Exercises

### Beginner

Navigate to your home directory.

---

### Intermediate

Navigate to `/etc`, then return to your previous directory using `cd -`.

---

### Advanced

Create a nested directory structure and practice moving between directories using both relative and absolute paths.

---

# 💼 Real Interview Questions

### Beginner

**Q: What does the `cd` command do?**

A: It changes the current working directory.

---

### Intermediate

**Q: What is the difference between an absolute path and a relative path?**

A: An absolute path starts from the root (`/`), while a relative path starts from the current working directory.

---

### Advanced

**Q: Why is `cd` implemented as a shell builtin instead of a normal executable?**

A: Because changing the working directory of a child process would not affect the parent shell. Implementing `cd` as a shell builtin allows it to change the shell's own working directory.

---

# 🛠 Troubleshooting

### Problem

```text
bash: cd: directory: No such file or directory
```

### Cause

The specified directory does not exist or the path is incorrect.

### Solution

Verify the directory exists:

```bash
ls
pwd
find . -type d
```

---

# 📚 Official Documentation

- GNU Bash Manual (`help cd`)
- Bash Reference Manual
- POSIX Shell Specification

---

# 📖 Further Reading

- Nexora: `pwd`
- Nexora: `ls`
- Nexora: Linux Filesystem Concepts

---

# 💡 Did You Know?

Unlike many Linux commands, `cd` is a **shell builtin**. If it were an external program, it could only change its own working directory—not the shell you're using. That's why `cd` must be part of the shell itself.

---

# 📌 Quick Summary

- `cd` changes the current working directory.
- `cd` → Home directory.
- `cd ..` → Parent directory.
- `cd -` → Previous directory.
- `cd /` → Root directory.
- Supports both absolute and relative paths.

---

# 🤝 Contributors

| Name | Contribution |
|------|--------------|
| Revanth B L | Initial version |

---

# 📝 Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-09 | Initial version |