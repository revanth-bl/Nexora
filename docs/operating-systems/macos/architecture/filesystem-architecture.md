# macOS Filesystem Architecture

## Overview

The **macOS filesystem architecture** defines how macOS organizes, stores, protects, and accesses data.

Modern macOS systems primarily use **APFS (Apple File System)**, which was designed by Apple for flash storage and SSD-based systems while supporting features required by modern macOS security and system-management technologies.

Understanding the filesystem architecture is essential for system administration, troubleshooting, storage management, permissions, backups, and security.

---

# High-Level Architecture

A simplified view of the macOS filesystem is:

```text
Physical Storage
       │
       ▼
   APFS Container
       │
       ├── System Volume
       │
       ├── Data Volume
       │
       ├── Preboot
       │
       ├── Recovery
       │
       └── VM
              │
              ▼
        macOS Filesystem
              │
              ├── System Files
              ├── Applications
              ├── Users
              ├── Library Data
              └── Temporary Data
```

The exact layout can vary depending on the macOS version, Mac architecture, and storage configuration.

---

# APFS

**APFS (Apple File System)** is the primary filesystem used by modern macOS installations.

It replaced HFS+ as Apple's main filesystem for modern operating systems.

APFS was designed with modern storage technologies and security requirements in mind.

Important APFS features include:

- Space sharing
- Snapshots
- Cloning
- Encryption
- Copy-on-write
- Fast directory sizing
- Crash protection
- Multiple volumes inside a container

---

# APFS Containers

An APFS container is a storage-management layer that can contain multiple APFS volumes.

A simplified structure looks like:

```text
Physical Disk
      │
      ▼
APFS Container
      │
      ├── Macintosh HD
      ├── Macintosh HD - Data
      ├── Preboot
      ├── Recovery
      └── VM
```

Unlike traditional partition layouts, APFS volumes inside the same container can dynamically share available storage space.

---

# APFS Volumes

An APFS container can contain multiple volumes.

Modern macOS installations commonly use separate volumes for different purposes.

### System Volume

Contains the macOS operating-system files.

On modern macOS versions, the system volume is protected from normal modification.

### Data Volume

Contains writable data associated with the operating system and users.

This includes:

- User home directories
- Applications and application data
- Writable system data
- User configuration
- Documents

### Preboot Volume

Contains files required during the boot process.

It helps the system locate and load the appropriate operating-system environment.

### Recovery Volume

Contains components used by macOS Recovery.

Recovery tools can be used for:

- System repair
- Disk management
- macOS reinstallation
- Security recovery
- Troubleshooting

### VM Volume

Used for virtual-memory-related storage.

---

# System and Data Volume Separation

Modern macOS separates operating-system files from writable user and system data.

A simplified representation is:

```text
macOS
│
├── System Volume
│      └── Protected Operating System
│
└── Data Volume
       ├── Users
       ├── Applications
       ├── Writable System Data
       └── Other Data
```

This separation helps protect the operating system while allowing applications and users to modify appropriate areas.

---

# Signed System Volume

Modern macOS uses the **Signed System Volume (SSV)** security mechanism.

The system volume is cryptographically verified to help ensure that operating-system files have not been improperly modified.

This works together with other macOS security technologies such as:

- Secure Boot
- System Integrity Protection
- Code signing
- FileVault

The goal is to establish greater trust in the operating system loaded during startup.

---

# Filesystem Hierarchy

Although macOS provides a graphical interface for managing files, it retains a Unix-style filesystem hierarchy.

Important directories include:

```text
/
├── Applications
├── Library
├── System
├── Users
├── Volumes
├── private
├── bin
├── sbin
├── usr
├── dev
├── etc
├── tmp
└── var
```

Some directories may be implemented differently, protected, hidden, or linked internally depending on the macOS version.

---

# Root Directory

The root directory is represented by:

```text
/
```

It is the top-level directory of the filesystem hierarchy.

You can inspect it with:

```bash
ls /
```

---

# Applications

Applications installed for general system use are commonly located in:

```text
/Applications
```

Applications installed only for a particular user may also exist within the user's home directory.

For example:

```text
~/Applications
```

---

# Users

User home directories are normally located under:

```text
/Users
```

For example:

```text
/Users/username
```

A user's home directory commonly contains:

```text
Desktop
Documents
Downloads
Library
Movies
Music
Pictures
Public
```

---

# User Library

Each user has a Library directory:

```text
~/Library
```

It contains user-specific application data and configuration.

