# Linux Permissions Cheat Sheet

## Overview

Linux permissions control who can read, write, or execute files and directories. Proper permission management is essential for system security and access control.

---

# Permission Types

| Symbol | Meaning | Description |
|--------|---------|-------------|
| `r` | Read | View file contents or list directory contents |
| `w` | Write | Modify a file or directory |
| `x` | Execute | Run a file or enter a directory |

---

# Permission Numbers

| Number | Permission | Binary |
|---------|------------|--------|
| 0 | --- | 000 |
| 1 | --x | 001 |
| 2 | -w- | 010 |
| 3 | -wx | 011 |
| 4 | r-- | 100 |
| 5 | r-x | 101 |
| 6 | rw- | 110 |
| 7 | rwx | 111 |

---

# User Classes

| Symbol | Description |
|--------|-------------|
| `u` | Owner (User) |
| `g` | Group |
| `o` | Others |
| `a` | All users |

---

# View Permissions

```bash
ls -l
```

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
- rwx r-x r--
  │   │   │
  │   │   └── Others
  │   └────── Group
  └────────── Owner
```

---

# Change Permissions (Symbolic)

Add execute permission:

```bash
chmod +x script.sh
```

Remove write permission:

```bash
chmod u-w file.txt
```

Add read permission to group:

```bash
chmod g+r file.txt
```

Grant all permissions to owner:

```bash
chmod u+rwx file.txt
```

Remove all permissions from others:

```bash
chmod o-rwx file.txt
```

---

# Change Permissions (Numeric)

```bash
chmod 777 file
chmod 755 file
chmod 700 file
chmod 644 file
chmod 600 file
```

---

# Common Permission Values

| Permission | Meaning |
|------------|---------|
| `777` | Everyone has full access *(avoid unless necessary)* |
| `755` | Owner full, others read & execute |
| `750` | Owner full, group read & execute |
| `700` | Owner only |
| `644` | Owner read/write, others read |
| `640` | Owner read/write, group read |
| `600` | Owner read/write only |
| `400` | Read-only for owner |

---

# Change Ownership

Change owner:

```bash
sudo chown user file.txt
```

Change owner and group:

```bash
sudo chown user:developers file.txt
```

Change group:

```bash
sudo chgrp developers file.txt
```

Recursive ownership:

```bash
sudo chown -R user:group directory/
```

---

# Default Permissions

Display current umask:

```bash
umask
```

Set umask:

```bash
umask 022
```

Common values:

| Umask | Default File | Default Directory |
|--------|--------------|-------------------|
| 022 | 644 | 755 |
| 027 | 640 | 750 |
| 077 | 600 | 700 |

---

# Special Permissions

## SUID

```bash
chmod u+s file
```

Numeric:

```bash
chmod 4755 file
```

Example:

```bash
-rwsr-xr-x
```

---

## SGID

```bash
chmod g+s directory
```

Numeric:

```bash
chmod 2755 directory
```

Example:

```bash
drwxr-sr-x
```

---

## Sticky Bit

```bash
chmod +t directory
```

Numeric:

```bash
chmod 1777 directory
```

Example:

```bash
drwxrwxrwt
```

Used for:

```text
/tmp
```

---

# File Attributes

View attributes:

```bash
lsattr file
```

Make immutable:

```bash
sudo chattr +i file
```

Remove immutable flag:

```bash
sudo chattr -i file
```

---

# Access Control Lists (ACL)

View ACL:

```bash
getfacl file
```

Grant permission:

```bash
setfacl -m u:john:rwx file
```

Remove ACL:

```bash
setfacl -x u:john file
```

---

# Find Files by Permission

World-writable files:

```bash
find / -perm -002
```

Executable files:

```bash
find . -perm /111
```

SUID files:

```bash
find / -perm -4000
```

SGID files:

```bash
find / -perm -2000
```

---

# Useful Commands

```bash
ls -l
chmod
chown
chgrp
umask
lsattr
chattr
getfacl
setfacl
find
```

---

# Permission Examples

Make script executable:

```bash
chmod +x script.sh
```

Private file:

```bash
chmod 600 secrets.txt
```

Public HTML file:

```bash
chmod 644 index.html
```

Private directory:

```bash
chmod 700 private/
```

Shared project directory:

```bash
chmod 775 project/
```

---

# Best Practices

- Follow the Principle of Least Privilege.
- Avoid using `chmod 777`.
- Assign ownership carefully.
- Use groups instead of granting permissions to everyone.
- Review permissions regularly.
- Use ACLs only when traditional permissions are insufficient.
- Protect sensitive files with restrictive permissions.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Using `777` everywhere | Use the minimum required permissions |
| Running as root unnecessarily | Use `sudo` only when needed |
| Ignoring ownership | Verify owner and group |
| Making sensitive files public | Restrict access with `600` or `640` |
| Forgetting execute permission | Use `chmod +x` for scripts |

---

# Quick Reference

```bash
ls -l                 # View permissions
chmod 755 file        # Change permissions
chmod +x script.sh    # Make executable
chown user file       # Change owner
chgrp group file      # Change group
umask                 # View default permissions
lsattr                # View file attributes
chattr +i file        # Make immutable
getfacl file          # View ACL
setfacl               # Modify ACL
```

---

# Related Topics

- Permissions
- Users and Groups
- File Management
- Security
- Filesystem
- Linux Commands
- Access Control
- System Administration