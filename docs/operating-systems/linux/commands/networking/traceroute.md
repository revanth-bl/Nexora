# traceroute

> Trace the path that network packets take from your computer to a remote destination.

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

`traceroute` is a network diagnostic utility that shows the route packets take through the network to reach a destination. It displays each intermediate router (hop) along the path and the time taken to reach it.

Network administrators use `traceroute` to identify routing problems, network latency, and packet loss between systems.

- **What does it do?** Displays the network path to a destination.
- **Why does it exist?** To help diagnose routing and connectivity issues.
- **When is it commonly used?** Troubleshooting slow networks, unreachable hosts, routing loops, and ISP problems.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Trace the route to a remote host
- Interpret hop information
- Measure network latency
- Troubleshoot routing issues
- Use common traceroute options

---

# ⚙️ Syntax

```bash
traceroute [options] destination
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `destination` | Hostname or IP address to trace | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-n` | Display numeric IP addresses instead of resolving hostnames |
| `-I` | Use ICMP Echo Requests instead of UDP packets |
| `-T` | Use TCP SYN packets |
| `-m <hops>` | Set the maximum number of hops |
| `-q <count>` | Number of probes sent per hop |
| `-w <seconds>` | Wait time before timing out |

---

# 💻 Basic Examples

## Example 1

```bash
traceroute google.com
```

Trace the network path to Google.

---

## Example 2

```bash
traceroute 8.8.8.8
```

Trace the route using an IP address.

---

## Example 3

```bash
traceroute -n google.com
```

Display numeric IP addresses without DNS lookups.

---

## Example 4

```bash
traceroute -I google.com
```

Use ICMP packets instead of the default UDP packets.

---

## Example 5

```bash
traceroute -m 20 example.com
```

Limit the trace to a maximum of 20 hops.

---

# 📤 Example Output

```text
traceroute to google.com (142.250.190.78), 30 hops max

1  192.168.1.1      1.2 ms  1.0 ms  1.1 ms
2  10.10.0.1        8.5 ms  8.2 ms  8.3 ms
3  172.16.5.2      15.1 ms 15.0 ms 15.2 ms
4  142.250.190.78  24.3 ms 24.1 ms 24.2 ms
```

Explanation:

- Column 1 → Hop number
- Column 2 → Router IP address or hostname
- Remaining columns → Round-trip time for each probe

---

# 🌍 Real-world Use Cases

- Diagnosing slow internet connections
- Identifying where packet loss occurs
- Troubleshooting cloud server connectivity
- Verifying routing between data centers
- Debugging VPN and ISP routing problems

---

# 🧠 How It Works

`traceroute` sends packets with gradually increasing **Time-To-Live (TTL)** values.

Each router decreases the TTL by one.

When the TTL reaches zero, the router sends back an **ICMP Time Exceeded** message, allowing `traceroute` to identify that hop.

This process repeats until the destination is reached.

---

# ⚠️ Common Mistakes

❌ Assuming `* * *` always indicates a network problem.

Some routers intentionally ignore traceroute requests for security reasons.

---

❌ Confusing latency with bandwidth.

High latency does not necessarily mean low bandwidth.

---

❌ Running traceroute only once.

Network routes may change dynamically, so multiple tests can provide a more accurate picture.

---

# ✅ Best Practices

- Use `-n` to speed up output by skipping DNS lookups.
- Run multiple traces if investigating intermittent issues.
- Compare traces from different locations when diagnosing routing problems.
- Use alongside `ping` for complete network diagnostics.

---

# 🔒 Security Considerations

Some firewalls block traceroute packets, causing incomplete results.

Administrators may intentionally disable ICMP responses to reduce network reconnaissance opportunities.

---

# 🚀 Performance Notes

`traceroute` generates only a small amount of network traffic.

DNS lookups can significantly slow execution; using `-n` improves speed.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `ping` | Tests connectivity |
| `tracepath` | Similar utility without root privileges |
| `ss` | Displays active network sockets |
| `ip` | Displays routing tables and interfaces |
| `netstat` | Legacy networking utility |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `ping` | Tests connectivity only |
| `traceroute` | Shows the complete network path |
| `tracepath` | Similar but simpler and often requires fewer privileges |

---

# 🧪 Practice Exercises

### Beginner

Trace the route to `google.com`.

---

### Intermediate

Trace the route to `8.8.8.8` using numeric IP addresses only.

---

### Advanced

Compare the routes to two different websites and identify where they diverge.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does `traceroute` do?

**A:** It displays the network path packets take from the local machine to a destination.

---

### Intermediate

**Q:** What is the purpose of the TTL value in `traceroute`?

**A:** TTL limits packet lifetime. `traceroute` increases the TTL one hop at a time to discover each router along the path.

---

### Advanced

**Q:** Why might `traceroute` display `* * *` for some hops?

**A:** Some routers block or ignore traceroute probes, rate-limit ICMP responses, or filter packets through firewall rules.

---

# 🛠 Troubleshooting

**Problem:** Every hop shows `* * *`.

**Cause:**

- Firewall blocking traceroute packets
- Network filtering
- Destination blocking probes

**Solution:**

- Try `traceroute -I`
- Test connectivity with `ping`
- Verify firewall rules

---

**Problem:** Trace stops before reaching the destination.

**Cause:**

Intermediate routers may block responses or the destination may be unreachable.

**Solution:**

Run the trace again or test from another network.

---

# 📚 Official Documentation

- `man traceroute`
- https://linux.die.net/man/8/traceroute

---

# 📖 Further Reading

- Nexora: `ping`
- Nexora: `ip`
- Nexora: `ss`
- Linux Networking Fundamentals

---

# 📌 Quick Summary

- `traceroute` shows the network path to a destination.
- Uses increasing TTL values to discover routers.
- Helps diagnose routing issues and latency.
- `-n` skips DNS lookups for faster output.
- Commonly used with `ping` during network troubleshooting.

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