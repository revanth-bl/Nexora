# tee

> Read from standard input and write output to both the terminal and one or more files simultaneously.

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

`tee` is a Linux command that reads data from **standard input (stdin)** and writes it to both **standard output (stdout)** and one or more files simultaneously.

It is especially useful when you want to save the output of a command while still displaying it on the terminal.

- **What does it do?** Copies input to both the terminal and files.
- **Why does it exist?** To avoid running a command twice when you need to both view and save its output.
- **When is it commonly used?** Logging command output, debugging shell scripts, and creating reports.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Save command output while displaying it
- Append output to existing files
- Use `tee` in pipelines
- Write to multiple files simultaneously
- Understand common use cases

---

# ⚙️ Syntax

```bash
tee [OPTIONS] FILE...
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `FILE` | File(s) to receive a copy of the input | No |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-a` | Append to the file instead of overwriting it |
| `-i` | Ignore interrupt signals (`Ctrl + C`) |
| `--help` | Display help information |
| `--version` | Show version information |

---

# 💻 Basic Examples

## Example 1

Save command output to a file.

```bash
ls | tee files.txt
```

---

## Example 2

Append output to a file.

```bash
date | tee -a log.txt
```

---

## Example 3

Write to multiple files.

```bash
echo "Hello, Linux!" | tee file1.txt file2.txt
```

---

## Example 4

Save system information.

```bash
uname -a | tee system-info.txt
```

---

## Example 5

Capture command output while monitoring logs.

```bash
journalctl -f | tee journal.log
```

---

# 📤 Example Output

```text
$ echo "Welcome" | tee message.txt

Welcome
```

Contents of `message.txt`:

```text
Welcome
```

---

# 🌍 Real-world Use Cases

- Logging command output
- Saving installation logs
- Recording system information
- Creating backup reports
- Debugging shell scripts
- Monitoring services while keeping a log

---

# 🧠 How It Works

`tee` receives data from **standard input**, then duplicates it.

One copy goes to:

- The terminal (`stdout`)

Another copy goes to:

- One or more files

```text
Command
   │
   ▼
  tee
 ┌──┴────────┐
 ▼           ▼
Terminal    File
```

---

# ⚠️ Common Mistakes

❌ Forgetting that `tee` overwrites files by default.

```bash
tee output.txt
```

replaces existing contents.

Use:

```bash
tee -a output.txt
```

to append instead.

---

❌ Expecting `tee` to work without input.

`tee` reads from standard input, so it is usually used in a pipeline.

Example:

```bash
ls | tee files.txt
```

---

❌ Forgetting `sudo` when writing to protected files.

Example:

```bash
echo "text" | sudo tee /etc/example.conf
```

---

# ✅ Best Practices

- Use `-a` when preserving existing logs.
- Combine `tee` with pipes for efficient workflows.
- Use descriptive filenames for saved output.
- Prefer `sudo tee` when writing to system files instead of redirecting with `>`.

---

# 🔒 Security Considerations

Avoid saving sensitive information such as:

- Passwords
- API keys
- Authentication tokens

Ensure log files created with `tee` have appropriate file permissions.

---

# 🚀 Performance Notes

`tee` is lightweight and introduces minimal overhead, even when writing to multiple files.

Performance depends mainly on the speed of the storage device.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `echo` | Generate text for `tee` |
| `cat` | Display file contents |
| `head` | Display the beginning of a file |
| `tail` | Display the end of a file |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `tee` | Writes output to both terminal and file |
| `>` | Redirects output only to a file |
| `>>` | Appends output only to a file |
| `cat` | Displays file contents |

---

# 🧪 Practice Exercises

### Beginner

Save the output of `ls` to a file while displaying it.

---

### Intermediate

Append the current date to a log file.

---

### Advanced

Use `tee` to save the output of `journalctl -f` while monitoring logs in real time.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `tee` command?

**A:** It copies input to both the terminal and one or more files simultaneously.

---

### Intermediate

**Q:** What is the difference between `tee` and the `>` redirection operator?

**A:** `tee` displays the output on the terminal while also writing it to a file. The `>` operator redirects output only to a file.

---

### Advanced

**Q:** Why is `sudo tee` often used instead of `sudo echo "text" > file`?

**A:** Because shell redirection (`>`) is performed before `sudo` is applied. Using `sudo tee` ensures the write operation is performed with elevated privileges.

Example:

```bash
echo "data" | sudo tee /etc/config.conf
```

---

# 🛠 Troubleshooting

**Problem:** Existing file contents were overwritten.

**Solution:**

Use:

```bash
tee -a filename
```

to append instead of overwrite.

---

**Problem:** Permission denied when writing to a system file.

**Solution:**

Use:

```bash
echo "text" | sudo tee /path/to/file
```

instead of:

```bash
echo "text" > /path/to/file
```

---

# 📚 Official Documentation

- `man tee`
- GNU Coreutils Manual (`tee`)

---

# 📖 Further Reading

- Nexora: `echo`
- Nexora: `cat`
- Nexora: `tail`
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `tee` writes input to both the terminal and one or more files.
- Use `-a` to append instead of overwrite.
- Frequently used with pipelines.
- Useful for logging command output while viewing it.
- Essential for scripting and system administration.

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