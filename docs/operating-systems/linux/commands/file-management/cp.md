# cp

> Copies files and directories from one location to another without removing the original.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | File Management |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 6 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

The `cp` (copy) command creates a duplicate of a file or directory at another location.

Unlike `mv`, which moves data, `cp` leaves the original intact and creates a new copy.

- **What does it do?** Copies files and directories.
- **Why does it exist?** Allows safe duplication of data without affecting the original.
- **When is it commonly used?** Creating backups, duplicating configuration files, copying project folders, and preparing deployment artifacts.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Copy files
- Copy directories
- Preserve file metadata
- Copy recursively
- Avoid accidental overwrites

---

# ⚙️ Syntax

```bash
cp [OPTIONS] SOURCE DESTINATION
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `SOURCE` | File or directory to copy | Yes |
| `DESTINATION` | Destination path | Yes |

---

# 🔧 Common Options

| Option | Description |
|---------|-------------|
| `-r` or `-R` | Copy directories recursively |
| `-a` | Archive mode (preserves permissions, timestamps, symbolic links, etc.) |
| `-i` | Prompt before overwriting existing files |
| `-u` | Copy only when the source is newer |
| `-v` | Show each copied file (verbose output) |
| `-p` | Preserve timestamps, ownership, and permissions |

---

# 💻 Basic Examples

## Example 1

Copy a file.

```bash
cp file.txt backup.txt
```

---

## Example 2

Copy a file into another directory.

```bash
cp notes.txt Documents/
```

---

## Example 3

Copy an entire directory.

```bash
cp -r project backup/
```

---

## Example 4

Preserve metadata.

```bash
cp -a project project-backup
```

---

## Example 5

Ask before overwriting.

```bash
cp -i config.conf backup/
```

---

# 📤 Example Output

```text
$ cp -v notes.txt backup/

'notes.txt' -> 'backup/notes.txt'
```

---

# 🌍 Real-world Use Cases

- Backing up configuration files before editing.
- Copying application files during deployment.
- Duplicating project directories.
- Creating backup snapshots before upgrades.

---

# 🧠 How It Works

`cp` reads the source file and writes a duplicate to the destination.

When copying directories, the `-r` (recursive) option traverses every subdirectory and file until the complete structure has been duplicated.

---

# ⚠️ Common Mistakes

❌ Forgetting `-r` when copying directories.

```bash
cp project backup/
```

Error:

```text
cp: -r not specified; omitting directory
```

Correct:

```bash
cp -r project backup/
```

---

❌ Accidentally overwriting files.

Use:

```bash
cp -i
```

to receive a confirmation prompt.

---

❌ Losing file metadata.

Use:

```bash
cp -a
```

when creating backups.

---

# ✅ Best Practices

- Use `cp -a` for backups.
- Use `cp -i` when copying important files.
- Verify the destination before copying.
- Use verbose mode (`-v`) when copying many files.

---

# 🔒 Security Considerations

Copying sensitive files also copies their contents.

Be careful when copying:

- SSH keys
- Password files
- Certificates
- Environment files (`.env`)

Always verify file permissions after copying.

---

# 🚀 Performance Notes

Copying large directories may take significant time depending on:

- File size
- Number of files
- Storage speed
- Filesystem type

Using SSDs greatly improves copy performance.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `mv` | Moves files instead of copying |
| `rm` | Deletes files |
| `rsync` | Efficient synchronization between locations |
| `tar` | Archives files before copying |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `cp` | Creates a duplicate |
| `mv` | Moves the original |
| `rsync` | Synchronizes only changed data |

---

# 🧪 Practice Exercises

### Beginner

Copy a file named `notes.txt` to `backup.txt`.

---

### Intermediate

Copy an entire project directory recursively.

---

### Advanced

Create a backup of a project while preserving permissions, timestamps, and symbolic links.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `cp` command?

**A:** It copies files or directories to another location without removing the original.

---

### Intermediate

**Q:** Why is `cp -r` required for directories?

**A:** Because directories contain nested files and folders that must be copied recursively.

---

### Advanced

**Q:** What is the difference between `cp -r` and `cp -a`?

**A:** `cp -r` copies directories recursively, while `cp -a` also preserves permissions, ownership, timestamps, symbolic links, and other metadata, making it ideal for backups.

---

# 🛠 Troubleshooting

### Problem

```text
cp: cannot stat 'file.txt': No such file or directory
```

### Cause

The source file does not exist or the path is incorrect.

### Solution

Verify the path:

```bash
pwd
ls
```

---

# 📚 Official Documentation

- GNU Coreutils `cp` manual (`man cp`)
- POSIX `cp` specification

---

# 📖 Further Reading

- Nexora: `mv`
- Nexora: `rm`
- Nexora: `rsync`

---

# 💡 Did You Know?

Unlike `mv`, which usually renames or relocates files within the same filesystem, `cp` always creates a new copy of the data. This means copying a large file can take significantly longer than moving it on the same disk.

---

# 📌 Quick Summary

- `cp` copies files and directories.
- Use `-r` for directories.
- Use `-a` for backups.
- Use `-i` to prevent accidental overwrites.
- Use `-v` to see what is being copied.

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