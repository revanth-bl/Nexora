# Logging Patterns

## Overview

Logging patterns are standardized approaches to recording application and system events. Well-designed logging helps developers and system administrators monitor systems, troubleshoot issues, audit activities, and improve application reliability.

A consistent logging strategy makes logs easier to search, analyze, and integrate with monitoring tools.

---

# Why Logging Matters

Logging provides several benefits:

- Detect system errors
- Troubleshoot application issues
- Monitor system health
- Audit user activities
- Improve security
- Track performance
- Support incident response
- Simplify debugging

---

# Common Logging Levels

| Level | Purpose |
|--------|---------|
| TRACE | Detailed diagnostic information |
| DEBUG | Debugging information |
| INFO | General operational messages |
| WARNING | Potential problems |
| ERROR | Recoverable errors |
| CRITICAL | Severe failures requiring immediate attention |

---

# Logging Workflow

```text
Application
      │
      ▼
Generate Log Event
      │
      ▼
Write to Log File
      │
      ▼
Centralized Log Collection
      │
      ▼
Monitoring & Alerting
      │
      ▼
Analysis & Troubleshooting
```

---

# Structured Logging

Instead of plain text:

```text
User logged in
```

Use structured data:

```json
{
  "timestamp": "2026-07-25T10:30:00Z",
  "level": "INFO",
  "user": "alice",
  "action": "login",
  "status": "success"
}
```

Benefits:

- Easy searching
- Machine-readable
- Better analytics
- Integration with monitoring tools

---

# Log Format

A good log entry typically includes:

- Timestamp
- Log level
- Service name
- Process ID
- User or request ID
- Message
- Error details (if applicable)

Example:

```text
2026-07-25 10:30:15 INFO nginx[1234]: Server started successfully
```

---

# Common Log Locations (Linux)

| File | Purpose |
|------|---------|
| `/var/log/syslog` | General system logs |
| `/var/log/messages` | System messages (RHEL/CentOS) |
| `/var/log/auth.log` | Authentication logs |
| `/var/log/kern.log` | Kernel logs |
| `/var/log/dmesg` | Boot messages |
| `/var/log/nginx/` | Nginx logs |
| `/var/log/apache2/` | Apache logs |

---

# Logging Commands

View logs:

```bash
cat /var/log/syslog
```

Follow logs in real time:

```bash
tail -f /var/log/syslog
```

View systemd logs:

```bash
journalctl
```

Follow journal logs:

```bash
journalctl -f
```

View logs for a service:

```bash
journalctl -u nginx
```

---

# Log Rotation

Linux commonly uses **logrotate** to prevent log files from growing indefinitely.

Force log rotation:

```bash
sudo logrotate -f /etc/logrotate.conf
```

Configuration:

```text
/etc/logrotate.conf
```

Benefits:

- Saves disk space
- Prevents oversized log files
- Archives old logs
- Compresses historical logs

---

# Centralized Logging

Centralized logging collects logs from multiple systems into one location.

Popular solutions:

| Tool | Purpose |
|------|---------|
| ELK Stack | Elasticsearch, Logstash, Kibana |
| OpenSearch | Log search and analytics |
| Graylog | Centralized log management |
| Splunk | Enterprise log analysis |
| Fluentd | Log collection |
| Loki | Log aggregation for Grafana |

---

# Security Logging

Monitor events such as:

- Failed login attempts
- Successful logins
- Permission changes
- File modifications
- Firewall activity
- SSH connections
- Sudo usage

Example:

```bash
sudo tail -f /var/log/auth.log
```

---

# Performance Logging

Track metrics including:

- CPU usage
- Memory usage
- Disk I/O
- Network activity
- Request latency
- Database query times

These logs help identify performance bottlenecks.

---

# Logging Best Practices

- Use consistent log levels.
- Include timestamps in every log entry.
- Write meaningful and descriptive messages.
- Avoid logging sensitive information such as passwords or API keys.
- Use structured logging where possible.
- Rotate and archive logs regularly.
- Monitor logs continuously.
- Retain logs according to organizational policies.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Logging everything | Log meaningful events only |
| Logging sensitive data | Mask or omit confidential information |
| Using inconsistent formats | Standardize log structure |
| Ignoring log rotation | Configure automatic rotation |
| Missing timestamps | Include timestamps in every entry |

---

# Real-World Examples

- Monitoring web server requests
- Tracking failed SSH login attempts
- Recording application errors
- Auditing administrator actions
- Debugging production issues
- Monitoring API requests
- Detecting security incidents
- Troubleshooting service failures

---

# Summary

Logging patterns define how applications and systems record operational events. By using consistent log formats, appropriate log levels, centralized collection, and proper log rotation, organizations can improve observability, security, troubleshooting, and overall system reliability.

---

# Related Topics

- Logging
- Monitoring
- Troubleshooting
- System Administration
- Automation
- Security
- DevOps
- Observability
- ELK Stack
- Systemd Journal