Examples include:

- Application preferences
- Caches
- Application support data
- Saved application state
- User-specific configuration

The user Library is normally hidden from casual browsing in Finder but can be accessed through Terminal.

```bash
ls ~/Library
```

---

# System Library

The system-level Library is:

```text
/Library
```

It contains resources shared across the system.

Examples include:

- System configuration
- Frameworks
- Launch services
- Fonts
- System extensions
- Application support resources

---

# System Directory

The macOS operating-system components are associated with:

```text
/System
```

Modern macOS protects important system content from unauthorized modification.

The exact internal organization can vary between macOS releases.

---

# Volumes

Mounted filesystems are accessible through:

```text
/Volumes
```

For example, an external disk might appear as:

```text
/Volumes/ExternalDrive
```

You can inspect mounted volumes with:

```bash
ls /Volumes
```

---

# Unix Directories

macOS also provides traditional Unix directories.

### `/bin`

Contains essential command-line utilities.

### `/sbin`

Contains essential system administration utilities.

### `/usr`

Contains many Unix utilities, libraries, and system resources.

### `/etc`

Provides compatibility and configuration-related paths.

### `/var`

Contains variable system data.

### `/tmp`

Provides temporary storage.

### `/dev`

Contains device interfaces exposed through the Unix device model.

---

# File Permissions

macOS uses Unix-style file permissions.

A typical permission representation is:

```text
-rwxr-xr--
```

Permissions apply to:

```text
Owner
Group
Others
```

For example:

```bash
ls -l
```

can display permissions and ownership information.

macOS also supports additional security mechanisms beyond traditional Unix permissions.

These include:

- Access Control Lists (ACLs)
- System Integrity Protection
- Privacy permissions
- Application sandboxing
- Code signing

---

# Access Control Lists

Traditional Unix permissions are not always sufficient for modern macOS security requirements.

macOS supports **ACLs (Access Control Lists)** for more detailed permission control.

ACLs can provide permissions for specific users or groups beyond the basic owner/group/other model.

They can be inspected with:

```bash
ls -le
```

---

# File Flags

macOS supports filesystem-level file flags.

They can be viewed with:

```bash
ls -lO
```

These flags can provide additional restrictions or metadata associated with files.

---

# Extended Attributes

macOS makes extensive use of **extended attributes**.

They store additional metadata associated with files.

You can inspect them using:

```bash
xattr filename
```

To display their values:

```bash
xattr -l filename
```

Extended attributes can be used for information associated with:

- Downloads
- Applications
- Security metadata
- Finder behavior
- Filesystem metadata

---

# Resource Forks and Metadata

Historically, macOS inherited support for filesystem metadata concepts such as resource forks.

Modern macOS primarily uses extended attributes and related filesystem mechanisms for storing additional metadata.

This allows files to carry information beyond their main data stream.

---

# Copy-on-Write

APFS uses **copy-on-write (COW)** techniques.

Instead of immediately overwriting existing filesystem structures, new data can be written to a new location and filesystem metadata updated to reference it.

This helps improve filesystem consistency and enables features such as:

- Snapshots
- Cloning
- Efficient updates
- Crash resilience

---

# APFS Clones

APFS supports file and directory cloning.

A clone can initially share storage with the original data rather than immediately creating a complete physical copy.

When data changes, APFS can write the modified blocks separately.

Conceptually:

```text
Original File
      │
      ├──────────────┐
      │              │
      ▼              ▼
   Clone A        Clone B
      │              │
      └── Shared Data
```

This can make certain copy operations significantly more storage-efficient.

---

# APFS Snapshots

APFS supports filesystem snapshots.

A snapshot represents a point-in-time view of filesystem data.

Snapshots can be useful for:

- System updates
- Recovery
- Backup workflows
- Rollback operations
- System protection

A simplified model is:

```text
Filesystem
    │
    ├── Current State
    │
    ├── Snapshot A
    │
    └── Snapshot B
```

Snapshots are metadata-based and can initially require relatively little additional storage.

---

# Encryption

APFS supports filesystem encryption.

macOS can use encryption technologies such as **FileVault** to protect stored data.

Encryption helps protect information if the physical storage device is accessed outside the normal operating environment.

---

# FileVault

**FileVault** provides full-volume data encryption for macOS.

When enabled, data stored on the Mac is protected using encryption.

A simplified flow is:

```text
User Authentication
        │
        ▼
Key Availability
        │
        ▼
Encrypted Storage
        │
        ▼
Filesystem Access
```

