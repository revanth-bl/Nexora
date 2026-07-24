# Logging Best Practices

## Overview

Logging is essential for monitoring system activity, troubleshooting issues, auditing security events, and understanding application behavior. Effective logging practices help administrators quickly identify problems, improve system reliability, and maintain security.

This guide covers best practices for managing logs on Linux systems.

---

# Why Logging Matters

Good logging helps you:

- Troubleshoot system and application issues
- Monitor system health
- Detect security incidents
- Audit user activity
- Analyze performance
- Meet compliance and auditing requirements

---

# 1. Centralize Log Storage

Store logs in standard locations rather than scattering them across the filesystem.

Common log directory:

```text
/var/log
```

Examples:

```text
/var/log/syslog
/var/log/messages
/var/log/auth.log
/var/log/kern.log
```

Centralized logs simplify monitoring and troubleshooting.

---

# 2. Use System Logging Services

Modern Linux distributions use **systemd-journald** for collecting system logs.

Some systems also use:

- rsyslog
- syslog-ng

View system logs:

```bash
journalctl
```

---

# 3. Monitor Logs Regularly

Review logs frequently to identify:

- Failed logins
- Service failures
- Hardware errors
- Disk issues
- Security alerts

Example:

```bash
journalctl -b
```

View authentication logs:

```bash
sudo journalctl -u ssh
```

---

# 4. Use Appropriate Log Levels

Applications should categorize messages by importance.

Common log levels:

| Level | Purpose |
|--------|---------|
| DEBUG | Detailed debugging information |
| INFO | General operational messages |
| NOTICE | Significant but normal events |
| WARNING | Potential issues |
| ERROR | Recoverable errors |
| CRITICAL | Serious failures |
| ALERT | Immediate administrator attention required |
| EMERGENCY | System is unusable |

Avoid excessive logging at high severity levels.

---

# 5. Rotate Log Files

Log files continuously grow over time.

Use **logrotate** to:

- Rotate logs
- Compress old logs
- Delete outdated logs
- Prevent disks from filling up

Check logrotate configuration:

```bash
cat /etc/logrotate.conf
```

---

# 6. Keep Log Files Secure

Logs often contain sensitive information such as:

- Usernames
- IP addresses
- Error messages
- Authentication events

Protect them with appropriate permissions.

Check permissions:

```bash
ls -l /var/log
```

---

# 7. Avoid Logging Sensitive Information

Do **not** log:

- Passwords
- API keys
- Tokens
- Private keys
- Credit card information
- Personal data unless required

Sensitive information in logs creates security risks.

---

# 8. Use Meaningful Log Messages

Good log message:

```text
Database connection failed: timeout after 30 seconds.
```

Poor log message:

```text
Something went wrong.
```

Include enough context to identify the problem quickly.

---

# 9. Include Timestamps

Every log entry should include the time the event occurred.

Example:

```text
2026-07-24 10:42:15 INFO SSH login successful for user alice
```

Accurate timestamps help reconstruct events.

---

# 10. Monitor Disk Usage

Large log files can consume significant storage.

Check filesystem usage:

```bash
df -h
```

Check log directory size:

```bash
du -sh /var/log
```

---

# 11. Search Logs Efficiently

Use command-line tools to filter logs.

Examples:

```bash
grep ERROR /var/log/syslog
```

```bash
journalctl | grep ssh
```

```bash
journalctl -p err
```

Efficient searching speeds up troubleshooting.

---

# 12. Archive Old Logs

Instead of deleting logs immediately:

- Compress old logs
- Archive them securely
- Retain them according to organizational policies

Common formats:

- `.gz`
- `.xz`

---

# 13. Monitor Services

Check service logs individually.

Example:

```bash
journalctl -u nginx
```

```bash
journalctl -u ssh
```

```bash
journalctl -u docker
```

This isolates issues with specific services.

---

# 14. Use Real-Time Log Monitoring

Monitor logs as they are written.

Example:

```bash
tail -f /var/log/syslog
```

For journal logs:

```bash
journalctl -f
```

Useful during troubleshooting.

---

# 15. Regularly Review Authentication Logs

Authentication logs help detect:

- Failed login attempts
- Brute-force attacks
- Unauthorized access
- Privilege escalation

Examples:

```bash
journalctl -u ssh
```

or

```bash
cat /var/log/auth.log
```

(Location may vary by distribution.)

---

# Common Commands

View all logs:

```bash
journalctl
```

View current boot logs:

```bash
journalctl -b
```

Follow logs in real time:

```bash
journalctl -f
```

View logs for a service:

```bash
journalctl -u nginx
```

View error messages:

```bash
journalctl -p err
```

View kernel logs:

```bash
journalctl -k
```

Monitor a log file:

```bash
tail -f /var/log/syslog
```

Search log entries:

```bash
grep ERROR /var/log/syslog
```

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Never reviewing logs | Monitor logs regularly |
| Logging sensitive information | Exclude confidential data |
| Ignoring log growth | Configure log rotation |
| Using vague messages | Write descriptive logs |
| Deleting logs immediately | Archive important logs |
| Weak permissions | Restrict access to log files |

---

# Best Practices Checklist

- Store logs in standard locations.
- Use `systemd-journald` or another logging service.
- Review logs regularly.
- Configure log rotation.
- Protect log files with proper permissions.
- Never log sensitive information.
- Include timestamps and meaningful messages.
- Monitor log storage usage.
- Archive important logs.
- Use `journalctl`, `grep`, and `tail` for analysis.

---

# Key Takeaways

- Logging is essential for troubleshooting, monitoring, and security.
- Linux primarily uses `systemd-journald` and, in some cases, `rsyslog` to manage logs.
- Regular log review, secure storage, and log rotation help maintain a healthy system.
- Well-structured logs make diagnosing problems significantly easier.

---

## Related Topics

- System Startup
- System Services
- Troubleshooting
- Security
- Performance
- Journalctl
- Logrotate
```