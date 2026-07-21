# grep

> Search for text patterns inside files and command output using regular expressions.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Search and Filtering |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 10 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`grep` (Global Regular Expression Print) searches files or input streams for lines that match a specified pattern. It is one of the most frequently used Linux commands for searching logs, configuration files, source code, and command output.

`grep` supports both simple text matching and powerful regular expressions, making it an essential tool for developers, system administrators, and DevOps engineers.

- **What does it do?** Searches for lines matching a pattern.
- **Why does it exist?** To quickly locate information within files or command output.
- **When is it commonly used?** Searching logs, filtering command output, finding configuration settings, and locating code.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Search for text in files
- Perform case-insensitive searches
- Search recursively through directories
- Display line numbers and matching counts
- Combine `grep` with pipes for filtering

---

# ⚙️ Syntax

```bash
grep [options] PATTERN [FILE...]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `PATTERN` | Text or regular expression to search for | Yes |
| `FILE` | One or more files to search | No (reads from standard input if omitted) |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-i` | Ignore case distinctions |
| `-r` or `-R` | Search recursively through directories |
| `-n` | Show line numbers |
| `-v` | Invert the match (show non-matching lines) |
| `-c` | Count matching lines |
| `-l` | Display only filenames with matches |
| `-w` | Match whole words only |
| `-E` | Use extended regular expressions |

---

# 💻 Basic Examples

## Example 1

```bash
grep "error" app.log
```

Find lines containing the word `error`.

---

## Example 2

```bash
grep -i "warning" app.log
```

Search for `warning` without considering letter case.

---

## Example 3

```bash
grep -rn "TODO" .
```

Recursively search the current directory and display matching line numbers.

---

## Example 4

```bash
ps aux | grep nginx
```

Display running processes related to Nginx.

---

## Example 5

```bash
grep -v "^#" config.conf
```

Display all lines except comments.

---

# 📤 Example Output

```text
$ grep -n "ERROR" server.log

12:ERROR Failed to connect to database
47:ERROR Authentication failed
91:ERROR Timeout while reading response
```

Each matching line is displayed along with its line number.

---

# 🌍 Real-world Use Cases

- Searching server logs for errors
- Finding configuration values
- Filtering command output
- Searching source code for functions or variables
- Monitoring application logs

---

# 🧠 How It Works

`grep` reads input line by line and compares each line against the specified pattern.

If a match is found, the entire line is printed unless modified by command options.

When using regular expressions, `grep` applies pattern-matching rules rather than literal string comparison.

---

# ⚠️ Common Mistakes

❌ Forgetting quotes around patterns containing spaces or special characters.

---

❌ Searching recursively from the filesystem root.

This can take a long time and produce many permission errors.

---

❌ Forgetting `-i` when searching case-insensitively.

`Error` and `error` are different by default.

---

# ✅ Best Practices

- Use quotes around search patterns.
- Combine `grep` with pipes for efficient filtering.
- Use `-n` when locating text in source code.
- Use recursive searches only when necessary.
- Learn basic regular expressions for more powerful searches.

---

# 🔒 Security Considerations

Searching sensitive log files or configuration files may expose credentials or confidential information.

Protect and securely handle any output containing sensitive data.

---

# 🚀 Performance Notes

`grep` is highly optimized and can search very large files efficiently.

Recursive searches across entire filesystems may be slower depending on directory size.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `find` | Find files before searching inside them |
| `locate` | Search for filenames |
| `awk` | Advanced text processing |
| `sed` | Stream editing |
| `less` | View search results interactively |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `grep` | Searches file contents |
| `find` | Searches files and directories |
| `locate` | Searches indexed filenames |
| `awk` | Performs pattern matching and data processing |

---

# 🧪 Practice Exercises

### Beginner

Search for the word `Linux` in a text file.

---

### Intermediate

Recursively search your project for `TODO` comments.

---

### Advanced

Display every line in a log file that does **not** contain the word `INFO`.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `grep` command do?

**A:** It searches files or input for lines matching a specified pattern.

---

### Intermediate

**Q:** What is the difference between `grep -i` and `grep -v`?

**A:** `-i` ignores case while matching; `-v` displays lines that do **not** match the pattern.

---

### Advanced

**Q:** Why is `grep` commonly used with pipes?

**A:** Pipes allow `grep` to filter the output of other commands, making it easy to extract relevant information without creating intermediate files.

---

# 🛠 Troubleshooting

**Problem:** No matches found.

**Cause:**

- Incorrect pattern
- Wrong filename
- Case mismatch

**Solution:**

Verify the file contents and try using:

```bash
grep -i "pattern" file.txt
```

---

**Problem:** Too many results.

**Solution:**

Use more specific patterns or combine options like `-w` and `-n`.

---

# 📚 Official Documentation

- `man grep`
- GNU Grep Manual

---

# 📖 Further Reading

- Nexora: `find`
- Nexora: `sed`
- Nexora: `awk`
- GNU Grep Documentation

---

# 📌 Quick Summary

- `grep` searches for text patterns in files and command output.
- Supports regular expressions and recursive searches.
- Works seamlessly with pipes.
- One of the most essential Linux commands for developers and administrators.
- Use `-i`, `-n`, `-r`, and `-v` frequently.

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