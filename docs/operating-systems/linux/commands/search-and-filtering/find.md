# find

> Search for files and directories based on name, type, size, permissions, ownership, timestamps, and many other attributes.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Search and Filtering |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 10 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`find` is one of the most powerful file-searching utilities in Linux. Unlike `ls`, which simply lists directory contents, `find` recursively searches directories and allows you to filter files using dozens of criteria such as name, type, size, ownership, permissions, and modification time.

It can also execute commands on matching files, making it an essential tool for system administration and automation.

- **What does it do?** Searches for files and directories matching specified criteria.
- **Why does it exist?** To efficiently locate and process files across the filesystem.
- **When is it commonly used?** Finding configuration files, cleaning old logs, locating large files, auditing permissions, and scripting.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Search for files by name
- Filter by file type and size
- Search by ownership and permissions
- Find recently modified files
- Execute commands on search results

---

# ⚙️ Syntax

```bash
find [path] [expression]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `path` | Directory where the search begins | No (defaults to current directory) |
| `expression` | Search conditions and actions | No |

---

# 🔧 Options / Expressions

| Option | Description |
|---------|-------------|
| `-name` | Search by exact filename (case-sensitive) |
| `-iname` | Search by filename (case-insensitive) |
| `-type` | Search by file type (`f`, `d`, `l`, etc.) |
| `-size` | Search by file size |
| `-user` | Search by file owner |
| `-group` | Search by group owner |
| `-mtime` | Search by modification time |
| `-perm` | Search by file permissions |
| `-exec` | Execute a command on matching files |
| `-delete` | Delete matching files |

---

# 💻 Basic Examples

## Example 1

```bash
find . -name "*.txt"
```

Find all `.txt` files in the current directory and its subdirectories.

---

## Example 2

```bash
find /etc -type f
```

Find all regular files inside `/etc`.

---

## Example 3

```bash
find . -size +100M
```

Find files larger than 100 MB.

---

## Example 4

```bash
find . -mtime -7
```

Find files modified within the last 7 days.

---

## Example 5

```bash
find . -name "*.log" -delete
```

Delete all `.log` files.

---

## Example 6

```bash
find . -name "*.sh" -exec chmod +x {} \;
```

Make every shell script executable.

---

# 📤 Example Output

```text
$ find . -name "*.conf"

./nginx/nginx.conf
./apache/httpd.conf
./app/config.conf
```

Each matching path is printed on its own line.

---

# 🌍 Real-world Use Cases

- Locate configuration files
- Delete temporary or log files
- Find recently modified documents
- Audit world-writable files
- Execute commands on multiple files

---

# 🧠 How It Works

`find` starts at the specified directory and recursively walks the filesystem.

For each file or directory, it evaluates the search expressions. If all conditions match, the file is printed or processed.

Unlike `locate`, `find` searches the live filesystem, so its results are always up to date.

---

# ⚠️ Common Mistakes

❌ Forgetting quotes around wildcards.

Incorrect:

```bash
find . -name *.txt
```

Correct:

```bash
find . -name "*.txt"
```

---

❌ Using `-delete` without testing first.

Always verify matches before deleting files.

---

❌ Searching from the filesystem root unnecessarily.

Searching from `/` can be slow and may generate many permission errors.

---

# ✅ Best Practices

- Start searching from the smallest relevant directory.
- Test searches before using `-delete`.
- Combine multiple search conditions for precision.
- Use `-exec` carefully, especially with destructive commands.

---

# 🔒 Security Considerations

Running `find` with `sudo` may expose or modify sensitive system files.

Review search results before performing actions like `-delete` or `-exec rm`.

---

# 🚀 Performance Notes

Searching large filesystems can be time-consuming because `find` examines every file and directory.

Limit the search scope whenever possible for better performance.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `locate` | Fast indexed file search |
| `grep` | Search inside file contents |
| `ls` | List directory contents |
| `xargs` | Process search results efficiently |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `find` | Searches the live filesystem |
| `locate` | Searches an indexed database (much faster) |
| `grep` | Searches file contents, not filenames |

---

# 🧪 Practice Exercises

### Beginner

Find all `.txt` files in your home directory.

---

### Intermediate

Find directories named `backup`.

---

### Advanced

Find all files larger than 500 MB and modified within the last 30 days.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `find` command?

**A:** It searches for files and directories using various criteria such as name, size, permissions, and timestamps.

---

### Intermediate

**Q:** What is the difference between `find` and `locate`?

**A:** `find` searches the live filesystem, while `locate` searches a prebuilt index, making it much faster but potentially outdated.

---

### Advanced

**Q:** Why should you be cautious when using `find -delete`?

**A:** Because it permanently removes matching files. It's best to verify the search results before adding the `-delete` action.

---

# 🛠 Troubleshooting

**Problem:** `Permission denied`

**Cause:**

Some directories cannot be accessed by the current user.

**Solution:**

Use:

```bash
sudo find ...
```

if appropriate, or suppress errors:

```bash
find . 2>/dev/null
```

---

# 📚 Official Documentation

- `man find`
- GNU Findutils Documentation

---

# 📖 Further Reading

- Nexora: `locate`
- Nexora: `grep`
- Nexora: `xargs`
- GNU Findutils Manual

---

# 📌 Quick Summary

- `find` searches files and directories recursively.
- Supports filtering by name, type, size, owner, permissions, and time.
- Can execute commands on matching files.
- Always verify results before using destructive actions like `-delete`.
- One of the most powerful Linux command-line utilities.

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