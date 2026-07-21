# ip

> Display and manage network interfaces, IP addresses, routes, and network configuration.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`ip` is the modern Linux networking utility provided by the **iproute2** package. It replaces legacy tools such as `ifconfig`, `route`, and `arp`, offering a unified interface for configuring and troubleshooting networking.

- **What does it do?** Displays and manages network interfaces, IP addresses, routing tables, and neighboring devices.
- **Why does it exist?** To provide a powerful and consistent replacement for older networking utilities.
- **When is it commonly used?** Network troubleshooting, cloud computing, server administration, container networking, and DevOps automation.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display IP addresses
- View network interfaces
- Inspect routing tables
- Enable or disable network interfaces
- Understand why `ip` replaced `ifconfig`

---

# ⚙️ Syntax

```bash
ip [OPTIONS] OBJECT COMMAND
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `OBJECT` | Network object (`addr`, `link`, `route`, `neigh`, etc.) | Yes |
| `COMMAND` | Action to perform | Yes |

---

# 🔧 Common Objects

| Object | Description |
|---------|-------------|
| `addr` | Manage IP addresses |
| `link` | Manage network interfaces |
| `route` | Manage routing tables |
| `neigh` | Display ARP/Neighbor cache |
| `rule` | Display routing rules |
| `tunnel` | Configure network tunnels |

---

# 💻 Basic Examples

## Example 1

```bash
ip addr
```

Displays all network interfaces and their assigned IP addresses.

---

## Example 2

```bash
ip link
```

Lists all available network interfaces.

---

## Example 3

```bash
ip route
```

Displays the system routing table.

---

## Example 4

```bash
ip addr show eth0
```

Shows IP information for the `eth0` interface.

---

## Example 5

```bash
sudo ip link set eth0 down
```

Temporarily disables the network interface.

---

## Example 6

```bash
sudo ip link set eth0 up
```

Re-enables the network interface.

---

# 📤 Example Output

```text
$ ip addr

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.1.25/24
    inet6 fe80::1a2b:3c4d:5e6f/64
```

Explanation:

- `eth0` → Network interface
- `UP` → Interface is active
- `inet` → IPv4 address
- `inet6` → IPv6 address

---

# 🌍 Real-world Use Cases

- Checking a server's IP address
- Troubleshooting network issues
- Viewing routing information
- Managing cloud instances
- Configuring Docker or Kubernetes networking
- Diagnosing interface problems

---

# 🧠 How It Works

The `ip` command communicates directly with the Linux kernel through the **Netlink** interface. It retrieves or modifies networking information such as interfaces, addresses, routing tables, and neighbors without relying on deprecated networking utilities.

Unlike older commands, `ip` groups networking functionality into objects like `addr`, `link`, and `route`, making administration more organized and extensible.

---

# ⚠️ Common Mistakes

❌ Using deprecated commands like `ifconfig` on modern systems.

❌ Bringing down the wrong interface while connected through SSH.

❌ Forgetting to use `sudo` when modifying network settings.

❌ Assuming interface names are always `eth0` (modern systems often use names like `ens33`, `enp0s3`, or `wlp2s0`).

---

# ✅ Best Practices

- Prefer `ip` over legacy networking commands.
- Verify interface names before making changes.
- Use `ip addr` to inspect addresses.
- Use `ip route` to troubleshoot routing issues.
- Test configuration changes carefully on remote servers.

---

# 🔒 Security Considerations

Changing network interfaces or routing tables can disconnect a remote system. Always verify commands before running them on production servers, especially over SSH.

Avoid exposing internal IP addresses when sharing logs or screenshots publicly.

---

# 🚀 Performance Notes

`ip` is lightweight and communicates efficiently with the Linux kernel. It is suitable for both interactive administration and automation scripts.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `hostname` | Display system hostname |
| `ping` | Test connectivity |
| `ss` | Display socket information |
| `netstat` | Legacy networking utility |
| `traceroute` | Trace packet routes |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `ip` | Modern networking management tool |
| `ifconfig` | Legacy interface management |
| `route` | Legacy routing management |

---

# 🧪 Practice Exercises

### Beginner

Display all IP addresses configured on your system.

---

### Intermediate

Display the routing table and identify the default gateway.

---

### Advanced

Temporarily disable a network interface and then bring it back online.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `ip` command?

**A:** It displays and manages network interfaces, IP addresses, routing tables, and other networking information.

---

### Intermediate

**Q:** Why is `ip` preferred over `ifconfig`?

**A:** `ip` is actively maintained, supports modern networking features, and replaces several legacy networking utilities with a single command.

---

### Advanced

**Q:** What is the Netlink interface?

**A:** Netlink is the communication interface between user-space networking tools (such as `ip`) and the Linux kernel, allowing networking information to be queried and modified efficiently.

---

# 🛠 Troubleshooting

**Problem:** `ip: command not found`

**Cause:** The `iproute2` package is missing.

**Solution:**

Ubuntu/Debian:

```bash
sudo apt install iproute2
```

RHEL/CentOS:

```bash
sudo yum install iproute
```

Verify installation:

```bash
ip --version
```

---

# 📚 Official Documentation

- `man ip`
- `man ip-address`
- `man ip-route`
- https://man7.org/linux/man-pages/man8/ip.8.html

---

# 📖 Further Reading

- Nexora: `ping`
- Nexora: `hostname`
- Nexora: `ss`
- Nexora: Linux Networking Fundamentals

---

# 📌 Quick Summary

- `ip` is the modern Linux networking utility.
- Replaces `ifconfig`, `route`, and `arp`.
- Manages interfaces, addresses, routes, and neighbors.
- Essential for Linux administrators, DevOps engineers, and cloud professionals.

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