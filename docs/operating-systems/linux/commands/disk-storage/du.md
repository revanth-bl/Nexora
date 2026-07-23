# du

> Estimate and display disk space used by files and directories.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Disk Storage |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`du` (Disk Usage) is a Linux command used to estimate and display the amount of disk space occupied by files and directories. Unlike `df`, which reports usage for entire file systems, `du` provides detailed usage information for individual directories and files.

It is commonly used to identify large directories, troubleshoot low disk space, and analyze storage consumption.

- **What does it do?** Displays disk usage for files and directories.
- **Why does it exist?** To help users locate where disk space is being used.
- **When is it commonly used?** Finding large files, cleaning up storage, and monitoring disk usage.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display directory sizes
- Show human-readable output
- Summarize directory usage
- Find the largest directories
- Compare `du` with `df`

---

# ⚙️ Syntax

```bash
du [OPTIONS] [FILE...]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `FILE` | File or directory to analyze | No |

If no file or directory is specified, `du` analyzes the current directory.

---

# 🔧 Common Options

| Option | Description |
|---------|-------------|
| `-h` | Human-readable sizes (KB, MB, GB) |
| `-s` | Display only the total size of each argument |
| `-a` | Include individual files in the output |
| `-c` | Display a grand total |
| `--max-depth=N` | Limit directory traversal depth |
| `-x` | Stay on one filesystem |
| `--help` | Show help information |

---

# 💻 Basic Examples

## Example 1

Display disk usage for the current directory.

```bash
du
```

---

## Example 2

Display human-readable sizes.

```bash
du -h
```

---

## Example 3

Display only the total size of a directory.

```bash
du -sh Downloads
```

---

## Example 4

Display sizes up to one directory level.

```bash
du -h --max-depth=1
```

---

## Example 5

Find the largest directories.

```bash
du -h --max-depth=1 | sort -hr
```

---

## Example 6

Display disk usage for all files.

```bash
du -ah
```

---

# 📤 Example Output

```text
$ du -h --max-depth=1

4.0K    ./scripts
28M     ./images
120M    ./videos
152M    .
```

---

# 🌍 Real-world Use Cases

- Finding large directories
- Cleaning up storage
- Monitoring project size
- Checking backup sizes
- Troubleshooting low disk space
- Analyzing log file growth

---

# 🧠 How It Works

`du` recursively scans files and directories, calculates their disk usage, and reports the results.

```text
Directory
     │
     ▼
     du
     │
     ▼
Usage Report
```

Unlike `df`, `du` reads the filesystem to calculate the size of files and directories.

---

# ⚠️ Common Mistakes

❌ Confusing `du` with `df`.

```bash
du
```

shows directory and file usage.

```bash
df
```

shows filesystem usage.

---

❌ Forgetting the `-h` option.

Without it:

```text
157286400
```

With it:

```text
150M
```

---

❌ Running `du` on the root directory without limiting depth.

```bash
du -h /
```

This may take a long time.

Instead:

```bash
du -h --max-depth=1 /
```

---

# ✅ Best Practices

- Use `du -sh` to quickly check directory size.
- Combine `du` with `sort` to identify the largest directories.
- Limit recursion depth when analyzing large filesystems.
- Use `-x` to avoid crossing mounted filesystems.

---

# 🔒 Security Considerations

Scanning directories may require elevated permissions.

Use:

```bash
sudo du -sh /var/log
```

only when necessary.

Avoid exposing sensitive directory structures on shared systems.

---

# 🚀 Performance Notes

`du` scans the filesystem recursively, so performance depends on:

- Number of files
- Directory depth
- Storage device speed

Large filesystems may take noticeable time to analyze.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `df` | Display filesystem usage |
| `find` | Locate files |
| `lsblk` | List block devices |
| `ncdu` | Interactive disk usage analyzer |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `du` | Shows directory and file usage |
| `df` | Shows filesystem usage |
| `find` | Searches for files |
| `ncdu` | Interactive disk usage viewer |

---

# 🧪 Practice Exercises

### Beginner

Display the size of your home directory.

---

### Intermediate

List the sizes of all first-level directories in `/var`.

---

### Advanced

Find the five largest directories in your home folder using `du` and `sort`.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `du` command do?

**A:** It estimates and displays the disk space used by files and directories.

---

### Intermediate

**Q:** How do you display only the total size of a directory in a human-readable format?

**A:**

```bash
du -sh directory_name
```

---

### Advanced

**Q:** What is the difference between `du` and `df`?

**A:**

- `du` calculates the space used by files and directories.
- `df` reports available and used space for mounted file systems.

---

# 🛠 Troubleshooting

**Problem:** `du` takes too long to finish.

**Solution:**

Limit the directory depth:

```bash
du -h --max-depth=1
```

or analyze a smaller directory.

---

**Problem:** "Permission denied" messages appear.

**Solution:**

Run with appropriate privileges:

```bash
sudo du -sh /directory
```

Only use `sudo` when necessary.

---

# 📚 Official Documentation

- `man du`
- GNU Coreutils Manual (`du`)

---

# 📖 Further Reading

- Nexora: `df`
- Nexora: `find`
- Nexora: `lsblk`
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `du` displays disk usage for files and directories.
- Use `-h` for human-readable output.
- Use `-s` to display only the total size.
- Combine with `sort` to identify large directories.
- Essential for analyzing storage usage and troubleshooting disk space issues.

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