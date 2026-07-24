# Permissions Best Practices

## Overview

Permissions are one of Linux's core security features. They determine who can read, write, or execute files and directories. Proper permission management protects sensitive data, prevents unauthorized access, and helps maintain system integrity.

This guide covers best practices for managing file and directory permissions in Linux.

---

# Why Follow Permission Best Practices?

Proper permissions help you:

- Protect sensitive files
- Prevent unauthorized access
- Reduce security risks
- Protect system integrity
- Support multi-user environments
- Simplify administration

---

# 1. Follow the Principle of Least Privilege

Grant users only the permissions they need to perform their tasks.

Instead of:

```text
Everyone has full access.
```

Use:

```text
Users receive only the minimum required permissions.
```

This minimizes accidental or malicious damage.

---

# 2. Avoid Using Root Regularly

Use a normal user account for daily work.

Use administrative privileges only when necessary.

Example:

```bash
sudo apt update
```

Instead of logging in directly as the root user.

---

# 3. Use Groups Effectively

Rather than assigning permissions to individual users, organize users into groups.

Example:

```text
developers
admins
finance
support
```

Groups simplify permission management.

---

# 4. Set Appropriate File Permissions

General recommendations:

| File Type | Recommended Permission |
|------------|------------------------|
| Regular files | 644 |
| Executable scripts | 755 |
| Directories | 755 |
| Private files | 600 |
| SSH private keys | 600 |

Avoid giving more permissions than necessary.

---

# 5. Protect Sensitive Files

Sensitive files should be readable only by authorized users.

Examples:

- SSH keys
- Password files
- Configuration files containing secrets
- SSL certificates

Example:

```bash
chmod 600 ~/.ssh/id_rsa
```

---

# 6. Avoid Using 777 Permissions

Never use:

```bash
chmod 777 file
```

unless absolutely necessary.

Problems:

- Anyone can read
- Anyone can modify
- Anyone can execute

This creates significant security risks.

---

# 7. Regularly Review Permissions

Periodically audit file permissions.

Useful command:

```bash
find /home -type f -perm -002
```

This helps identify world-writable files.

---

# 8. Set Correct Ownership

Ensure files are owned by the appropriate user and group.

View ownership:

```bash
ls -l
```

Change owner:

```bash
sudo chown user:group file
```

Proper ownership prevents unauthorized modifications.

---

# 9. Secure Home Directories

Users should not access each other's private files unless required.

Recommended permissions:

```text
700
750
```

depending on organizational requirements.

---

# 10. Protect System Files

System directories such as:

```text
/etc
/bin
/usr
/boot
```

should only be modified by administrators.

Avoid changing permissions on critical system files without understanding the consequences.

---

# 11. Use Access Control Lists (ACLs) When Needed

Standard permissions may not always be flexible enough.

Linux supports ACLs for more granular access control.

Example:

```bash
setfacl -m u:alice:rwx project/
```

ACLs allow permissions for specific users without changing ownership.

---

# 12. Monitor Permission Changes

Unexpected permission changes may indicate:

- Configuration errors
- User mistakes
- Security incidents

Regular audits help detect unauthorized modifications.

---

# 13. Limit SUID and SGID Programs

Special permission bits such as SUID and SGID should be used sparingly.

Find SUID files:

```bash
find / -perm -4000
```

Review them periodically to reduce security risks.

---

# 14. Back Up Important Permissions

When backing up systems, preserve ownership and permissions.

Example:

```bash
cp -a source destination
```

or

```bash
tar -p
```

This ensures restored files retain their original security settings.

---

# 15. Educate Users

Users should understand:

- File ownership
- Read, write, execute permissions
- Safe use of `chmod`
- Safe use of `chown`
- Risks of overly permissive access

User awareness improves overall system security.

---

# Common Permission Commands

View permissions:

```bash
ls -l
```

Change permissions:

```bash
chmod 755 file
```

Change owner:

```bash
sudo chown user file
```

Change group:

```bash
sudo chgrp developers file
```

View numeric permissions:

```bash
stat file
```

Find world-writable files:

```bash
find / -type f -perm -002
```

Find SUID files:

```bash
find / -perm -4000
```

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Using `chmod 777` everywhere | Apply only necessary permissions |
| Working as root all the time | Use `sudo` only when needed |
| Ignoring file ownership | Assign proper owners and groups |
| Giving everyone write access | Follow the principle of least privilege |
| Forgetting to audit permissions | Review permissions regularly |
| Ignoring SUID programs | Monitor and minimize their use |

---

# Best Practices Checklist

- Follow the principle of least privilege.
- Use normal user accounts for daily work.
- Organize users into groups.
- Assign appropriate file permissions.
- Protect sensitive files.
- Avoid `chmod 777`.
- Review permissions regularly.
- Set correct ownership.
- Secure home directories.
- Use ACLs when needed.
- Audit SUID and SGID programs.
- Preserve permissions during backups.

---

# Key Takeaways

- Linux permissions are essential for protecting files, directories, and system resources.
- Grant only the access users require and avoid overly permissive settings.
- Regular audits, proper ownership, and secure handling of privileged files help maintain a secure and stable system.
- Good permission management is a cornerstone of Linux system administration.

---

## Related Topics

- Users and Groups
- File System
- Security
- Access Control Lists (ACLs)
- System Administration
- File Management
- Linux Commands
- Troubleshooting