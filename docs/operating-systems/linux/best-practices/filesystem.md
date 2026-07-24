# Filesystem Best Practices

## Overview

The Linux filesystem stores and organizes data in a hierarchical directory structure. Following filesystem best practices helps maintain a clean, secure, and efficient system while reducing the risk of data loss and simplifying system administration.

This guide covers practical recommendations for managing files, directories, and storage on Linux systems.

---

# Why Follow Filesystem Best Practices?

Good filesystem practices help you:

- Keep the system organized
- Improve security
- Simplify backups
- Prevent accidental data loss
- Optimize storage usage
- Make troubleshooting easier

---

# 1. Follow the Filesystem Hierarchy Standard (FHS)

Linux follows the **Filesystem Hierarchy Standard (FHS)**, which defines the purpose of each top-level directory.

Common directories:

| Directory | Purpose |
|-----------|---------|
| `/home` | User files |
| `/etc` | Configuration files |
| `/var` | Variable data (logs, cache, databases) |
| `/usr` | Applications and shared resources |
| `/tmp` | Temporary files |
| `/opt` | Third-party software |

Avoid storing files in incorrect locations.

---

# 2. Keep Personal Files in `/home`

Store documents, projects, downloads, and scripts inside your home directory.

Example:

```text
/home/alice/
├── Documents
├── Downloads
├── Projects
└── Scripts
```

Avoid saving personal files in system directories.

---

# 3. Do Not Modify System Directories Unnecessarily

Directories such as:

- `/bin`
- `/lib`
- `/usr`
- `/boot`

contain essential system files.

Only modify them when required and with proper understanding.

---

# 4. Separate Data from Configuration

Store configuration files separately from application data.

Example:

```text
Configuration:
/etc/nginx/nginx.conf

Website files:
/var/www/html/
```

This makes backups and migrations easier.

---

# 5. Use Meaningful Directory Names

Use descriptive names instead of generic ones.

Good:

```text
Projects/
Linux-Docs/
Backups/
```

Poor:

```text
Stuff/
Misc/
New Folder/
```

Clear names improve navigation and collaboration.

---

# 6. Avoid Excessively Deep Directory Structures

Example of a poor structure:

```text
Projects/
    Old/
        Backup/
            Final/
                Version/
                    Files/
```

Instead, keep the hierarchy simple and logical.

---

# 7. Use Appropriate File Permissions

Protect files using proper ownership and permissions.

Check permissions:

```bash
ls -l
```

Change permissions:

```bash
chmod
```

Change ownership:

```bash
chown
```

Grant only the permissions that users actually need.

---

# 8. Clean Temporary Files Regularly

Temporary files accumulate over time.

Common locations:

```text
/tmp
/var/tmp
```

Remove unnecessary temporary files periodically.

---

# 9. Monitor Disk Usage

Check available storage regularly.

Display filesystem usage:

```bash
df -h
```

Display directory sizes:

```bash
du -sh *
```

Monitoring storage helps prevent unexpected disk exhaustion.

---

# 10. Organize Project Files

Keep project files together.

Example:

```text
project/
├── docs/
├── src/
├── scripts/
├── tests/
└── README.md
```

A consistent structure makes projects easier to maintain.

---

# 11. Avoid Duplicate Files

Instead of storing multiple copies:

- Use symbolic links when appropriate.
- Keep backups in dedicated backup directories.
- Remove obsolete versions.

Locate duplicates:

```bash
find . -type f
```

---

# 12. Use Symbolic Links Carefully

Symbolic links provide shortcuts to files or directories.

Create a symbolic link:

```bash
ln -s /opt/project ~/project
```

Avoid creating unnecessary or broken links.

---

# 13. Keep Log Files Under Control

System logs are usually stored in:

```text
/var/log
```

Regularly:

- Review logs
- Rotate logs
- Remove obsolete logs if appropriate

Large log files can consume significant disk space.

---

# 14. Back Up Important Data

Always maintain backups of:

- Personal files
- Configuration files
- Databases
- Projects

Popular backup tools include:

- rsync
- tar
- Timeshift
- BorgBackup

---

# 15. Mount External Storage Properly

Mount removable storage using standard mount points.

Examples:

```text
/media
/mnt
```

Check mounted filesystems:

```bash
findmnt
```

Unmount devices safely before removing them:

```bash
umount /mnt
```

---

# 16. Use Version Control for Important Projects

Rather than keeping multiple copies of files, use a version control system.

Example:

```bash
git init
```

Benefits:

- Version history
- Easier collaboration
- Reliable recovery of previous changes

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Saving personal files in `/etc` | Use `/home` |
| Ignoring disk usage | Monitor with `df` and `du` |
| Using weak permissions | Apply least-privilege permissions |
| Creating cluttered directories | Organize logically |
| Forgetting backups | Schedule regular backups |
| Leaving large log files unmanaged | Rotate and clean logs |

---

# Best Practices Checklist

- Follow the Filesystem Hierarchy Standard.
- Keep personal files in `/home`.
- Avoid modifying system directories.
- Separate configuration from application data.
- Use meaningful directory names.
- Monitor disk usage regularly.
- Apply proper file permissions.
- Clean temporary files.
- Back up important data.
- Mount external storage correctly.
- Organize projects consistently.
- Use version control for source code.

---

# Key Takeaways

- A well-organized filesystem improves security, maintainability, and performance.
- Following Linux directory conventions makes systems easier to administer.
- Regular monitoring, backups, and permission management help prevent common filesystem problems.
- Good filesystem organization benefits both individual users and teams.

---

## Related Topics

- Filesystem Architecture
- Files and Directories
- Permissions
- Disk Storage
- Backup and Restore
- File Management Commands
- Package Management
```