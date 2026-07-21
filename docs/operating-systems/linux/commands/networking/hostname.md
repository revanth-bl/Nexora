# hostname

> Display or temporarily set the system's hostname.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 5 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`hostname` is a command used to display or temporarily change the hostname of a Linux system. The hostname uniquely identifies a machine on a network and is commonly used in networking, system administration, and server management.

- **What does it do?** Displays or changes the system's hostname.
- **Why does it exist?** Every computer on a network needs a unique name for identification and communication.
- **When is it commonly used?** Checking system identity, configuring servers, troubleshooting networking issues, and SSH administration.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display the current hostname
- View the Fully Qualified Domain Name (FQDN)
- Display the IP address associated with the hostname
- Understand temporary hostname changes
- Know when to use `hostnamectl` instead

---

# ⚙️ Syntax

```bash
hostname [options] [new-hostname]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `new-hostname` | Temporary hostname to assign | No |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-f` | Display Fully Qualified Domain Name (FQDN) |
| `-I` | Display all assigned IP addresses |
| `-i` | Display hostname's IP address |
| `-s` | Display short hostname |
| `-d` | Display DNS domain name |
| `--help` | Show help information |

---

# 💻 Basic Examples

## Example 1

```bash
hostname
```

Displays the current hostname.

---

## Example 2

```bash
hostname -I
```

Displays all IP addresses assigned to the system.

---

## Example 3

```bash
hostname -f
```

Displays the Fully Qualified Domain Name.

---

## Example 4

```bash
sudo hostname web-server
```

Temporarily changes the hostname until the next reboot.

---

# 📤 Example Output

```text
$ hostname
ubuntu-server
```

```text
$ hostname -I
192.168.1.15 172.17.0.1
```

```text
$ hostname -f
ubuntu-server.example.com
```

---

# 🌍 Real-world Use Cases

- Identifying remote servers after logging in with SSH
- Verifying system identity before deployment
- Checking network configuration
- Troubleshooting DNS issues
- Managing multiple Linux servers

---

# 🧠 How It Works

The Linux kernel stores the system hostname in memory. Running `hostname` retrieves this value. When changing the hostname using the command, the change is temporary and lasts only until the next reboot unless updated through system configuration.

On modern Linux distributions using **systemd**, `hostnamectl` is the preferred tool for making permanent hostname changes.

---

# ⚠️ Common Mistakes

❌ Assuming `hostname` permanently changes the hostname.

❌ Confusing hostname with IP address.

❌ Forgetting to update `/etc/hosts` after changing the hostname on some systems.

---

# ✅ Best Practices

- Use descriptive hostnames for servers.
- Use `hostnamectl` for permanent hostname changes.
- Verify hostname after making changes.
- Keep naming conventions consistent across infrastructure.

---

# 🔒 Security Considerations

Hostnames often reveal information about an organization's infrastructure (for example, `db-prod-01` or `finance-server`). Avoid exposing sensitive hostname information in publicly shared logs or screenshots.

---

# 🚀 Performance Notes

The `hostname` command is extremely lightweight and completes almost instantly since it reads information maintained by the operating system.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| hostnamectl | Permanently manage hostnames |
| uname | Display kernel and system information |
| ip | Display network configuration |
| ping | Test network connectivity |
| ssh | Connect to remote systems |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| hostname | Display or temporarily change hostname |
| hostnamectl | Permanently configure hostname (systemd) |
| uname -n | Display network node hostname |

---

# 🧪 Practice Exercises

### Beginner

Display your computer's hostname.

---

### Intermediate

Display all IP addresses assigned to your system.

---

### Advanced

Temporarily rename your machine and verify the change.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is a hostname?

**A:** A hostname is the human-readable name assigned to a computer or device on a network.

---

### Intermediate

**Q:** What is the difference between `hostname` and `hostnamectl`?

**A:** `hostname` displays or temporarily changes the hostname, while `hostnamectl` permanently manages the hostname on systemd-based Linux systems.

---

### Advanced

**Q:** Why is a consistent hostname naming convention important?

**A:** It improves infrastructure management, automation, monitoring, troubleshooting, and makes large server environments easier to understand.

---

# 🛠 Troubleshooting

**Problem:** Hostname reverts after reboot.

**Cause:** The hostname was changed only temporarily using the `hostname` command.

**Solution:** Use:

```bash
sudo hostnamectl set-hostname new-hostname
```

to make the change permanent.

---

# 📚 Official Documentation

- `man hostname`
- `man hostnamectl`
- https://man7.org/linux/man-pages/man1/hostname.1.html

---

# 📖 Further Reading

- Nexora: `hostnamectl`
- Nexora: `ip`
- Nexora: DNS Concepts

---

# 📌 Quick Summary

- `hostname` displays the system's hostname.
- It can temporarily change the hostname.
- Use `hostnamectl` for permanent changes.
- Frequently used in networking, server administration, and troubleshooting.

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