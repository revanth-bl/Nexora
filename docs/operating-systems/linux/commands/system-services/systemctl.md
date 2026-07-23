# systemctl

> Manage systemd services, units, and the overall Linux system.

> **Note:** `systemctl` is the primary command for managing services on modern Linux distributions that use **systemd**.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | System Services |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 9 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`systemctl` is the command-line utility used to interact with **systemd**, the init system responsible for starting, stopping, enabling, and monitoring services on most modern Linux distributions.

Besides managing services, `systemctl` can control system targets, reboot or shut down the system, and inspect the status of various system components.

- **What does it do?** Manages systemd services and units.
- **Why does it exist?** To provide centralized control over system services and boot processes.
- **When is it commonly used?** Starting services, enabling services at boot, troubleshooting failures, and administering Linux servers.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Start and stop services
- Restart and reload services
- Enable services at boot
- Disable services
- View service status
- List running services
- Understand systemd units

---

# ⚙️ Syntax

```bash
systemctl [OPTIONS] COMMAND [UNIT]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `COMMAND` | Action to perform | Yes |
| `UNIT` | Service or unit name | Usually |

---

# 🔧 Common Commands

| Command | Description |
|---------|-------------|
| `start` | Start a service |
| `stop` | Stop a service |
| `restart` | Restart a service |
| `reload` | Reload configuration |
| `status` | Show service status |
| `enable` | Enable service at boot |
| `disable` | Disable service at boot |
| `is-active` | Check whether a service is running |
| `is-enabled` | Check whether a service starts automatically |
| `list-units` | List active units |
| `list-unit-files` | List installed unit files |

---

# 💻 Basic Examples

## Example 1

Start the SSH service.

```bash
sudo systemctl start ssh
```

---

## Example 2

Stop a service.

```bash
sudo systemctl stop nginx
```

---

## Example 3

Restart Apache.

```bash
sudo systemctl restart apache2
```

---

## Example 4

Check service status.

```bash
systemctl status docker
```

---

## Example 5

Enable a service at boot.

```bash
sudo systemctl enable nginx
```

---

## Example 6

Disable a service.

```bash
sudo systemctl disable nginx
```

---

## Example 7

Check if a service is active.

```bash
systemctl is-active ssh
```

---

## Example 8

List running services.

```bash
systemctl list-units --type=service
```

---

# 📤 Example Output

```text
$ systemctl status ssh

● ssh.service - OpenSSH Server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled)
     Active: active (running)
       Docs: man:sshd(8)
   Main PID: 821
      Tasks: 1
```

---

# 🌍 Real-world Use Cases

- Managing web servers (Apache, Nginx)
- Managing database servers (MySQL, PostgreSQL)
- Starting Docker services
- Troubleshooting failed services
- Configuring automatic service startup
- Managing production Linux servers

---

# 🧠 How It Works

`systemctl` communicates with **systemd**, which manages system resources through **units**.

Common unit types include:

- `.service` — Background services
- `.socket` — Socket activation
- `.target` — Groups of units (similar to runlevels)
- `.mount` — Mounted filesystems
- `.timer` — Scheduled tasks

Example:

```text
systemctl
      │
      ▼
systemd
      │
      ▼
Service Units
```

---

# ⚠️ Common Mistakes

❌ Forgetting `sudo`.

Administrative actions require root privileges.

---

❌ Using `restart` instead of `reload`.

Restart:

```text
Stop → Start
```

Reload:

```text
Reload configuration only
```

---

❌ Forgetting to enable a service after installation.

A running service may not automatically start after reboot unless enabled.

---

# ✅ Best Practices

- Use `status` before troubleshooting.
- Use `enable` for services that should start automatically.
- Prefer `reload` when only configuration changes.
- Review logs with `journalctl` after service failures.
- Learn common service names used by your distribution.

---

# 🔒 Security Considerations

Only administrators should manage critical services.

Stopping essential services may disconnect users or interrupt applications.

Always verify the service name before executing commands.

---

# 🚀 Performance Notes

`systemctl` itself is lightweight.

Restarting services may briefly interrupt applications, while `reload` often avoids downtime.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `service` | Legacy service manager |
| `journalctl` | View service logs |
| `ps` | View running processes |
| `top` | Monitor processes |
| `kill` | Terminate processes |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `systemctl` | Complete systemd service management |
| `service` | Compatibility wrapper for service management |
| `journalctl` | Displays logs |
| `ps` | Lists processes |

---

# 🧪 Practice Exercises

### Beginner

Start the SSH service.

---

### Intermediate

Enable Docker so it starts automatically after reboot.

---

### Advanced

Find a failed service and inspect its logs using both `systemctl` and `journalctl`.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is `systemctl`?

**A:** It is the command-line utility used to manage services and other systemd units on modern Linux systems.

---

### Intermediate

**Q:** What is the difference between `enable` and `start`?

**A:**

- `start` starts the service immediately.
- `enable` configures the service to start automatically during system boot.

---

### Advanced

**Q:** How would you troubleshoot a service that fails to start?

**A:**

1. Check its status:

```bash
systemctl status service_name
```

2. Review its logs:

```bash
journalctl -u service_name
```

3. Verify the configuration and restart the service after fixing any issues.

---

# 🛠 Troubleshooting

**Problem:** Service failed to start.

**Solution:**

Check its status:

```bash
systemctl status service_name
```

Then inspect the logs:

```bash
journalctl -u service_name
```

---

**Problem:** Service doesn't start after reboot.

**Solution:**

Enable it:

```bash
sudo systemctl enable service_name
```

Verify:

```bash
systemctl is-enabled service_name
```

---

# 📚 Official Documentation

- `man systemctl`
- `man systemd`

---

# 📖 Further Reading

- Nexora: `journalctl`
- Nexora: `service`
- systemd Documentation
- Linux Foundation Documentation

---

# 📌 Quick Summary

- `systemctl` is the primary tool for managing systemd services.
- Use `start`, `stop`, `restart`, and `status` for service management.
- Use `enable` and `disable` to control startup behavior.
- Combine `systemctl` with `journalctl` for effective troubleshooting.
- It is one of the most important commands for Linux administration.

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