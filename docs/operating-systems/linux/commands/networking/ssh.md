# ssh

> Securely connect to and manage remote systems over an encrypted network connection.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`ssh` (Secure Shell) is a secure network protocol and command-line tool used to remotely access and manage computers over an encrypted connection.

It is one of the most important Linux commands and is widely used by system administrators, DevOps engineers, cloud engineers, and developers to securely administer servers.

- **What does it do?** Establishes a secure remote terminal session.
- **Why does it exist?** To replace insecure remote login protocols like Telnet by providing encryption and authentication.
- **When is it commonly used?** Managing remote servers, deploying applications, transferring files, executing remote commands, and tunneling network traffic.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Connect to remote Linux servers
- Authenticate using passwords or SSH keys
- Connect using custom ports
- Execute remote commands
- Troubleshoot common SSH connection issues

---

# ⚙️ Syntax

```bash
ssh [options] user@host
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `user` | Username on the remote system | Yes |
| `host` | Hostname or IP address | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-p <port>` | Connect using a custom SSH port |
| `-i <key>` | Specify an SSH private key |
| `-v` | Enable verbose debugging output |
| `-X` | Enable X11 forwarding |
| `-L` | Create a local port forwarding tunnel |
| `-R` | Create a remote port forwarding tunnel |
| `-N` | Do not execute a remote command |
| `-T` | Disable pseudo-terminal allocation |

---

# 💻 Basic Examples

## Example 1

```bash
ssh user@192.168.1.10
```

Connect to a remote server.

---

## Example 2

```bash
ssh user@example.com
```

Connect using a hostname.

---

## Example 3

```bash
ssh -p 2222 user@server
```

Connect using a custom SSH port.

---

## Example 4

```bash
ssh -i ~/.ssh/id_ed25519 user@server
```

Authenticate using a specific SSH private key.

---

## Example 5

```bash
ssh user@server "uptime"
```

Run a single command remotely without opening an interactive shell.

---

# 📤 Example Output

```text
The authenticity of host '192.168.1.10' can't be established.
ED25519 key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxx.
Are you sure you want to continue connecting (yes/no)? yes

Welcome to Ubuntu 24.04 LTS

user@server:~$
```

Explanation:

- The first connection asks you to verify the server's identity.
- The server's public key is stored in `~/.ssh/known_hosts`.
- Future connections verify the stored key automatically.

---

# 🌍 Real-world Use Cases

- Managing cloud servers (AWS, Azure, GCP)
- Deploying applications
- Administering Linux servers
- Running remote maintenance scripts
- Securely accessing Raspberry Pi devices
- Managing Kubernetes nodes

---

# 🧠 How It Works

SSH establishes an encrypted connection between the client and the remote server.

The authentication process can use:

- Password authentication
- Public/private SSH key pairs
- Certificates

Once authenticated, all communication—including commands, file transfers, and terminal sessions—is encrypted.

---

# ⚠️ Common Mistakes

❌ Using passwords instead of SSH keys.

SSH keys are significantly more secure and are the recommended authentication method.

---

❌ Forgetting the correct username.

```bash
ssh root@server
```

may fail if the server expects another user such as:

```bash
ssh ubuntu@server
```

---

❌ Ignoring host key warnings.

Never blindly accept changed host keys—they may indicate a man-in-the-middle attack or that the server has been rebuilt.

---

# ✅ Best Practices

- Use SSH key authentication instead of passwords.
- Protect your private key with appropriate file permissions.
- Disable password authentication on production servers when possible.
- Verify host fingerprints before accepting new servers.
- Use `~/.ssh/config` to simplify frequent connections.

---

# 🔒 Security Considerations

Never share your private SSH key.

Typical SSH key files:

```text
~/.ssh/id_ed25519
~/.ssh/id_rsa
```

The public key (`.pub`) can be shared with remote servers, but the private key must remain secret.

Use passphrases to add another layer of protection.

---

# 🚀 Performance Notes

SSH encryption introduces minimal overhead on modern hardware.

Using SSH keys typically speeds up authentication compared to entering passwords.

Compression (`-C`) can improve performance on slower network connections.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `scp` | Securely copy files over SSH |
| `rsync` | Synchronize files over SSH |
| `ssh-keygen` | Generate SSH key pairs |
| `ssh-copy-id` | Install SSH public keys on remote systems |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `ssh` | Secure remote login |
| `scp` | Secure file transfer |
| `rsync` | Efficient file synchronization |
| `telnet` | Unencrypted remote login (obsolete for administration) |

---

# 🧪 Practice Exercises

### Beginner

Connect to a remote Linux server using SSH.

---

### Intermediate

Generate an SSH key pair and authenticate without using a password.

---

### Advanced

Configure SSH to use a custom port and connect using a configuration file.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is SSH?

**A:** SSH (Secure Shell) is a protocol for securely accessing and managing remote systems over an encrypted connection.

---

### Intermediate

**Q:** What is the difference between a public key and a private key?

**A:** The public key is copied to the remote server, while the private key remains on the client and is used to prove identity during authentication.

---

### Advanced

**Q:** Why is SSH considered more secure than Telnet?

**A:** SSH encrypts all communication, including authentication and data transfer, while Telnet transmits everything in plain text.

---

# 🛠 Troubleshooting

**Problem:** `Permission denied (publickey)`

**Cause:**

- Public key not installed on the server
- Wrong private key
- Incorrect file permissions

**Solution:**

- Verify the public key exists in `~/.ssh/authorized_keys`
- Use the correct private key with `-i`
- Check permissions on `.ssh` directories and key files

---

**Problem:** `Connection refused`

**Cause:**

- SSH server is not running
- Incorrect port
- Firewall blocking access

**Solution:**

- Verify the SSH service is running
- Check firewall settings
- Confirm the correct SSH port

---

# 📚 Official Documentation

- `man ssh`
- https://man.openbsd.org/ssh

---

# 📖 Further Reading

- Nexora: `scp`
- Nexora: `rsync`
- Nexora: `ssh-keygen`
- Linux SSH Fundamentals

---

# 📌 Quick Summary

- `ssh` provides secure remote access to Linux systems.
- Supports password and SSH key authentication.
- Encrypts all communication.
- Forms the foundation for tools like `scp` and `rsync`.
- SSH keys are the recommended authentication method.

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