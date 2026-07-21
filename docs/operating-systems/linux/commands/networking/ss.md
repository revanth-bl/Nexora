# ss

> Display and investigate network sockets and active network connections on Linux systems.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`ss` (Socket Statistics) is a modern Linux utility used to inspect network sockets and active connections. It is the recommended replacement for the older `netstat` command because it is faster and provides more detailed information.

System administrators, DevOps engineers, and network engineers frequently use `ss` to troubleshoot network issues, identify listening services, and monitor active TCP and UDP connections.

- **What does it do?** Displays socket statistics and network connections.
- **Why does it exist?** To efficiently inspect network sockets and diagnose networking problems.
- **When is it commonly used?** Troubleshooting servers, checking listening ports, monitoring active connections, and debugging applications.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- View active TCP and UDP connections
- Identify listening services
- Filter socket information
- Display process information for sockets
- Troubleshoot network-related issues

---

# ⚙️ Syntax

```bash
ss [options]
```

---

# 📝 Parameters

Most `ss` operations use command-line options rather than positional parameters.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-t` | Show TCP sockets |
| `-u` | Show UDP sockets |
| `-l` | Show listening sockets only |
| `-a` | Show all sockets |
| `-n` | Show numeric addresses instead of resolving hostnames |
| `-p` | Display process using each socket |
| `-s` | Display socket statistics summary |
| `-4` | Show IPv4 sockets |
| `-6` | Show IPv6 sockets |

---

# 💻 Basic Examples

## Example 1

```bash
ss
```

Displays established network connections.

---

## Example 2

```bash
ss -t
```

Shows TCP connections only.

---

## Example 3

```bash
ss -tuln
```

Displays all listening TCP and UDP ports using numeric addresses.

---

## Example 4

```bash
sudo ss -tulpn
```

Shows listening services along with the owning process.

---

## Example 5

```bash
ss -s
```

Displays a summary of socket statistics.

---

# 📤 Example Output

```text
State   Recv-Q Send-Q Local Address:Port   Peer Address:Port
LISTEN  0      128    0.0.0.0:22           0.0.0.0:*
LISTEN  0      511    0.0.0.0:80           0.0.0.0:*
ESTAB   0      0      192.168.1.20:22      192.168.1.5:53012
```

Explanation:

- **State** → Current socket state.
- **Recv-Q** → Data waiting to be read.
- **Send-Q** → Data waiting to be transmitted.
- **Local Address** → Local IP address and port.
- **Peer Address** → Remote system connected to the socket.

---

# 🌍 Real-world Use Cases

- Checking whether a web server is listening on port 80 or 443
- Finding which application is using a specific port
- Troubleshooting SSH connectivity
- Monitoring active client connections
- Diagnosing networking issues on production servers

---

# 🧠 How It Works

`ss` reads socket information directly from the Linux kernel using the Netlink interface.

Unlike `netstat`, which parses multiple system files, `ss` retrieves information more efficiently, making it significantly faster on systems with many active connections.

---

# ⚠️ Common Mistakes

❌ Forgetting `sudo` when using `-p`.

Without sufficient privileges, process information may not be displayed.

---

❌ Confusing listening sockets with active connections.

Listening sockets wait for incoming connections, while established sockets represent active communication.

---

❌ Forgetting `-n`.

Without `-n`, `ss` performs DNS lookups, which can slow down output.

---

# ✅ Best Practices

- Use `ss -tuln` to quickly check open ports.
- Add `-p` when troubleshooting services.
- Use `-n` to avoid unnecessary hostname resolution.
- Prefer `ss` over `netstat` on modern Linux systems.

---

# 🔒 Security Considerations

Running:

```bash
sudo ss -tulpn
```

reveals which services are listening on the system.

Administrators should regularly audit listening ports and disable unnecessary services to reduce the attack surface.

---

# 🚀 Performance Notes

`ss` is significantly faster than `netstat`, especially on servers with thousands of active connections.

Its direct communication with the kernel minimizes overhead and improves scalability.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `netstat` | Legacy network statistics tool |
| `ip` | Configure and inspect network interfaces |
| `ping` | Test network connectivity |
| `lsof` | Show which process is using a file or network port |
| `systemctl` | Manage network-related services |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `ss` | Modern socket inspection tool |
| `netstat` | Older, slower networking utility |
| `lsof -i` | Shows processes using network ports |

---

# 🧪 Practice Exercises

### Beginner

Display all listening TCP ports.

---

### Intermediate

Identify which process is listening on port 22.

---

### Advanced

Display all active TCP connections without performing DNS lookups.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `ss` command do?

**A:** It displays network sockets, active connections, and listening ports.

---

### Intermediate

**Q:** Why is `ss` preferred over `netstat`?

**A:** It is faster, more efficient, and communicates directly with the Linux kernel through Netlink.

---

### Advanced

**Q:** Which command would you use to determine which process is listening on port 443?

**A:**

```bash
sudo ss -tulpn
```

Then locate the entry for port `443`.

---

# 🛠 Troubleshooting

**Problem:** Process names are not displayed.

**Cause:** Insufficient permissions.

**Solution:**

Run:

```bash
sudo ss -tulpn
```

---

**Problem:** Expected port is not listed.

**Cause:** The service may not be running or is bound to a different interface.

**Solution:**

- Verify the service status.
- Check firewall configuration.
- Confirm the application's listening address.

---

# 📚 Official Documentation

- `man ss`
- https://man7.org/linux/man-pages/man8/ss.8.html

---

# 📖 Further Reading

- Nexora: `ip`
- Nexora: `netstat`
- Nexora: `ping`
- Linux Networking Fundamentals

---

# 📌 Quick Summary

- `ss` displays socket and network connection information.
- It is the modern replacement for `netstat`.
- Use `ss -tuln` to view listening ports.
- Use `sudo ss -tulpn` to identify which process owns each port.
- It is fast, efficient, and widely used for network troubleshooting.

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