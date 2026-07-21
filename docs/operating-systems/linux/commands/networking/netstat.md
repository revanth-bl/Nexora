# netstat

> Display network connections, routing tables, interface statistics, and listening ports.

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

`netstat` (Network Statistics) is a command-line utility used to display active network connections, routing tables, interface statistics, and listening ports. Although it has largely been replaced by the `ss` command on modern Linux systems, it remains widely used and is still available on many distributions.

- **What does it do?** Displays network-related information such as connections, ports, routing tables, and interface statistics.
- **Why does it exist?** To help administrators monitor and troubleshoot network activity.
- **When is it commonly used?** Diagnosing network issues, checking open ports, verifying services, and troubleshooting connectivity.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- View active network connections
- List listening ports
- Display routing tables
- Identify processes using network ports
- Understand when to use `ss` instead

---

# ⚙️ Syntax

```bash
netstat [options]
```

---

# 📝 Parameters

`netstat` does not require positional parameters. Behavior is controlled through command-line options.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-a` | Show all connections and listening ports |
| `-t` | Display TCP connections |
| `-u` | Display UDP connections |
| `-l` | Show only listening sockets |
| `-n` | Show numerical addresses instead of resolving hostnames |
| `-p` | Display the process ID and program name |
| `-r` | Show routing table |
| `-i` | Show network interface statistics |
| `-s` | Show protocol statistics |

---

# 💻 Basic Examples

## Example 1

```bash
netstat -a
```

Displays all active and listening connections.

---

## Example 2

```bash
netstat -tuln
```

Lists all TCP and UDP listening ports without resolving hostnames.

---

## Example 3

```bash
sudo netstat -tulpn
```

Displays listening ports along with the owning processes.

---

## Example 4

```bash
netstat -r
```

Displays the routing table.

---

## Example 5

```bash
netstat -i
```

Displays network interface statistics.

---

# 📤 Example Output

```text
Proto Recv-Q Send-Q Local Address      Foreign Address    State
tcp        0      0 0.0.0.0:22         0.0.0.0:*          LISTEN
tcp        0      0 192.168.1.20:22    192.168.1.15:52344 ESTABLISHED
udp        0      0 0.0.0.0:68         0.0.0.0:*
```

Explanation:

- **Proto** → Network protocol
- **Local Address** → Local IP and port
- **Foreign Address** → Remote IP and port
- **State** → Connection state (LISTEN, ESTABLISHED, etc.)

---

# 🌍 Real-world Use Cases

- Checking if a service is listening on a port
- Identifying applications using specific ports
- Troubleshooting SSH or web server issues
- Viewing routing information
- Monitoring active network connections

---

# 🧠 How It Works

`netstat` reads networking information from the Linux kernel through the `/proc` filesystem. It gathers details about active sockets, routing tables, interfaces, and protocol statistics before displaying them in a human-readable format.

Modern Linux systems recommend using the `ss` command because it is faster and provides more detailed socket information.

---

# ⚠️ Common Mistakes

❌ Assuming `netstat` is installed by default on every Linux distribution.

❌ Forgetting to use `sudo` when viewing process information with `-p`.

❌ Using `netstat` instead of the newer `ss` command on modern systems.

---

# ✅ Best Practices

- Prefer `ss` for modern Linux systems.
- Use `-n` to avoid DNS lookups and improve performance.
- Use `-tulpn` to quickly identify listening services.
- Combine with `grep` to filter results.

Example:

```bash
sudo netstat -tulpn | grep :80
```

---

# 🔒 Security Considerations

Open ports shown by `netstat` may expose running services. Regularly review listening ports to ensure unnecessary services are not accessible.

Avoid sharing outputs containing internal IP addresses or sensitive service information publicly.

---

# 🚀 Performance Notes

`netstat` is slower than `ss` because it parses information from the `/proc` filesystem and performs additional processing. For systems with many connections, `ss` provides better performance.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `ss` | Modern replacement for `netstat` |
| `ip` | Manage network interfaces and routes |
| `ping` | Test network connectivity |
| `traceroute` | Trace packet paths |
| `lsof` | Display files and ports opened by processes |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `netstat` | Legacy networking utility |
| `ss` | Modern, faster socket statistics tool |
| `lsof` | Shows processes using files and network ports |

---

# 🧪 Practice Exercises

### Beginner

Display all active network connections.

---

### Intermediate

Identify which process is listening on port 22.

---

### Advanced

Display the routing table and explain the default gateway entry.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `netstat` command do?

**A:** It displays network connections, listening ports, routing tables, and network statistics.

---

### Intermediate

**Q:** Why is `ss` preferred over `netstat`?

**A:** `ss` is faster, actively maintained, and provides more detailed socket information.

---

### Advanced

**Q:** Which command would you use to identify the process listening on port 443?

**A:** Use:

```bash
sudo netstat -tulpn | grep :443
```

or preferably:

```bash
sudo ss -tulpn | grep :443
```

---

# 🛠 Troubleshooting

**Problem:** `netstat: command not found`

**Cause:** The `net-tools` package is not installed.

**Solution:**

Ubuntu/Debian:

```bash
sudo apt install net-tools
```

RHEL/CentOS:

```bash
sudo yum install net-tools
```

Verify installation:

```bash
netstat --version
```

---

# 📚 Official Documentation

- `man netstat`
- `man ss`
- https://man7.org/linux/man-pages/

---

# 📖 Further Reading

- Nexora: `ss`
- Nexora: `ip`
- Nexora: `ping`
- Linux Networking Fundamentals

---

# 📌 Quick Summary

- `netstat` displays network connections and routing information.
- Commonly used to inspect listening ports and active connections.
- Has been largely replaced by the faster `ss` command.
- Still useful on many Linux systems for network troubleshooting.

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