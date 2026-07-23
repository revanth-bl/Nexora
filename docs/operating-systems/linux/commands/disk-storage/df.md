# df

> Display disk space usage for mounted file systems.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Disk Storage |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 6 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`df` (Disk Free) is a Linux command used to display information about the available and used disk space on mounted file systems. It helps administrators monitor storage usage and identify partitions that are running out of space.

`df` reports usage at the **filesystem level**, making it different from the `du` command, which reports usage for individual files and directories.

- **What does it do?** Displays disk space usage for mounted file systems.
- **Why does it exist?** To monitor available storage and filesystem capacity.
- **When is it commonly used?** Checking disk usage, troubleshooting storage issues, and monitoring servers.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display filesystem usage
- Read disk usage statistics
- Show human-readable sizes
- Display filesystem types
- Check specific partitions

---

# ⚙️ Syntax

```bash
df [OPTIONS] [FILE...]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `FILE` | Display information for the filesystem containing the file | No |

---

# 🔧 Common Options

| Option | Description |
|---------|-------------|
| `-h` | Human-readable sizes (KB, MB, GB) |
| `-H` | Human-readable using powers of 1000 |
| `-T` | Display filesystem type |
| `-i` | Show inode usage instead of block usage |
| `-a` | Include all file systems |
| `--total` | Display a grand total |
| `--help` | Show help information |

---

# 💻 Basic Examples

## Example 1

Display disk usage.

```bash
df
```

---

## Example 2

Display human-readable sizes.

```bash
df -h
```

---

## Example 3

Show filesystem types.

```bash
df -T
```

---

## Example 4

Display inode usage.

```bash
df -i
```

---

## Example 5

Check a specific filesystem.

```bash
df -h /home
```

---

# 📤 Example Output

```text
$ df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   18G   30G  38% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
/dev/sdb1       500G  320G  180G  65% /data
```

---

# 🌍 Real-world Use Cases

- Checking available disk space
- Monitoring server storage
- Identifying nearly full partitions
- Troubleshooting "No space left on device" errors
- Monitoring cloud virtual machines

---

# 🧠 How It Works

`df` reads filesystem metadata maintained by the operating system and reports:

- Total space
- Used space
- Available space
- Usage percentage
- Mount point

```text
Filesystem
     │
     ▼
    df
     │
     ▼
Disk Usage Report
```

---

# ⚠️ Common Mistakes

❌ Confusing `df` with `du`.

```bash
df
```

shows filesystem usage.

```bash
du
```

shows directory or file usage.

---

❌ Forgetting the `-h` option.

Without it:

```text
20971520
```

With it:

```text
20G
```

---

❌ Ignoring inode usage.

Sometimes disk space is available, but all inodes are consumed.

Check with:

```bash
df -i
```

---

# ✅ Best Practices

- Use `df -h` for readability.
- Regularly monitor server storage.
- Check inode usage on systems with many small files.
- Investigate partitions above 80–90% utilization.

---

# 🔒 Security Considerations

Monitoring disk usage helps prevent:

- Application failures due to full disks
- Log files consuming all available storage
- Denial-of-service issues caused by exhausted storage

Restrict access to sensitive mount points where appropriate.

---

# 🚀 Performance Notes

`df` is very fast because it retrieves filesystem statistics directly from the kernel rather than scanning every file.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `du` | Display directory and file usage |
| `lsblk` | List block devices |
| `mount` | Display mounted filesystems |
| `fdisk` | Manage disk partitions |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `df` | Shows filesystem usage |
| `du` | Shows directory/file usage |
| `lsblk` | Displays storage devices |
| `mount` | Displays mounted filesystems |

---

# 🧪 Practice Exercises

### Beginner

Display disk usage in human-readable format.

---

### Intermediate

Display the filesystem type for every mounted partition.

---

### Advanced

Check both disk space and inode usage, then identify any partitions that may require cleanup.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `df` command do?

**A:** It displays the available and used disk space for mounted file systems.

---

### Intermediate

**Q:** What is the purpose of the `-h` option?

**A:** It displays file sizes in a human-readable format such as KB, MB, and GB.

---

### Advanced

**Q:** What is the difference between `df` and `du`?

**A:**

- `df` reports disk usage at the filesystem level.
- `du` reports disk usage for individual files and directories.

---

# 🛠 Troubleshooting

**Problem:** A filesystem reports 100% usage.

**Solution:**

Use:

```bash
df -h
```

to identify the affected filesystem, then use:

```bash
du -sh /*
```

to locate large directories consuming space.

---

**Problem:** Disk appears to have free space, but files cannot be created.

**Solution:**

Check inode usage:

```bash
df -i
```

A filesystem with exhausted inodes cannot create new files even if storage space remains.

---

# 📚 Official Documentation

- `man df`
- GNU Coreutils Manual (`df`)

---

# 📖 Further Reading

- Nexora: `du`
- Nexora: `lsblk`
- Nexora: `mount`
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `df` displays filesystem disk usage.
- Use `-h` for human-readable output.
- Use `-T` to show filesystem types.
- Use `-i` to monitor inode usage.
- Essential for monitoring Linux storage and troubleshooting disk space issues.

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