# rsync

> Efficiently synchronize files and directories between local and remote systems.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`rsync` (Remote Sync) is a fast and efficient utility for copying and synchronizing files and directories. It transfers only the differences between the source and destination, making it significantly faster than repeatedly copying entire files.

It works locally as well as over SSH, making it one of the most widely used tools for backups, deployments, and file synchronization.

- **What does it do?** Synchronizes files and directories efficiently.
- **Why does it exist?** To minimize data transfer and speed up file copying.
- **When is it commonly used?** Backups, deployments, migrations, and remote file synchronization.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Synchronize files locally
- Synchronize files over SSH
- Preserve permissions and timestamps
- Delete files that no longer exist in the source
- Perform dry-run operations before syncing

---

# ⚙️ Syntax

```bash
rsync [options] source destination
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `source` | Source file or directory | Yes |
| `destination` | Destination file or directory | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-a` | Archive mode (preserves permissions, timestamps, links, ownership, etc.) |
| `-v` | Verbose output |
| `-h` | Human-readable numbers |
| `-z` | Compress data during transfer |
| `-P` | Show progress and allow resume |
| `--delete` | Delete files not present in the source |
| `--dry-run` | Show what would happen without making changes |
| `-e ssh` | Transfer files over SSH |

---

# 💻 Basic Examples

## Example 1

```bash
rsync -av source/ backup/
```

Synchronizes one local directory to another.

---

## Example 2

```bash
rsync -avz project/ user@server:/var/www/project/
```

Synchronizes a local project to a remote server using SSH.

---

## Example 3

```bash
rsync -av --delete source/ backup/
```

Makes the destination an exact copy by deleting extra files.

---

## Example 4

```bash
rsync -av --dry-run source/ backup/
```

Shows what changes would occur without actually copying files.

---

## Example 5

```bash
rsync -avP largefile.iso user@server:/backup/
```

Copies a large file with progress information and resume capability.

---

# 📤 Example Output

```text
sending incremental file list

index.html
style.css
images/logo.png

sent 2.31M bytes
received 120 bytes
total size is 15.8M
speedup is 6.78
```

Explanation:

- **sending incremental file list** → Only changed files are transferred.
- **sent/received** → Network traffic statistics.
- **speedup** → Efficiency gained by transferring only differences.

---

# 🌍 Real-world Use Cases

- Daily server backups
- Website deployments
- Synchronizing development environments
- Migrating files between servers
- Copying large datasets efficiently

---

# 🧠 How It Works

Unlike traditional copy commands, `rsync` compares the source and destination.

It transfers only changed blocks of data using its delta-transfer algorithm, reducing bandwidth usage and speeding up synchronization.

When used with SSH, all transferred data is encrypted.

---

# ⚠️ Common Mistakes

❌ Forgetting the trailing slash.

```bash
rsync source destination
```

copies the directory itself.

```bash
rsync source/ destination
```

copies only its contents.

---

❌ Using `--delete` without checking first.

This can permanently remove files from the destination.

Always perform a dry run first.

---

❌ Running as root unnecessarily.

This may overwrite ownership and permissions unintentionally.

---

# ✅ Best Practices

- Use `-a` for most synchronization tasks.
- Combine `-a`, `-v`, and `-h` for readable output.
- Run `--dry-run` before large operations.
- Use SSH for secure remote transfers.
- Verify backups after synchronization.

---

# 🔒 Security Considerations

When syncing over a network, prefer SSH:

```bash
rsync -avz -e ssh source/ user@server:/backup/
```

Avoid exposing rsync daemons directly to the internet unless properly secured.

Never synchronize sensitive data to untrusted systems.

---

# 🚀 Performance Notes

`rsync` is highly efficient because it transfers only modified data.

Compression (`-z`) reduces bandwidth usage but increases CPU usage.

For local transfers on fast storage, compression usually provides little benefit.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `scp` | Secure file copying without synchronization |
| `ssh` | Secure remote login used by rsync |
| `cp` | Local file copying |
| `tar` | Archive files before synchronization |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `cp` | Copies everything every time |
| `scp` | Secure copy without delta synchronization |
| `rsync` | Transfers only changed data |

---

# 🧪 Practice Exercises

### Beginner

Synchronize one directory to another on the same machine.

---

### Intermediate

Synchronize a project to a remote server using SSH.

---

### Advanced

Perform a dry run with `--delete`, verify the changes, then execute the synchronization.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of `rsync`?

**A:** To efficiently synchronize files and directories by transferring only changed data.

---

### Intermediate

**Q:** Why is `rsync` faster than `scp` for repeated transfers?

**A:** Because `rsync` transfers only the differences between the source and destination instead of copying everything again.

---

### Advanced

**Q:** What is the importance of the trailing slash (`/`) in an `rsync` source path?

**A:** A trailing slash copies the contents of the directory, while omitting it copies the directory itself.

---

# 🛠 Troubleshooting

**Problem:** Permission denied.

**Cause:** Insufficient permissions or incorrect SSH configuration.

**Solution:**

- Verify file permissions.
- Ensure SSH access works.
- Check destination ownership.

---

**Problem:** Files unexpectedly deleted.

**Cause:** Using `--delete`.

**Solution:**

Always perform:

```bash
rsync --dry-run
```

before using `--delete`.

---

# 📚 Official Documentation

- `man rsync`
- https://rsync.samba.org/

---

# 📖 Further Reading

- Nexora: `scp`
- Nexora: `ssh`
- Nexora: `tar`
- Linux Backup Strategies

---

# 📌 Quick Summary

- `rsync` synchronizes files efficiently.
- Transfers only changed data.
- Supports local and remote synchronization.
- Works securely over SSH.
- Always use `--dry-run` before `--delete`.

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