# pwd

> Prints the absolute path of the current working directory.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | File Management |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 3 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

The `pwd` (Print Working Directory) command displays the full path of the directory you are currently working in.

It is one of the most frequently used Linux commands because almost every filesystem operation depends on knowing your current location.

- **What does it do?** Displays the current working directory.
- **Why does it exist?** Helps users understand their current location in the filesystem before performing operations.
- **When is it commonly used?** Before navigating directories, creating files, copying data, or executing scripts.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display your current directory
- Understand absolute paths
- Verify your location before running commands
- Use `pwd` effectively in shell scripts

---

# ⚙️ Syntax

```bash
pwd [OPTION]
```

---

# 📝 Parameters

The `pwd` command does not require any positional parameters.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-L` | Display the logical current directory (default behavior). |
| `-P` | Display the physical directory, resolving symbolic links. |

---

# 💻 Basic Examples

## Example 1

```bash
pwd
```

Displays your current working directory.

Example output:

```text
/home/revanth
```

---

## Example 2

```bash
pwd -P
```

Displays the physical path by resolving symbolic links.

Example:

```text
/var/www/project
```

---

## Example 3

```bash
cd /etc
pwd
```

Output:

```text
/etc
```

Confirms that the current directory has changed successfully.

---

# 📤 Example Output

```text
$ pwd

/home/revanth/Documents/Nexora
```

This means your shell is currently operating inside:

```
/home/revanth/Documents/Nexora
```

---

# 🌍 Real-world Use Cases

- Confirming your location before deleting files.
- Checking the current directory inside deployment scripts.
- Verifying paths while debugging shell scripts.
- Displaying the current directory in automation workflows.
- Ensuring commands execute in the intended project folder.

---

# 🧠 How It Works

Every shell maintains a record of the current working directory.

When you execute `pwd`, the shell prints this directory.

With the `-P` option, the shell resolves symbolic links and prints the actual physical location on disk.

---

# ⚠️ Common Mistakes

❌ Assuming you're in the correct directory without checking.

Always verify your location before using commands like:

```bash
rm
mv
cp
```

---

❌ Confusing relative paths with absolute paths.

`pwd` always displays the absolute path.

---

❌ Forgetting symbolic links.

If you're inside a symbolic link, `pwd` and `pwd -P` may display different paths.

---

# ✅ Best Practices

- Run `pwd` before performing destructive operations.
- Use `pwd` inside shell scripts for debugging.
- Prefer absolute paths when documenting procedures.
- Combine `pwd` with `ls` to inspect your current location.

---

# 🔒 Security Considerations

`pwd` itself is harmless.

However, sharing terminal screenshots that include `pwd` may reveal sensitive directory structures, usernames, or project locations.

---

# 🚀 Performance Notes

`pwd` is extremely fast.

It simply retrieves and prints the shell's current working directory.

Its execution time is effectively constant regardless of directory size.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `ls` | Lists files in the current directory |
| `cd` | Changes the current directory |
| `find` | Searches for files and directories |
| `realpath` | Displays the canonical absolute path |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `pwd` | Shows your current location |
| `cd` | Changes your location |
| `ls` | Displays contents of your current location |

---

# 🧪 Practice Exercises

### Beginner

Display your current directory.

---

### Intermediate

Navigate to `/usr/bin` and verify your location using `pwd`.

---

### Advanced

Create a symbolic link to a directory and compare the outputs of:

```bash
pwd
```

and

```bash
pwd -P
```

Explain the difference.

---

# 💼 Real Interview Questions

### Beginner

**Q: What does the `pwd` command do?**

A: It prints the absolute path of the current working directory.

---

### Intermediate

**Q: What is the difference between `pwd` and `pwd -P`?**

A: `pwd` displays the logical path, while `pwd -P` resolves symbolic links and displays the physical filesystem path.

---

### Advanced

**Q: Why is `pwd` useful in shell scripts?**

A: It helps verify the script's execution location, making debugging easier and preventing file operations from occurring in the wrong directory.

---

# 🛠 Troubleshooting

### Problem

`pwd` displays an unexpected directory.

### Cause

The shell is currently operating in a different directory than expected.

### Solution

Use:

```bash
cd <directory>
pwd
```

to navigate and verify your location.

---

# 📚 Official Documentation

- GNU Coreutils `pwd` manual (`man pwd`)
- POSIX `pwd` specification

---

# 📖 Further Reading

- Nexora: `cd` command
- Nexora: `ls` command
- Nexora: Linux Filesystem Concepts

---

# 📌 Quick Summary

- `pwd` prints the current working directory.
- It displays an absolute path.
- `-L` shows the logical path.
- `-P` resolves symbolic links.
- Use `pwd` before performing filesystem operations.

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