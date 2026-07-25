# Monitoring

## Overview

Monitoring is the continuous process of observing the health, performance, availability, and security of systems, applications, and networks. Effective monitoring enables administrators to detect issues early, maintain system reliability, optimize performance, and respond quickly to incidents.

Linux provides numerous built-in tools for monitoring system resources, while enterprise environments often use centralized monitoring platforms.

---

# Why Monitoring is Important

Monitoring helps organizations:

- Detect failures early
- Improve system availability
- Identify performance bottlenecks
- Ensure resource utilization remains healthy
- Enhance security
- Support troubleshooting
- Reduce downtime
- Improve capacity planning

---

# Key Monitoring Areas

- CPU Usage
- Memory Usage
- Disk Usage
- Disk I/O
- Network Activity
- Running Processes
- Services
- Logs
- System Load
- Hardware Health

---

# Monitoring Workflow

```text
Collect Metrics
        │
        ▼
Analyze Data
        │
        ▼
Generate Alerts
        │
        ▼
Investigate Issues
        │
        ▼
Resolve Problems
        │
        ▼
Continuous Monitoring
```

---

# CPU Monitoring

View CPU usage:

```bash
top
```

Interactive process viewer:

```bash
htop
```

CPU statistics:

```bash
mpstat
```

Example:

```bash
mpstat 2
```

Displays CPU statistics every two seconds.

---

# Memory Monitoring

View memory usage:

```bash
free -h
```

Example output:

```text
              total   used   free
Mem:           16Gi   8Gi    6Gi
```

Monitor memory continuously:

```bash
watch free -h
```

---

# Disk Monitoring

Check disk space:

```bash
df -h
```

Check directory size:

```bash
du -sh /home/user
```

Monitor disk I/O:

```bash
iostat
```

---

# Process Monitoring

View running processes:

```bash
ps aux
```

Interactive monitoring:

```bash
top
```

Search for a process:

```bash
pgrep nginx
```

Terminate a process:

```bash
kill PID
```

---

# Network Monitoring

Display network interfaces:

```bash
ip addr
```

View active connections:

```bash
ss -tuln
```

Check connectivity:

```bash
ping google.com
```

View network statistics:

```bash
netstat -i
```

---

# Service Monitoring

Check service status:

```bash
systemctl status nginx
```

List active services:

```bash
systemctl list-units --type=service
```

Restart a service:

```bash
sudo systemctl restart nginx
```

---

# Log Monitoring

View system logs:

```bash
journalctl
```

Follow logs in real time:

```bash
journalctl -f
```

Monitor authentication logs:

```bash
tail -f /var/log/auth.log
```

---

# System Load Monitoring

Display system uptime and load:

```bash
uptime
```

Example:

```text
load average: 0.50, 0.62, 0.71
```

The three numbers represent the average system load over:

- 1 minute
- 5 minutes
- 15 minutes

---

# Hardware Monitoring

View hardware information:

```bash
lscpu
```

Display memory hardware:

```bash
sudo dmidecode -t memory
```

Check storage devices:

```bash
lsblk
```

Monitor SMART disk health:

```bash
smartctl -H /dev/sda
```

---

# Common Monitoring Tools

| Tool | Purpose |
|------|---------|
| top | Process monitoring |
| htop | Interactive system monitor |
| vmstat | Virtual memory statistics |
| iostat | Disk I/O statistics |
| mpstat | CPU statistics |
| sar | Historical performance data |
| free | Memory usage |
| df | Disk usage |
| du | Directory size |
| journalctl | System logs |
| ss | Network connections |
| lsof | Open files and ports |

---

# Enterprise Monitoring Solutions

| Tool | Purpose |
|------|---------|
| Prometheus | Metrics collection |
| Grafana | Visualization dashboards |
| Nagios | Infrastructure monitoring |
| Zabbix | Enterprise monitoring |
| Icinga | Network and system monitoring |
| Datadog | Cloud monitoring |
| New Relic | Application performance monitoring |
| Elastic Stack | Monitoring and log analysis |

---

# Alerting

Monitoring systems often generate alerts when:

- CPU usage exceeds a threshold
- Memory usage is high
- Disk space is low
- Services stop unexpectedly
- Network connectivity fails
- Security events occur

Alerts may be sent through:

- Email
- SMS
- Slack
- Microsoft Teams
- PagerDuty
- Webhooks

---

# Best Practices

- Monitor critical services continuously.
- Configure meaningful alert thresholds.
- Avoid excessive alerts to reduce alert fatigue.
- Monitor trends instead of isolated metrics.
- Combine metrics with log analysis.
- Rotate and archive logs regularly.
- Use dashboards for visualization.
- Review monitoring data periodically.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Monitoring only CPU | Monitor all critical resources |
| Ignoring historical data | Analyze trends over time |
| Setting unrealistic alerts | Use practical thresholds |
| Not monitoring logs | Include log analysis |
| Delayed response to alerts | Establish incident response procedures |

---

# Real-World Examples

- Monitoring a web server's uptime
- Detecting high CPU usage on a database server
- Alerting when disk space drops below 10%
- Tracking application response times
- Monitoring Kubernetes clusters
- Observing cloud infrastructure health
- Detecting unauthorized login attempts
- Monitoring network latency

---

# Summary

Monitoring is an essential practice for maintaining reliable, secure, and high-performing Linux systems. By continuously tracking system metrics, logs, services, and hardware health, administrators can detect problems early, optimize performance, and ensure system availability through proactive maintenance.

---

# Related Topics

- Logging
- Automation
- Performance Optimization
- System Administration
- Troubleshooting
- Security
- DevOps
- Prometheus
- Grafana
- Observability