# chown

> Change the ownership of files and directories in Linux by assigning a new user, group, or both.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Permissions |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`chown` (Change Owner) is used to change the owner and/or group associated with a file or directory. Ownership determines who has control over a file and works alongside Linux file permissions.

System administrators frequently use `chown` when managing users, deploying applications, configuring web servers, or transferring project ownership.

- **What does it do?** Changes the owner and/or group of files and directories.
- **Why does it exist?** To manage file ownership and ensure the correct users have control over resources.
- **When is it commonly used?** Setting ownership for websites, applications, user home directories, shared folders, and deployment files.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Change the owner of a file
- Change the group of a file
- Change both owner and group simultaneously
- Recursively change ownership
- Understand ownership in Linux

---

# ⚙️ Syntax

```bash
chown [options] owner[:group] file
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `owner` | New owner username | Yes |
| `group` | New group name (optional) | No |
| `file` | File or directory to modify | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-R` | Recursively change ownership |
| `-v` | Display every processed file |
| `-c` | Show only files whose ownership changed |
| `--reference=<file>` | Copy ownership from another file |
| `-h` | Affect symbolic links instead of their targets |

---

# 💻 Basic Examples

## Example 1

```bash
sudo chown alice file.txt
```

Change the owner of `file.txt` to **alice**.

---

## Example 2

```bash
sudo chown alice:developers project.txt
```

Change both owner and group.

---

## Example 3

```bash
sudo chown :developers project.txt
```

Change only the group.

---

## Example 4

```bash
sudo chown -R www-data:www-data /var/www/html
```

Recursively change ownership of a website directory.

---

## Example 5

```bash
sudo chown --reference=file1 file2
```

Copy ownership from `file1` to `file2`.

---

# 📤 Example Output

```text
$ ls -l report.txt
-rw-r--r-- 1 root root 2048 Jul 9 12:10 report.txt

$ sudo chown revanth report.txt

$ ls -l report.txt
-rw-r--r-- 1 revanth root 2048 Jul 9 12:10 report.txt
```

Explanation:

- The owner changed from **root** to **revanth**.
- The group remained unchanged.

---

# 🌍 Real-world Use Cases

- Changing ownership after copying files as `root`
- Configuring ownership for web server directories
- Assigning project files to development teams
- Restoring ownership after backups
- Managing shared directories

---

# 🧠 How It Works

Every Linux file has:

- An **owner**
- A **group**

When a file is accessed, Linux checks:

1. Owner permissions
2. Group permissions
3. Other (everyone else) permissions

`chown` modifies the ownership metadata stored by the filesystem. It does **not** change the file's contents.

---

# ⚠️ Common Mistakes

❌ Forgetting `sudo`.

Changing ownership usually requires administrative privileges.

---

❌ Confusing `chmod` with `chown`.

- `chmod` changes permissions.
- `chown` changes ownership.

---

❌ Recursively changing ownership of system directories.

Running:

```bash
sudo chown -R user /
```

can break the operating system.

---

# ✅ Best Practices

- Use recursive ownership changes carefully.
- Verify ownership with `ls -l`.
- Assign ownership based on the principle of least privilege.
- Use groups for shared project access instead of giving everyone ownership.

---

# 🔒 Security Considerations

Improper ownership can expose sensitive files or prevent services from functioning correctly.

For example, web server directories often require:

```bash
sudo chown -R www-data:www-data /var/www/html
```

Changing ownership of critical system files should only be done when necessary.

---

# 🚀 Performance Notes

Changing ownership of a single file is very fast.

Recursive operations (`-R`) may take time on directories containing thousands of files.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `chmod` | Change file permissions |
| `chgrp` | Change only the group |
| `ls` | Display ownership information |
| `stat` | Show detailed file metadata |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `chown` | Changes owner and group |
| `chgrp` | Changes only the group |
| `chmod` | Changes permissions |

---

# 🧪 Practice Exercises

### Beginner

Change the owner of a file to your user account.

---

### Intermediate

Assign a file to a different group without changing its owner.

---

### Advanced

Recursively change ownership of an entire project directory.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `chown` command do?

**A:** It changes the owner and/or group of files and directories.

---

### Intermediate

**Q:** What is the difference between `chmod` and `chown`?

**A:** `chmod` modifies permissions, while `chown` changes ownership.

---

### Advanced

**Q:** Why is changing ownership important for web servers?

**A:** Services like Apache or Nginx need the correct ownership to securely access website files without granting unnecessary permissions.

---

# 🛠 Troubleshooting

**Problem:** `Operation not permitted`

**Cause:**

The current user lacks permission to change ownership.

**Solution:**

Run the command with `sudo`.

---

**Problem:** Service cannot access its files.

**Cause:**

Incorrect ownership.

**Solution:**

Verify ownership using:

```bash
ls -l
```

Then assign the correct owner using `chown`.

---

# 📚 Official Documentation

- `man chown`
- https://www.gnu.org/software/coreutils/manual/html_node/chown-invocation.html

---

# 📖 Further Reading

- Nexora: `chmod`
- Nexora: `ls`
- Nexora: Linux File Permissions
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `chown` changes file and directory ownership.
- Supports changing owner, group, or both.
- Requires administrative privileges in most cases.
- Commonly used for web servers, shared projects, and system administration.
- Works alongside `chmod` to manage Linux file security.

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