# mkdir

> Creates one or more directories in the Linux filesystem.

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

The `mkdir` (Make Directory) command creates new directories (folders) in the Linux filesystem.

Directories help organize files into a structured hierarchy, making projects easier to manage and navigate.

- **What does it do?** Creates new directories.
- **Why does it exist?** Provides a simple way to organize files and build directory structures.
- **When is it commonly used?** Setting up projects, organizing documents, creating backup folders, and preparing application directories.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Create a single directory
- Create multiple directories
- Create nested directory structures
- Understand parent directory creation
- Avoid common directory creation errors

---

# ⚙️ Syntax

```bash
mkdir [OPTIONS] DIRECTORY...
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `DIRECTORY` | Name or path of the directory to create | Yes |

---

# 🔧 Common Options

| Option | Description |
|---------|-------------|
| `-p` | Create parent directories if they don't exist |
| `-v` | Display a message for each created directory |
| `-m MODE` | Set directory permissions during creation |

---

# 💻 Basic Examples

## Example 1

Create a single directory.

```bash
mkdir projects
```

---

## Example 2

Create multiple directories.

```bash
mkdir docs images videos
```

---

## Example 3

Create nested directories.

```bash
mkdir -p projects/nexora/docs
```

---

## Example 4

Show created directories.

```bash
mkdir -v backup
```

Example output:

```text
mkdir: created directory 'backup'
```

---

## Example 5

Create a directory with specific permissions.

```bash
mkdir -m 755 website
```

---

# 📤 Example Output

```text
$ mkdir projects

$ ls

projects
```

---

# 🌍 Real-world Use Cases

- Creating a new project folder.
- Organizing documents into categories.
- Preparing deployment directories.
- Creating backup locations.
- Building nested folder structures for applications.

---

# 🧠 How It Works

When you execute `mkdir`, Linux creates a new directory entry in the filesystem.

Each directory contains metadata such as:

- Owner
- Permissions
- Timestamps
- Links to parent and child directories

Using `-p`, `mkdir` automatically creates any missing parent directories instead of failing.

---

# ⚠️ Common Mistakes

❌ Creating nested directories without `-p`.

Incorrect:

```bash
mkdir project/docs/images
```

If `project` doesn't exist, the command fails.

Correct:

```bash
mkdir -p project/docs/images
```

---

❌ Trying to create an existing directory.

```text
mkdir: cannot create directory 'docs': File exists
```

Use:

```bash
mkdir -p docs
```

to avoid an error if the directory already exists.

---

❌ Using invalid characters in directory names.

Stick to descriptive names using letters, numbers, hyphens (`-`), and underscores (`_`) for portability.

---

# ✅ Best Practices

- Use meaningful directory names.
- Use `mkdir -p` when creating nested structures.
- Keep directory hierarchies organized and predictable.
- Avoid spaces in directory names when possible.

---

# 🔒 Security Considerations

Directory permissions determine who can access, modify, or enter a directory.

When creating directories for shared systems or production environments, ensure appropriate permissions are applied using `-m` or `chmod`.

---

# 🚀 Performance Notes

`mkdir` is a lightweight operation and executes almost instantly.

Creating deeply nested directory structures with `-p` adds minimal overhead and is efficient even for large hierarchies.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `cd` | Navigate into a directory |
| `ls` | List directory contents |
| `pwd` | Display current directory |
| `rmdir` | Remove empty directories |
| `rm -r` | Remove directories recursively |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `mkdir` | Creates directories |
| `touch` | Creates empty files |
| `rmdir` | Removes empty directories |
| `rm -r` | Removes directories and their contents |

---

# 🧪 Practice Exercises

### Beginner

Create a directory named `practice`.

---

### Intermediate

Create the following structure in a single command:

```text
projects/
└── nexora/
    └── docs/
```

---

### Advanced

Create a directory named `secure` with permissions `700`.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `mkdir` command?

**A:** It creates one or more directories in the filesystem.

---

### Intermediate

**Q:** What does the `-p` option do?

**A:** It creates parent directories as needed and prevents errors if directories already exist.

---

### Advanced

**Q:** Why is `mkdir -p` commonly used in automation scripts?

**A:** It safely creates directory structures without failing if some or all directories already exist, making scripts idempotent.

---

# 🛠 Troubleshooting

### Problem

```text
mkdir: cannot create directory 'logs': Permission denied
```

### Cause

You do not have permission to create directories in the current location.

### Solution

Check permissions:

```bash
ls -ld .
```

Or create the directory in a location where you have write access, or use `sudo` if appropriate.

---

# 📚 Official Documentation

- GNU Coreutils `mkdir` manual (`man mkdir`)
- POSIX `mkdir` specification

---

# 📖 Further Reading

- Nexora: `cd`
- Nexora: `touch`
- Nexora: `rm`
- Nexora: Linux File Permissions

---

# 💡 Did You Know?

The special entries `.` (current directory) and `..` (parent directory) are automatically created inside every new directory by the filesystem. These entries help Linux navigate the directory hierarchy efficiently.

---

# 📌 Quick Summary

- `mkdir` creates directories.
- Use `-p` to create nested directories.
- Use `-v` for verbose output.
- Use `-m` to set permissions during creation.
- Prefer meaningful, organized directory names.

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