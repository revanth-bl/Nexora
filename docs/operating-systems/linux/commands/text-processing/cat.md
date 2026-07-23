# cat

> Display, concatenate, and create text files directly from the command line.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Text Processing |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`cat` (short for **concatenate**) is one of the most commonly used Linux commands. It is used to display the contents of files, combine multiple files, and create new text files directly from the terminal.

Although simple, `cat` is a powerful tool frequently used in scripting, debugging, and day-to-day Linux administration.

- **What does it do?** Displays, combines, and creates text files.
- **Why does it exist?** To quickly view and manipulate file contents.
- **When is it commonly used?** Viewing configuration files, merging files, creating small text files, and piping data between commands.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display file contents
- Concatenate multiple files
- Create text files
- Redirect output into files
- Use common display options

---

# ⚙️ Syntax

```bash
cat [OPTIONS] FILE...
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `FILE` | One or more files to display or concatenate | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-n` | Number all output lines |
| `-b` | Number only non-empty lines |
| `-s` | Squeeze multiple blank lines into one |
| `-E` | Display `$` at the end of each line |
| `-T` | Display tab characters as `^I` |
| `-A` | Show all non-printing characters |

---

# 💻 Basic Examples

## Example 1

Display a file.

```bash
cat notes.txt
```

---

## Example 2

Display multiple files.

```bash
cat file1.txt file2.txt
```

---

## Example 3

Create a file.

```bash
cat > notes.txt
```

Type your text, then press:

```text
Ctrl + D
```

to save the file.

---

## Example 4

Append text to a file.

```bash
cat >> notes.txt
```

---

## Example 5

Combine files.

```bash
cat chapter1.txt chapter2.txt > book.txt
```

---

## Example 6

Display line numbers.

```bash
cat -n notes.txt
```

---

# 📤 Example Output

```text
$ cat notes.txt

Linux is awesome.
Learning never stops.
```

With numbering:

```text
$ cat -n notes.txt

1  Linux is awesome.
2  Learning never stops.
```

---

# 🌍 Real-world Use Cases

- Viewing configuration files
- Reading log files
- Creating quick notes
- Combining multiple files
- Passing file contents to other commands
- Debugging scripts

---

# 🧠 How It Works

`cat` reads one or more files sequentially and writes their contents to **standard output (stdout)**.

It can also read input from the keyboard (standard input) and write it into a file using output redirection.

Example:

```text
File
   │
   ▼
 cat
   │
   ▼
Terminal (stdout)
```

---

# ⚠️ Common Mistakes

❌ Using `cat` to read very large files.

Prefer:

```bash
less file.txt
```

or

```bash
more file.txt
```

---

❌ Accidentally overwriting files.

```bash
cat > important.txt
```

replaces the file's contents.

Use:

```bash
cat >> important.txt
```

to append instead.

---

❌ Forgetting to press `Ctrl + D` after creating a file.

Without it, the terminal continues waiting for input.

---

# ✅ Best Practices

- Use `less` for large files.
- Use `cat -n` when reviewing source code.
- Avoid overwriting important files accidentally.
- Combine `cat` with pipes for efficient workflows.

---

# 🔒 Security Considerations

Be cautious when displaying sensitive files such as:

```text
/etc/shadow
```

or configuration files containing passwords or API keys.

Only authorized users should access confidential information.

---

# 🚀 Performance Notes

`cat` is extremely fast for small and medium-sized files.

For very large files, tools like `less` are more memory-efficient and easier to navigate.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `less` | View large files interactively |
| `more` | Paginated file viewer |
| `head` | Display the beginning of a file |
| `tail` | Display the end of a file |
| `tac` | Display file contents in reverse order |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `cat` | Display entire file |
| `less` | Interactive file viewer |
| `head` | First lines only |
| `tail` | Last lines only |
| `tac` | Reverse line order |

---

# 🧪 Practice Exercises

### Beginner

Display the contents of a text file.

---

### Intermediate

Combine two files into a third file.

---

### Advanced

Create a file using `cat`, append additional text, and display it with line numbers.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `cat` command do?

**A:** It displays, concatenates, and creates text files.

---

### Intermediate

**Q:** What is the difference between:

```bash
cat > file.txt
```

and

```bash
cat >> file.txt
```

**A:**

- `>` creates a new file or overwrites an existing one.
- `>>` appends data to an existing file without removing its current contents.

---

### Advanced

**Q:** Why would you use `less` instead of `cat` for large log files?

**A:** `less` allows interactive scrolling and loads content efficiently, making it easier to navigate very large files without flooding the terminal.

---

# 🛠 Troubleshooting

**Problem:** Terminal appears stuck after running:

```bash
cat > file.txt
```

**Solution:**

Finish entering text and press:

```text
Ctrl + D
```

to save the file and return to the shell.

---

**Problem:** File contents were accidentally overwritten.

**Solution:**

If no backup exists, recovery may not be possible. Use:

```bash
cat >> file.txt
```

when you intend to append rather than overwrite.

---

# 📚 Official Documentation

- `man cat`
- GNU Coreutils Manual (`cat`)

---

# 📖 Further Reading

- Nexora: `less`
- Nexora: `head`
- Nexora: `tail`
- GNU Coreutils Documentation

---

# 📌 Quick Summary

- `cat` displays, creates, and combines text files.
- Use `cat file.txt` to display a file.
- Use `cat > file.txt` to create or overwrite a file.
- Use `cat >> file.txt` to append to a file.
- One of the most fundamental Linux commands for text processing.

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