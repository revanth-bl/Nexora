# ps

> Display information about currently running processes on a Linux system.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Process Management |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`ps` (Process Status) displays information about active processes running on a Linux system. It helps administrators and developers inspect running programs, identify resource usage, troubleshoot issues, and obtain Process IDs (PIDs) needed by other commands like `kill`.

Unlike `top`, `ps` provides a snapshot of the current processes rather than a continuously updating view.

- **What does it do?** Displays information about running processes.
- **Why does it exist?** To inspect and manage active processes.
- **When is it commonly used?** Finding process IDs, debugging applications, monitoring services, and troubleshooting system issues.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- View running processes
- Understand common `ps` output fields
- Display processes for all users
- Find specific processes
- Combine `ps` with other Linux commands

---

# ⚙️ Syntax

```bash
ps [options]
```

---

# 📝 Parameters

`ps` primarily works through options rather than positional parameters.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-e` | Show all running processes |
| `-f` | Full-format listing |
| `-u user` | Show processes owned by a user |
| `-p PID` | Show information for a specific PID |
| `aux` | BSD-style output showing all processes with detailed information |
| `-o` | Display selected output columns |

---

# 💻 Basic Examples

## Example 1

```bash
ps
```

Display processes associated with the current terminal.

---

## Example 2

```bash
ps -e
```

Display every running process.

---

## Example 3

```bash
ps aux
```

Show detailed information for all running processes.

---

## Example 4

```bash
ps -u revanth
```

Display processes owned by the user `revanth`.

---

## Example 5

```bash
ps -p 1234
```

Display information about process ID `1234`.

---

# 📤 Example Output

```text
$ ps

PID   TTY          TIME CMD
2458  pts/0    00:00:01 bash
2514  pts/0    00:00:00 ps
```

Explanation:

- **PID** → Process ID
- **TTY** → Terminal associated with the process
- **TIME** → CPU time used
- **CMD** → Command that started the process

---

# 🌍 Real-world Use Cases

- Finding a PID before using `kill`
- Verifying that a service is running
- Monitoring application processes
- Checking which programs belong to a specific user
- Troubleshooting high CPU or memory usage

---

# 🧠 How It Works

Linux stores information about every running process in the `/proc` virtual filesystem.

`ps` reads this information and presents it in a human-readable format.

Unlike `top`, `ps` captures a single snapshot at the moment it is executed.

---

# ⚠️ Common Mistakes

❌ Expecting `ps` to update automatically.

It only shows a snapshot. Use `top` or `htop` for real-time monitoring.

---

❌ Confusing `ps` with `pstree`.

`ps` displays processes in a list, while `pstree` shows their parent-child relationships.

---

❌ Forgetting `aux`.

Running only `ps` displays processes attached to the current terminal, not the entire system.

---

# ✅ Best Practices

- Use `ps aux` when troubleshooting.
- Combine with `grep` to locate specific processes.
- Verify a PID before sending signals using `kill`.
- Use `-o` to customize output for scripts.

---

# 🔒 Security Considerations

Most users can view system processes, but detailed information about processes owned by other users may be restricted depending on system configuration.

Administrative privileges may be required for certain process details.

---

# 🚀 Performance Notes

`ps` is lightweight and completes quickly, even on systems running thousands of processes.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `top` | Real-time process monitoring |
| `kill` | Send signals to a process |
| `killall` | Kill processes by name |
| `pgrep` | Search processes by name |
| `pstree` | Display processes as a tree |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `ps` | Snapshot of running processes |
| `top` | Live, continuously updating process monitor |
| `htop` | Interactive process viewer |
| `pstree` | Displays process hierarchy |

---

# 🧪 Practice Exercises

### Beginner

Display all running processes.

---

### Intermediate

Find the PID of a running web server.

---

### Advanced

Display only the PID and command name using the `-o` option.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `ps` command do?

**A:** It displays information about running processes.

---

### Intermediate

**Q:** What is the difference between `ps` and `top`?

**A:** `ps` provides a snapshot of processes, while `top` displays a continuously updating, real-time view.

---

### Advanced

**Q:** Why is `ps aux | grep nginx` commonly used?

**A:** It searches the process list for running Nginx processes, making it easy to verify whether the service is active.

---

# 🛠 Troubleshooting

**Problem:** A process isn't shown.

**Cause:**

It may have already terminated before `ps` was executed.

**Solution:**

Run `ps` again or use `top` for real-time monitoring.

---

**Problem:** Too much output from `ps aux`.

**Solution:**

Filter the results:

```bash
ps aux | grep nginx
```

---

# 📚 Official Documentation

- `man ps`
- `man proc`

---

# 📖 Further Reading

- Nexora: `top`
- Nexora: `kill`
- Nexora: `killall`
- Nexora: `pgrep`

---

# 📌 Quick Summary

- `ps` displays information about running processes.
- `ps aux` is the most commonly used form.
- Use `ps -p` to inspect a specific PID.
- Combine with `grep` to locate processes.
- Unlike `top`, `ps` shows a single snapshot.

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