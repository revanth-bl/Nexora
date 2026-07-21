# Networking Commands

> Learn the essential Linux networking commands used to diagnose, monitor, troubleshoot, and manage network connectivity.

---

# 📖 Overview

Networking is one of the core areas of Linux administration. Whether you're checking internet connectivity, transferring files between servers, inspecting network interfaces, or troubleshooting communication issues, Linux provides a rich set of command-line tools.

This section covers the most commonly used networking commands, from beginner-friendly utilities like `ping` to advanced tools such as `ss` and `rsync`.

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Understand basic network communication
- Diagnose connectivity problems
- Inspect network interfaces
- Transfer files securely between systems
- Monitor network connections
- Download resources from the internet
- Troubleshoot routing and latency issues
- Use common Linux networking tools confidently

---

# 📚 Commands Covered

| Command | Purpose |
|----------|---------|
| `ping` | Test network connectivity and latency |
| `traceroute` | Display the path packets take across a network |
| `curl` | Transfer data from or to servers using URLs |
| `wget` | Download files from the web |
| `ssh` | Secure remote login |
| `scp` | Securely copy files between systems |
| `rsync` | Synchronize files and directories efficiently |
| `ip` | Configure and inspect network interfaces |
| `ss` | Display active network sockets and connections |
| `netstat` | Display network statistics and connections (legacy) |
| `hostname` | Display or change the system hostname |

---

# 📈 Learning Path

Recommended order:

1. `ping`
2. `hostname`
3. `ip`
4. `traceroute`
5. `curl`
6. `wget`
7. `ssh`
8. `scp`
9. `rsync`
10. `ss`
11. `netstat`

---

# 🌍 Real-world Applications

These commands are used daily by:

- Linux System Administrators
- DevOps Engineers
- Cloud Engineers
- Site Reliability Engineers (SREs)
- Cybersecurity Professionals
- Network Engineers
- Backend Developers

Common tasks include:

- Verifying server availability
- Troubleshooting network outages
- Downloading software packages
- Managing remote Linux servers
- Copying files securely
- Monitoring active network connections
- Diagnosing DNS and routing issues

---

# ⚠️ Best Practices

- Prefer `ip` over older networking tools like `ifconfig`.
- Prefer `ss` over `netstat` for modern Linux systems.
- Use SSH key authentication instead of passwords whenever possible.
- Verify connectivity with `ping` before investigating application-level issues.
- Avoid running networking commands with unnecessary root privileges.

---

# 🔗 Related Topics

- Linux File Management
- Linux Permissions
- Linux Process Management
- Shell Scripting
- Linux System Services
- Networking Fundamentals

---

# 🚀 What's Next?

After completing the Networking section, continue with:

- Process Management
- System Services
- Permissions
- Shell Scripting

These topics build on networking knowledge and are essential for Linux administration.

---

Happy learning! 🚀