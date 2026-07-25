# Process Management Cheat Sheet

## Overview

Process management is the practice of monitoring, controlling, and managing running programs (processes) in Linux. This cheat sheet covers the essential commands used to view, monitor, start, stop, and prioritize processes.

---

# View Running Processes

| Command | Description |
|----------|-------------|
| `ps` | Display current processes |
| `ps -e` | Show all running processes |
| `ps aux` | Detailed process list |
| `top` | Real-time process monitor |
| `htop` | Interactive process viewer |
| `pstree` | Display processes as a tree |

---

# Search Processes

Search by name:

```bash
ps aux | grep nginx
```

Using `pgrep`:

```bash
pgrep firefox
```

Show process tree:

```bash
pstree
```

---

# Process Information

Show process ID (PID):

```bash
pidof nginx
```

Display process details:

```bash
ps -p 1234
```

Monitor resource usage:

```bash
top
```

---

# Kill Processes

Terminate by PID:

```bash
kill PID
```

Force termination:

```bash
kill -9 PID
```

Terminate by process name:

```bash
killall firefox
```

Using `pkill`:

```bash
pkill nginx
```

---

# Process Signals

| Signal | Number | Description |
|---------|--------|-------------|
| `SIGTERM` | 15 | Gracefully terminate process |
| `SIGKILL` | 9 | Forcefully kill process |
| `SIGSTOP` | 19 | Pause a process |
| `SIGCONT` | 18 | Resume a paused process |
| `SIGHUP` | 1 | Reload configuration |
| `SIGINT` | 2 | Interrupt process (`Ctrl + C`) |

Examples:

```bash
kill -15 PID
kill -9 PID
kill -19 PID
kill -18 PID
```

---

# Background Processes

Run command in background:

```bash
command &
```

View background jobs:

```bash
jobs
```

Move job to background:

```bash
bg
```

Bring job to foreground:

```bash
fg
```

---

# Process Priority

View priorities:

```bash
top
```

Start with custom priority:

```bash
nice -n 10 command
```

Change priority:

```bash
renice 5 PID
```

Priority range:

```text
-20 (Highest Priority)
  0 (Default)
 19 (Lowest Priority)
```

---

# Monitor System Resources

CPU usage:

```bash
top
```

Memory usage:

```bash
free -h
```

Virtual memory:

```bash
vmstat
```

I/O statistics:

```bash
iostat
```

---

# Process Ownership

Show process owner:

```bash
ps aux
```

Run as another user:

```bash
sudo -u username command
```

---

# Schedule Processes

Run once:

```bash
at 10:00
```

Recurring jobs:

```bash
crontab -e
```

List cron jobs:

```bash
crontab -l
```

---

# Service Management

View service status:

```bash
systemctl status nginx
```

Start service:

```bash
sudo systemctl start nginx
```

Stop service:

```bash
sudo systemctl stop nginx
```

Restart service:

```bash
sudo systemctl restart nginx
```

Enable at boot:

```bash
sudo systemctl enable nginx
```

Disable at boot:

```bash
sudo systemctl disable nginx
```

---

# Useful Commands

```bash
ps
top
htop
pstree
pgrep
pidof
kill
killall
pkill
nice
renice
jobs
bg
fg
systemctl
```

---

# Common Tasks

Find a process:

```bash
pgrep apache2
```

Kill a process:

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

Run in background:

```bash
python app.py &
```

Monitor CPU usage:

```bash
top
```

Monitor memory:

```bash
free -h
```

---

# Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Stop current process |
| `Ctrl + Z` | Suspend current process |
| `bg` | Resume suspended process in background |
| `fg` | Bring process to foreground |
| `q` | Exit `top` or `htop` |

---

# Best Practices

- Use `SIGTERM` before `SIGKILL`.
- Monitor resource usage regularly.
- Avoid running unnecessary background processes.
- Adjust process priority only when needed.
- Use `systemctl` to manage system services.
- Investigate high CPU or memory usage before terminating processes.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Using `kill -9` immediately | Try `kill` (`SIGTERM`) first |
| Running too many background jobs | Monitor with `jobs` |
| Ignoring resource usage | Check with `top` or `htop` |
| Changing priorities without reason | Use default priorities unless necessary |
| Killing system services accidentally | Verify the PID or process name before terminating |

---

# Quick Reference

```bash
ps aux               # List processes
top                  # Monitor processes
htop                 # Interactive monitor
pgrep nginx          # Find process
kill PID             # Terminate process
kill -9 PID          # Force terminate
killall firefox      # Kill by name
jobs                 # Show background jobs
bg                   # Background job
fg                   # Foreground job
nice -n 10 command   # Run with lower priority
renice 5 PID         # Change priority
systemctl status ssh # Service status
```

---

# Related Topics

- Processes
- Signals
- System Services
- Scheduling
- Linux Commands
- System Administration
- Performance
- Troubleshooting