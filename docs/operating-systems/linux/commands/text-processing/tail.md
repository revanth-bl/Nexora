# tail

> Display the last few lines of a file or input stream.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Text Processing |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 6 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`tail` is a Linux command used to display the last part of a file or input stream. By default, it prints the last **10 lines**, making it particularly useful for monitoring log files and checking recent updates.

Unlike `head`, which displays the beginning of a file, `tail` focuses on the most recent content.

- **What does it do?** Displays the last part of a file.
- **Why does it exist?** To quickly inspect the most recent data in files.
- **When is it commonly used?** Monitoring logs, debugging applications, and viewing recent file updates.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display the last lines of a file
- Show a custom number of lines
- Display the last bytes of a file
- Monitor files in real time
- Use `tail` with pipes

---

# ⚙️ Syntax

```bash
tail [OPTIONS] FILE...
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `FILE` | File(s) to display | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-n N` | Display the last N lines |
| `-c N` | Display the last N bytes |
| `-f` | Follow file updates in real time |
| `-F` | Follow file by name, retry if recreated |
| `-q` | Never print file headers |
| `-v` | Always print file headers |
| `--help` | Display help information |

---

# 💻 Basic Examples

## Example 1

Display the last 10 lines.

```bash
tail logfile.log
```

---

## Example 2

Display the last 20 lines.

```bash
tail -n 20 logfile.log
```

---

## Example 3

Display the last 100 bytes.

```bash
tail -c 100 file.txt
```

---

## Example 4

Monitor a log file in real time.

```bash
tail -f /var/log/syslog
```

Press:

```text
Ctrl + C
```

to stop monitoring.

---

## Example 5

View the last few running processes.

```bash
ps aux | tail
```

---

# 📤 Example Output

```text
$ tail -n 5 logfile.log

[INFO] Server started
[INFO] User login successful
[WARNING] Low disk space
[ERROR] Connection timeout
[INFO] Backup completed
```

---

# 🌍 Real-world Use Cases

- Monitoring web server logs
- Watching application logs during debugging
- Checking recent system events
- Inspecting the latest entries in audit logs
- Viewing the end of large files

---

# 🧠 How It Works

`tail` reads the end of a file or input stream and prints only the requested portion.

When used with `-f`, it continues running and displays new data as it is written to the file.

```text
Growing Log File
        │
        ▼
      tail -f
        │
        ▼
 Live Updates
```

---

# ⚠️ Common Mistakes

❌ Forgetting that the default output is **10 lines**.

Specify a different number if needed:

```bash
tail -n 50 logfile.log
```

---

❌ Confusing `tail -f` with a one-time view.

`tail`:

```bash
tail logfile.log
```

Shows the last lines once.

`tail -f`:

```bash
tail -f logfile.log
```

Continuously monitors the file.

---

❌ Using `tail` to inspect the beginning of a file.

Use:

```bash
head file.txt
```

instead.

---

# ✅ Best Practices

- Use `tail -f` to monitor active log files.
- Combine `tail` with `grep` to filter important messages.
- Specify the number of lines using `-n` for clarity.
- Use `less` when interactive navigation is required.

Example:

```bash
tail -f /var/log/syslog | grep ERROR
```

---

# 🔒 Security Considerations

Log files may contain:

- Usernames
- IP addresses
- Authentication attempts
- API keys
- System configuration details

Only view sensitive logs if you have appropriate permissions.

---

# 🚀 Performance Notes

`tail` is highly efficient because it reads only the end of a file.

Even for very large log files, it requires minimal memory and is ideal for real-time monitoring.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `head` | Display the beginning of a file |
| `cat` | Display the entire file |
| `less` | Interactive file viewer |
| `journalctl` | Monitor systemd logs |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `tail` | Displays the end of a file |
| `head` | Displays the beginning of a file |
| `cat` | Displays the entire file |
| `less` | Interactive navigation |

---

# 🧪 Practice Exercises

### Beginner

Display the last 15 lines of a log file.

---

### Intermediate

Monitor a log file in real time using `tail -f`.

---

### Advanced

Monitor a log file and display only lines containing the word `ERROR`.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the default behavior of the `tail` command?

**A:** It displays the last **10 lines** of a file.

---

### Intermediate

**Q:** What is the purpose of the `-f` option?

**A:** It continuously monitors a file and displays new lines as they are added.

---

### Advanced

**Q:** What is the difference between `tail -f` and `tail -F`?

**A:**

- `tail -f` follows the current file descriptor.
- `tail -F` follows the filename and automatically reconnects if the file is rotated or recreated, making it ideal for log files.

---

# 🛠 Troubleshooting

**Problem:** `tail -f` never exits.

**Solution:**

This is expected behavior. Press:

```text
Ctrl + C
```

to stop monitoring.

---

**Problem:** Log file is rotated and monitoring stops.

**Solution:**

Use:

```bash
tail -F logfile.log
```

instead of:

```bash
tail -f logfile.log
```

---

# 📚 Official Documentation

- `man tail`
- GNU Coreutils Manual (`tail`)

---

# 📖 Further Reading

- Nexora: `head`
- Nexora: `less`
- Nexora: `journalctl`
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `tail` displays the end of a file.
- The default output is the last **10 lines**.
- Use `-n` to specify the number of lines.
- Use `-f` for real-time monitoring.
- Use `-F` to continue following rotated log files.

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