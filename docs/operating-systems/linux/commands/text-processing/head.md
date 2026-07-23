# head

> Display the first few lines of a file or input stream.

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

`head` is a Linux command used to display the beginning of a file or input stream. By default, it prints the first **10 lines**, making it useful for quickly previewing files without opening them entirely.

It is commonly used when inspecting log files, configuration files, CSV datasets, and command output.

- **What does it do?** Displays the first part of a file.
- **Why does it exist?** To quickly preview file contents.
- **When is it commonly used?** Inspecting logs, configuration files, datasets, and debugging.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display the first lines of a file
- Show a custom number of lines
- Display a specific number of bytes
- Use `head` with pipes
- Compare `head` with related commands

---

# ⚙️ Syntax

```bash
head [OPTIONS] FILE...
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
| `-n N` | Display the first N lines |
| `-c N` | Display the first N bytes |
| `-q` | Never print file headers |
| `-v` | Always print file headers |
| `--help` | Display help information |

---

# 💻 Basic Examples

## Example 1

Display the first 10 lines.

```bash
head file.txt
```

---

## Example 2

Display the first 5 lines.

```bash
head -n 5 file.txt
```

---

## Example 3

Display the first 100 bytes.

```bash
head -c 100 file.txt
```

---

## Example 4

Display the first 20 lines of multiple files.

```bash
head -n 20 file1.txt file2.txt
```

---

## Example 5

Preview command output.

```bash
ps aux | head
```

---

# 📤 Example Output

```text
$ head -n 5 notes.txt

Linux Basics
-------------
1. Files
2. Directories
3. Permissions
```

---

# 🌍 Real-world Use Cases

- Preview configuration files
- Inspect the beginning of log files
- Check CSV headers
- Debug command output
- View the first records of datasets

---

# 🧠 How It Works

`head` reads data from a file or standard input and stops after printing the requested number of lines or bytes.

Example:

```text
File
   │
   ▼
 head
   │
   ▼
Terminal
```

It can also receive input from another command:

```bash
cat file.txt | head
```

---

# ⚠️ Common Mistakes

❌ Forgetting that the default is **10 lines**.

To display a different number:

```bash
head -n 25 file.txt
```

---

❌ Confusing lines and bytes.

```bash
head -n 10 file.txt
```

shows **10 lines**.

```bash
head -c 10 file.txt
```

shows **10 bytes**.

---

❌ Using `cat` for very large files.

Instead, preview them using:

```bash
head
```

or

```bash
less
```

---

# ✅ Best Practices

- Use `head` to quickly inspect files.
- Combine with `grep` and pipes for efficient filtering.
- Use `-n` instead of relying on the default 10 lines.
- Use `less` for interactive browsing of large files.

---

# 🔒 Security Considerations

Previewing sensitive files may expose confidential information.

Be cautious when using:

```bash
head /etc/shadow
```

or application configuration files containing credentials.

---

# 🚀 Performance Notes

`head` is extremely fast because it stops reading once the requested number of lines or bytes has been displayed.

It is much more efficient than reading an entire large file.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `tail` | Display the end of a file |
| `cat` | Display the entire file |
| `less` | Interactive file viewer |
| `more` | Paginated file viewer |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `head` | Displays the beginning of a file |
| `tail` | Displays the end of a file |
| `cat` | Displays the entire file |
| `less` | Interactive navigation |

---

# 🧪 Practice Exercises

### Beginner

Display the first 15 lines of a text file.

---

### Intermediate

Display the first 200 bytes of a file.

---

### Advanced

Use `ps aux | head` to display only the first few running processes.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the default behavior of the `head` command?

**A:** It displays the first **10 lines** of a file.

---

### Intermediate

**Q:** How do you display the first 25 lines of a file?

**A:**

```bash
head -n 25 file.txt
```

---

### Advanced

**Q:** Why is `head` preferred over `cat` when previewing very large files?

**A:** Because `head` stops reading after displaying the requested number of lines, making it much faster and more memory-efficient than displaying the entire file.

---

# 🛠 Troubleshooting

**Problem:** Only the first 10 lines are shown.

**Solution:**

Specify the required number:

```bash
head -n 50 file.txt
```

---

**Problem:** Need to inspect the end of the file instead.

**Solution:**

Use:

```bash
tail file.txt
```

---

# 📚 Official Documentation

- `man head`
- GNU Coreutils Manual (`head`)

---

# 📖 Further Reading

- Nexora: `tail`
- Nexora: `cat`
- Nexora: `less`
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `head` displays the beginning of a file.
- The default output is the first **10 lines**.
- Use `-n` to specify the number of lines.
- Use `-c` to display bytes instead of lines.
- Ideal for previewing large files and command output.

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