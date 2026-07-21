# chmod

> Change file and directory permissions in Linux to control who can read, write, or execute them.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Permissions |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`chmod` (Change Mode) is used to modify the permissions of files and directories in Linux. Permissions determine who can read, write, or execute a file.

Proper permission management is essential for system security and is one of the first concepts every Linux administrator should master.

- **What does it do?** Changes file and directory permissions.
- **Why does it exist?** To control access and protect files from unauthorized users.
- **When is it commonly used?** Making scripts executable, securing sensitive files, configuring web servers, and managing shared directories.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Understand Linux file permissions
- Modify permissions using symbolic mode
- Modify permissions using numeric (octal) mode
- Secure files and directories
- Avoid common permission mistakes

---

# ⚙️ Syntax

```bash
chmod [options] mode file
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `mode` | Permission settings (symbolic or numeric) | Yes |
| `file` | File or directory to modify | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-R` | Apply permissions recursively to directories and their contents |
| `-v` | Display every file processed |
| `-c` | Display only files whose permissions changed |
| `--reference=<file>` | Copy permissions from another file |

---

# 💻 Basic Examples

## Example 1

```bash
chmod +x script.sh
```

Make a script executable.

---

## Example 2

```bash
chmod 755 script.sh
```

Owner has full access; others can read and execute.

---

## Example 3

```bash
chmod 644 notes.txt
```

Owner can read and write; everyone else can only read.

---

## Example 4

```bash
chmod -R 755 website/
```

Recursively apply permissions to an entire directory.

---

## Example 5

```bash
chmod go-r secret.txt
```

Remove read permission for group and others.

---

# 📤 Example Output

```text
$ ls -l script.sh
-rw-r--r-- 1 revanth revanth 1350 Jul 9 10:22 script.sh

$ chmod +x script.sh

$ ls -l script.sh
-rwxr-xr-x 1 revanth revanth 1350 Jul 9 10:22 script.sh
```

Explanation:

- `r` → Read permission
- `w` → Write permission
- `x` → Execute permission
- `-` → Permission not granted

---

# 🌍 Real-world Use Cases

- Making shell scripts executable
- Securing SSH private keys
- Configuring web server directories
- Restricting access to sensitive configuration files
- Preparing deployment scripts

---

# 🧠 How It Works

Linux stores permissions as metadata associated with each file and directory.

Permissions are divided into three categories:

- **Owner (u)**
- **Group (g)**
- **Others (o)**

Each category can have:

- Read (`r`) = 4
- Write (`w`) = 2
- Execute (`x`) = 1

Numeric permissions are calculated by adding these values.

Example:

```text
755

Owner  = 7 = rwx
Group  = 5 = r-x
Others = 5 = r-x
```

---

# ⚠️ Common Mistakes

❌ Using `777` on everything.

This grants everyone full access and creates serious security risks.

---

❌ Forgetting execute permission on scripts.

Without execute permission, scripts cannot be run directly.

---

❌ Using recursive permission changes carelessly.

Running:

```bash
chmod -R 777 /
```

would be catastrophic on a production system.

---

# ✅ Best Practices

- Follow the principle of least privilege.
- Use `644` for regular files unless execute permission is required.
- Use `755` for executable scripts and most directories.
- Protect sensitive files with restrictive permissions such as `600`.
- Verify permissions using `ls -l`.

---

# 🔒 Security Considerations

Incorrect permissions are one of the most common Linux security issues.

Examples:

- SSH private keys should be:

```bash
chmod 600 ~/.ssh/id_ed25519
```

- SSH directory:

```bash
chmod 700 ~/.ssh
```

Avoid world-writable (`777`) permissions unless absolutely necessary.

---

# 🚀 Performance Notes

Changing permissions is a lightweight filesystem operation.

Recursive changes (`chmod -R`) can take noticeable time on directories containing thousands of files.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `chown` | Change file ownership |
| `umask` | Set default permissions for new files |
| `ls` | Display current permissions |
| `stat` | Display detailed file metadata |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `chmod` | Changes permissions |
| `chown` | Changes owner and group |
| `umask` | Sets default permissions for new files |

---

# 🧪 Practice Exercises

### Beginner

Make a script executable.

---

### Intermediate

Change a file's permissions to `640`.

---

### Advanced

Recursively assign `755` permissions to a project directory while understanding its security implications.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does `chmod` do?

**A:** It changes file and directory permissions.

---

### Intermediate

**Q:** What does permission `755` mean?

**A:** The owner has read, write, and execute permissions, while the group and others have read and execute permissions only.

---

### Advanced

**Q:** Why is using `chmod 777` generally discouraged?

**A:** It grants full access to everyone, increasing the risk of unauthorized modification or execution of files.

---

# 🛠 Troubleshooting

**Problem:** `Permission denied` when executing a script.

**Cause:**

The execute permission is missing.

**Solution:**

```bash
chmod +x script.sh
```

---

**Problem:** SSH reports insecure private key permissions.

**Cause:**

The private key is accessible by other users.

**Solution:**

```bash
chmod 600 ~/.ssh/id_ed25519
```

---

# 📚 Official Documentation

- `man chmod`
- https://www.gnu.org/software/coreutils/manual/html_node/chmod-invocation.html

---

# 📖 Further Reading

- Nexora: `chown`
- Nexora: `ls`
- Nexora: Linux File Permissions
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `chmod` changes file and directory permissions.
- Supports symbolic (`+x`, `u+r`) and numeric (`755`, `644`) modes.
- Use restrictive permissions whenever possible.
- Avoid `777` except in rare, controlled situations.
- Essential for Linux security and administration.

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