# mv

> Moves or renames files and directories within the Linux filesystem.

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

The `mv` (Move) command is used to move files or directories from one location to another. It is also used to rename files and directories.

Unlike `cp`, which creates a copy, `mv` relocates the original item.

- **What does it do?** Moves or renames files and directories.
- **Why does it exist?** To organize files and change their names without creating duplicates.
- **When is it commonly used?** Organizing projects, renaming files, moving data between directories, and deployment tasks.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Move files between directories
- Rename files and directories
- Move multiple files at once
- Use common `mv` options safely
- Avoid accidental overwrites

---

# ⚙️ Syntax

```bash
mv [OPTIONS] SOURCE DESTINATION
```

or

```bash
mv [OPTIONS] SOURCE... DIRECTORY
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `SOURCE` | File or directory to move | Yes |
| `DESTINATION` | New name or target directory | Yes |

---

# 🔧 Common Options

| Option | Description |
|---------|-------------|
| `-i` | Ask before overwriting existing files |
| `-f` | Force overwrite without prompting |
| `-n` | Never overwrite existing files |
| `-v` | Display each move operation |

---

# 💻 Basic Examples

## Example 1

Rename a file.

```bash
mv notes.txt notes-old.txt
```

---

## Example 2

Move a file into another directory.

```bash
mv report.pdf Documents/
```

---

## Example 3

Move multiple files.

```bash
mv file1.txt file2.txt archive/
```

---

## Example 4

Rename a directory.

```bash
mv project project-backup
```

---

## Example 5

Display each move operation.

```bash
mv -v image.png Pictures/
```

Example output:

```text
renamed 'image.png' -> 'Pictures/image.png'
```

---

# 📤 Example Output

```text
$ ls

notes.txt

$ mv notes.txt archive/

$ ls archive

notes.txt
```

---

# 🌍 Real-world Use Cases

- Organizing project files into folders.
- Renaming configuration files.
- Moving application logs into backup directories.
- Deploying build artifacts.
- Cleaning up download folders.

---

# 🧠 How It Works

When moving files within the same filesystem, `mv` simply updates directory entries instead of copying data, making the operation very fast.

If the destination is on a different filesystem or partition, the system copies the data and removes the original file after the copy succeeds.

---

# ⚠️ Common Mistakes

❌ Accidentally overwriting an existing file.

```bash
mv report.txt backup/
```

If `backup/report.txt` already exists, it may be replaced.

Safer:

```bash
mv -i report.txt backup/
```

---

❌ Forgetting the destination directory.

```bash
mv report.txt
```

This produces an error because both source and destination are required.

---

❌ Confusing moving with copying.

Remember:

- `cp` creates a duplicate.
- `mv` relocates the original.

---

# ✅ Best Practices

- Use `-i` when working with important files.
- Use `-v` in scripts for easier debugging.
- Verify the destination before moving large datasets.
- Keep filenames descriptive and consistent.

---

# 🔒 Security Considerations

Moving files into protected directories may require elevated permissions.

Be cautious when using `mv` with `sudo`, as overwriting system files can cause unexpected behavior.

---

# 🚀 Performance Notes

Moving files within the same filesystem is nearly instantaneous because only filesystem metadata is updated.

Moving across different filesystems takes longer because the data must be copied before the original is removed.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `cp` | Copies files instead of moving them |
| `rm` | Deletes files |
| `mkdir` | Creates directories |
| `ls` | Lists directory contents |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `mv` | Moves or renames files |
| `cp` | Creates a copy |
| `rename` | Renames multiple files using patterns |

---

# 🧪 Practice Exercises

### Beginner

Rename `notes.txt` to `notes-old.txt`.

---

### Intermediate

Move all `.log` files into a directory named `logs`.

---

### Advanced

Move an entire project directory into `/opt/projects` while displaying each operation.

---

# 💼 Real Interview Questions

### Beginner

**Q:** Can `mv` rename a file?

**A:** Yes. If the destination is a new filename instead of a directory, `mv` renames the file.

---

### Intermediate

**Q:** What happens if the destination file already exists?

**A:** By default, it may be overwritten (depending on system settings). Use `-i` to prompt before replacing it.

---

### Advanced

**Q:** Why is moving a file within the same filesystem usually faster than copying it?

**A:** Because only filesystem metadata is updated. The file's data blocks remain in place, making the operation almost instantaneous.

---

# 🛠 Troubleshooting

### Problem

```text
mv: cannot move 'file.txt': Permission denied
```

### Cause

You do not have permission to write to the destination directory or modify the source.

### Solution

Check permissions:

```bash
ls -ld destination/
```

Use `sudo` only if appropriate.

---

# 📚 Official Documentation

- GNU Coreutils `mv` manual (`man mv`)
- POSIX `mv` specification

---

# 📖 Further Reading

- Nexora: `cp`
- Nexora: `rm`
- Nexora: `mkdir`
- Nexora: Linux File Permissions

---

# 💡 Did You Know?

Unlike graphical file managers, `mv` does not send files to a recycle bin or trash. Once a file is overwritten or removed as part of a move operation, recovering it can be difficult without backups.

---

# 📌 Quick Summary

- `mv` moves or renames files and directories.
- Use `-i` to prevent accidental overwrites.
- Use `-v` for verbose output.
- Moving within the same filesystem is extremely fast.
- `mv` changes the original file—it does not create a copy.

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