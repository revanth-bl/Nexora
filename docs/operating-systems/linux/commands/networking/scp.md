# scp

> Securely copy files and directories between local and remote systems using SSH.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 6 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`scp` (Secure Copy Protocol) is a command-line utility used to securely transfer files and directories between computers over an SSH connection.

Unlike `cp`, which copies files locally, `scp` encrypts all data during transmission, making it suitable for transferring sensitive information across networks.

- **What does it do?** Securely copies files between local and remote systems.
- **Why does it exist?** To provide a simple and secure way to transfer files over SSH.
- **When is it commonly used?** Deploying applications, transferring configuration files, backing up data, and copying logs from remote servers.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Copy files to remote servers
- Download files from remote systems
- Copy entire directories
- Use custom SSH ports
- Transfer files securely using SSH authentication

---

# ⚙️ Syntax

```bash
scp [options] source destination
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
| `-r` | Copy directories recursively |
| `-P <port>` | Specify SSH port |
| `-i <key>` | Use a specific SSH private key |
| `-p` | Preserve timestamps and permissions |
| `-C` | Compress data during transfer |
| `-v` | Enable verbose output |

---

# 💻 Basic Examples

## Example 1

```bash
scp file.txt user@server:/home/user/
```

Copies a local file to a remote server.

---

## Example 2

```bash
scp user@server:/home/user/file.txt .
```

Downloads a file from a remote server to the current directory.

---

## Example 3

```bash
scp -r project/ user@server:/var/www/
```

Copies an entire directory recursively.

---

## Example 4

```bash
scp -P 2222 file.txt user@server:/home/user/
```

Uses a custom SSH port.

---

## Example 5

```bash
scp -i ~/.ssh/id_ed25519 file.txt user@server:/home/user/
```

Uses a specific SSH private key.

---

# 📤 Example Output

```text
file.txt                               100%   24KB  1.4MB/s   00:00
```

Explanation:

- **100%** → Transfer completed successfully.
- **24KB** → File size.
- **1.4MB/s** → Transfer speed.
- **00:00** → Time taken.

---

# 🌍 Real-world Use Cases

- Uploading website files to production servers
- Downloading log files for troubleshooting
- Copying configuration files
- Backing up remote systems
- Transferring files between Linux servers

---

# 🧠 How It Works

`scp` establishes an encrypted SSH connection between the source and destination systems.

Once authenticated, the file data is securely transferred through the SSH tunnel, protecting it from interception during transmission.

---

# ⚠️ Common Mistakes

❌ Forgetting the `-r` option when copying directories.

```bash
scp project/ user@server:/backup/
```

This will fail.

Use:

```bash
scp -r project/ user@server:/backup/
```

---

❌ Using the wrong SSH port.

If SSH runs on a custom port, specify it using `-P`.

---

❌ Confusing `-P` and `-p`.

- `-P` → SSH Port
- `-p` → Preserve timestamps and permissions

---

# ✅ Best Practices

- Use SSH key authentication instead of passwords.
- Verify the destination path before copying.
- Use `-C` for slower network connections.
- Use `rsync` instead of `scp` for repeated transfers of large files.

---

# 🔒 Security Considerations

All data transferred using `scp` is encrypted through SSH.

Protect your private SSH keys and avoid copying sensitive files to untrusted systems.

Disable password authentication when possible and use SSH keys for stronger security.

---

# 🚀 Performance Notes

`scp` copies the entire file every time.

For frequently changing files or large directories, `rsync` is usually faster because it transfers only modified data.

Compression (`-C`) can improve transfer speed over slow networks.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `ssh` | Provides secure remote login |
| `rsync` | Efficient file synchronization |
| `cp` | Local file copying |
| `wget` | Download files from web servers |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `cp` | Copies files locally |
| `scp` | Securely copies files over SSH |
| `rsync` | Synchronizes only changed data |

---

# 🧪 Practice Exercises

### Beginner

Upload a text file to a remote server.

---

### Intermediate

Download a configuration file from a remote Linux machine.

---

### Advanced

Copy an entire project directory using SSH keys on a custom port.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What protocol does `scp` use?

**A:** It uses SSH (Secure Shell) for encrypted file transfers.

---

### Intermediate

**Q:** What is the difference between `scp` and `cp`?

**A:** `cp` copies files locally, while `scp` securely transfers files between systems over SSH.

---

### Advanced

**Q:** Why might `rsync` be preferred over `scp`?

**A:** `rsync` transfers only changed portions of files, reducing bandwidth usage and improving performance for repeated transfers.

---

# 🛠 Troubleshooting

**Problem:** Permission denied.

**Cause:** Incorrect file permissions or failed SSH authentication.

**Solution:**

- Verify SSH login works.
- Check file permissions.
- Ensure the correct SSH key is being used.

---

**Problem:** Connection refused.

**Cause:** SSH service is not running or the wrong port was specified.

**Solution:**

- Verify the SSH server is running.
- Check firewall rules.
- Confirm the correct port with:

```bash
ssh user@server
```

---

# 📚 Official Documentation

- `man scp`
- https://man.openbsd.org/scp

---

# 📖 Further Reading

- Nexora: `ssh`
- Nexora: `rsync`
- Linux SSH Fundamentals

---

# 📌 Quick Summary

- `scp` securely copies files using SSH.
- Supports both uploads and downloads.
- Use `-r` for directories.
- Use `-P` for custom SSH ports.
- Prefer SSH key authentication for better security.

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