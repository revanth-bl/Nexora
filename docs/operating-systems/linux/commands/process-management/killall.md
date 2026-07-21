# killall

> Terminate one or more running processes by their name instead of their Process ID (PID).

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Process Management |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 6 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`killall` sends signals to processes based on their name rather than their Process ID (PID). This makes it convenient when multiple instances of the same program are running or when you don't know the PID.

Unlike `kill`, which requires a PID, `killall` works directly with process names.

- **What does it do?** Sends signals to processes identified by name.
- **Why does it exist?** To simplify process management without needing PIDs.
- **When is it commonly used?** Closing applications, restarting services, and terminating multiple instances of a program.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Kill processes by name
- Send different signals using `killall`
- Terminate multiple process instances
- Understand when to use `killall` instead of `kill`

---

# ⚙️ Syntax

```bash
killall [options] process_name
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `process_name` | Name of the target process | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-9` | Forcefully terminate processes (SIGKILL) |
| `-15` | Gracefully terminate processes (SIGTERM, default) |
| `-i` | Ask for confirmation before killing each process |
| `-v` | Display information about terminated processes |
| `-u user` | Kill only processes owned by a specific user |
| `-l` | List available signal names |

---

# 💻 Basic Examples

## Example 1

```bash
killall firefox
```

Terminate all running Firefox processes.

---

## Example 2

```bash
killall -9 firefox
```

Forcefully terminate all Firefox processes.

---

## Example 3

```bash
killall -i python
```

Ask for confirmation before killing each Python process.

---

## Example 4

```bash
killall -u revanth nginx
```

Terminate all `nginx` processes owned by user `revanth`.

---

## Example 5

```bash
killall -v chrome
```

Display information about each terminated Chrome process.

---

# 📤 Example Output

```text
$ killall firefox

firefox: no process found
```

Or:

```text
Killed firefox(2458)
Killed firefox(2489)
```

---

# 🌍 Real-world Use Cases

- Closing all browser instances
- Stopping multiple Python scripts
- Restarting applications
- Managing background services
- Cleaning up development environments

---

# 🧠 How It Works

`killall` searches the system for processes whose names match the specified process name.

It then sends the selected signal to every matching process.

By default, it sends:

```text
SIGTERM (15)
```

which allows applications to shut down gracefully.

---

# ⚠️ Common Mistakes

❌ Confusing `killall` with `kill`.

`kill` uses a PID, while `killall` uses the process name.

---

❌ Using `killall -9` unnecessarily.

Try graceful termination first.

---

❌ Accidentally killing every instance of an application.

Remember that `killall` targets **all matching processes**.

---

# ✅ Best Practices

- Verify running processes with `ps` before using `killall`.
- Prefer the default SIGTERM before using SIGKILL.
- Use `-i` when you're unsure.
- Be cautious when multiple users are running the same application.

---

# 🔒 Security Considerations

Normal users can terminate only their own processes.

Administrative privileges (`sudo`) are required to terminate processes owned by other users or system services.

---

# 🚀 Performance Notes

`killall` is very efficient since it searches the system process table and sends signals directly.

Performance impact is negligible under normal workloads.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `kill` | Kill a process using its PID |
| `pkill` | Kill processes matching a name or pattern |
| `ps` | Display running processes |
| `top` | Monitor running processes |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `kill` | Uses Process ID (PID) |
| `killall` | Uses exact process name |
| `pkill` | Uses patterns or partial names |

---

# 🧪 Practice Exercises

### Beginner

Terminate all running instances of Firefox.

---

### Intermediate

Terminate only your own Python processes.

---

### Advanced

Compare the behavior of `kill`, `killall`, and `pkill` on a system running multiple instances of the same application.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the difference between `kill` and `killall`?

**A:** `kill` targets a process using its PID, while `killall` targets processes by their name.

---

### Intermediate

**Q:** What signal does `killall` send by default?

**A:** SIGTERM (15), which requests a graceful shutdown.

---

### Advanced

**Q:** Why might `killall` be dangerous on multi-user systems?

**A:** It may terminate every matching process if not used carefully, potentially affecting multiple applications or users.

---

# 🛠 Troubleshooting

**Problem:** `no process found`

**Cause:**

No running process matches the specified name.

**Solution:**

Verify the process name using:

```bash
ps aux
```

or

```bash
pgrep process_name
```

---

**Problem:** `Operation not permitted`

**Cause:**

You don't own the target process.

**Solution:**

Use `sudo` if you have administrative privileges.

---

# 📚 Official Documentation

- `man killall`
- `man signal`

---

# 📖 Further Reading

- Nexora: `kill`
- Nexora: `pkill`
- Nexora: `ps`
- Nexora: `top`

---

# 📌 Quick Summary

- `killall` terminates processes by **name**.
- Uses **SIGTERM** by default.
- Can terminate multiple instances simultaneously.
- Supports confirmation, verbose output, and user filtering.
- Prefer graceful termination before using `-9`.

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