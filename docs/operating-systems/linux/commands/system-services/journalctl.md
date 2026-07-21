# journalctl

> View, search, and manage system logs collected by the systemd journal.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | System Services |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`journalctl` is a command-line utility used to view and query logs collected by **systemd-journald**. It provides centralized logging for the Linux system, including kernel messages, services, applications, and system events.

Unlike traditional log files stored in `/var/log`, `journalctl` offers powerful filtering options based on time, service, priority, boot sessions, and more.

- **What does it do?** Displays and filters logs stored in the systemd journal.
- **Why does it exist?** To provide centralized and structured system logging.
- **When is it commonly used?** Troubleshooting services, debugging boot issues, and monitoring system activity.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- View system logs
- Filter logs by service
- Display logs from the current boot
- Follow logs in real time
- Filter logs by time and priority

---

# ⚙️ Syntax

```bash
journalctl [OPTIONS]
```

---

# 📝 Parameters

`journalctl` does not require positional parameters.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-b` | Show logs from the current boot |
| `-u SERVICE` | Show logs for a specific systemd service |
| `-f` | Follow logs in real time (similar to `tail -f`) |
| `-n N` | Display the last N log entries |
| `-p LEVEL` | Filter by log priority |
| `--since TIME` | Show logs after a specific time |
| `--until TIME` | Show logs before a specific time |
| `-k` | Display kernel logs only |
| `--disk-usage` | Show journal disk usage |

---

# 💻 Basic Examples

## Example 1

```bash
journalctl
```

Display all available journal logs.

---

## Example 2

```bash
journalctl -b
```

Display logs from the current boot.

---

## Example 3

```bash
journalctl -u ssh
```

Display logs for the SSH service.

---

## Example 4

```bash
journalctl -f
```

Follow new log entries in real time.

---

## Example 5

```bash
journalctl --since "1 hour ago"
```

Display logs from the last hour.

---

## Example 6

```bash
journalctl -p err
```

Display only error-level log messages.

---

# 📤 Example Output

```text
Jul 09 10:45:12 server systemd[1]: Started OpenSSH Server.
Jul 09 10:45:14 sshd[1024]: Accepted publickey for revanth.
Jul 09 10:46:30 systemd[1]: Started Docker Application Container Engine.
```

---

# 🌍 Real-world Use Cases

- Debugging failed system services
- Investigating boot failures
- Monitoring SSH login attempts
- Viewing application logs
- Checking kernel events
- Troubleshooting server issues

---

# 🧠 How It Works

`systemd-journald` collects logs from multiple sources, including:

- Kernel messages
- System services
- Applications
- Standard output and error streams
- Boot events

`journalctl` reads and filters this centralized journal, making it easier to analyze logs than searching multiple log files.

---

# ⚠️ Common Mistakes

❌ Forgetting that some logs require root privileges.

Use:

```bash
sudo journalctl
```

for complete access.

---

❌ Viewing every log without filters.

Instead, narrow the output using:

```bash
journalctl -u nginx
```

or

```bash
journalctl --since today
```

---

❌ Confusing journal logs with traditional log files.

Not every application writes directly to `/var/log`; many use the systemd journal.

---

# ✅ Best Practices

- Filter logs by service using `-u`.
- Use `-b` when troubleshooting boot problems.
- Use `-f` for live monitoring.
- Combine time filters with service filters for faster debugging.
- Archive or vacuum old journals if disk usage becomes excessive.

---

# 🔒 Security Considerations

System logs may contain:

- Usernames
- IP addresses
- Service failures
- Authentication attempts
- System configuration details

Restrict access to logs and avoid sharing sensitive information publicly.

---

# 🚀 Performance Notes

Large journals may contain millions of log entries.

Using filters such as:

```bash
journalctl -u nginx
```

or

```bash
journalctl --since today
```

significantly improves query performance.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `systemctl` | Manage systemd services |
| `dmesg` | Display kernel ring buffer |
| `tail` | View the end of log files |
| `less` | Browse log output interactively |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `journalctl` | Reads logs from the systemd journal |
| `dmesg` | Displays kernel messages only |
| `tail` | Reads the end of text log files |
| `cat /var/log/...` | Reads traditional log files |

---

# 🧪 Practice Exercises

### Beginner

Display all journal logs.

---

### Intermediate

View logs for the SSH service.

---

### Advanced

Display only error logs generated during the last 24 hours.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is `journalctl` used for?

**A:** It displays and filters logs stored by the systemd journal.

---

### Intermediate

**Q:** How do you view logs for a specific service?

**A:**

```bash
journalctl -u service_name
```

Example:

```bash
journalctl -u nginx
```

---

### Advanced

**Q:** How would you investigate why a service failed after boot?

**A:** Check the service logs from the current boot:

```bash
journalctl -b -u service_name
```

This shows only logs related to that service during the latest boot session.

---

# 🛠 Troubleshooting

**Problem:** Permission denied when viewing logs.

**Solution:**

```bash
sudo journalctl
```

or add the user to the `systemd-journal` group (distribution-dependent).

---

**Problem:** Too much log output.

**Solution:**

Filter by service, time, or priority:

```bash
journalctl -u docker --since today
```

---

# 📚 Official Documentation

- `man journalctl`
- `man systemd-journald`

---

# 📖 Further Reading

- Nexora: `systemctl`
- Nexora: `dmesg`
- systemd Documentation

---

# 📌 Quick Summary

- `journalctl` displays logs stored by `systemd-journald`.
- Use `-u` to filter logs by service.
- Use `-b` to view logs from the current boot.
- Use `-f` to monitor logs in real time.
- Essential for Linux troubleshooting and system administration.

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