FileVault is particularly important for protecting data on lost or stolen Macs.

---

# Disk Utility

macOS provides **Disk Utility** for graphical storage management.

It can be used to:

- Inspect disks
- View APFS containers
- View volumes
- Format storage
- Partition disks
- Mount and unmount volumes
- Repair supported filesystem structures

---

# diskutil

The command-line equivalent for many storage-management operations is:

```bash
diskutil
```

List disks:

```bash
diskutil list
```

Show information about a disk:

```bash
diskutil info /dev/disk0
```

List APFS containers:

```bash
diskutil apfs list
```

> Storage-management commands can modify disks. Verify the target device carefully before performing destructive operations.

---

# Finding Disk Usage

The `df` command displays filesystem-level disk usage:

```bash
df -h
```

The `du` command displays directory and file usage:

```bash
du -sh ~/Documents
```

These tools answer different questions:

```text
df
│
└── How much space is available on the filesystem?

du
│
└── What is consuming space inside a directory?
```

---

# Mounting and Unmounting

Mounted filesystems are exposed through the filesystem hierarchy.

List mounted filesystems:

```bash
mount
```

Unmount a volume:

```bash
diskutil unmount /Volumes/VolumeName
```

Mounting and unmounting should be performed carefully, particularly when applications are actively using a volume.

---

# Filesystem and Security Boundaries

Modern macOS filesystem architecture is closely integrated with the operating system's security model.

Important boundaries include:

```text
Hardware
   │
   ▼
APFS Storage
   │
   ▼
System Volume
   │
   ├── Cryptographic Verification
   ├── SIP Protection
   └── System Security
   │
   ▼
Data Volume
   │
   ├── Users
   ├── Applications
   └── Writable Data
```

This architecture helps separate trusted operating-system components from data that applications and users need to modify.

---

# Important Commands

| Command | Purpose |
|---|---|
| `ls` | List directory contents |
| `pwd` | Show current directory |
| `cd` | Change directory |
| `df` | Show filesystem disk usage |
| `du` | Show directory disk usage |
| `mount` | Show mounted filesystems |
| `diskutil` | Manage disks and volumes |
| `diskutil list` | List storage devices |
| `diskutil apfs list` | Display APFS information |
| `ls -l` | Show permissions and ownership |
| `ls -le` | Show ACL information |
| `ls -lO` | Show file flags |
| `xattr` | Inspect extended attributes |
| `stat` | Display file metadata |

---

# Troubleshooting Filesystem Problems

When investigating a filesystem problem, follow a structured approach.

```text
Identify the affected volume
          │
          ▼
Check whether it is mounted
          │
          ▼
Check available storage
          │
          ▼
Inspect permissions
          │
          ▼
Inspect filesystem information
          │
          ▼
Check logs for related errors
          │
          ▼
Use appropriate recovery tools
```

Useful commands include:

```bash
df -h
```

```bash
diskutil list
```

```bash
diskutil apfs list
```

```bash
mount
```

```bash
ls -le
```

```bash
xattr -l filename
```

---

# Key Concepts

| Concept | Description |
|---|---|
| APFS | Apple's modern filesystem |
| APFS Container | Storage space containing APFS volumes |
| APFS Volume | Logical filesystem within a container |
| System Volume | Protected macOS operating-system data |
| Data Volume | Writable system and user data |
| Preboot | Boot-related data |
| Recovery | Recovery environment data |
| VM | Virtual-memory-related storage |
| Snapshot | Point-in-time filesystem state |
| Clone | Efficient copy sharing storage |
| Copy-on-write | Writes new data rather than overwriting existing structures directly |
| FileVault | Storage encryption technology |
| SSV | Signed System Volume |
| ACL | Extended filesystem permission model |
| Extended Attribute | Additional metadata attached to files |

---

# Summary

The macOS filesystem architecture combines a Unix filesystem hierarchy with Apple's modern APFS storage architecture and security technologies.

The most important concepts to understand are:

```text
APFS
 │
 ├── Containers
 │      │
 │      └── Volumes
 │
 ├── System / Data separation
 │
 ├── Snapshots
 │
 ├── Clones
 │
 ├── Encryption
 │
 └── Copy-on-write
```

At the operating-system level, this storage architecture works together with Unix permissions, ACLs, extended attributes, System Integrity Protection, Signed System Volume, and FileVault.

Understanding these layers provides the foundation for managing storage, diagnosing filesystem problems, and understanding how macOS protects its operating system and user data.