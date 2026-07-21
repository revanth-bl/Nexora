# export

> Set environment variables and make them available to child processes and programs.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | System Information |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`export` is a shell built-in command used to create or modify environment variables and make them available to child processes.

Without `export`, a variable exists only in the current shell. Once exported, any program or shell launched from the current session can access it.

- **What does it do?** Creates or marks shell variables as environment variables.
- **Why does it exist?** To allow child processes to inherit variables from the current shell.
- **When is it commonly used?** Configuring software, setting `PATH`, defining API keys, and customizing shell environments.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Create environment variables
- Export variables to child processes
- Modify existing variables
- Permanently store environment variables
- Understand the difference between shell and environment variables

---

# ⚙️ Syntax

```bash
export NAME=value
```

or

```bash
export NAME
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `NAME` | Variable name | Yes |
| `value` | Variable value | No |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-p` | Display all exported variables |
| `-n` | Remove the export attribute from a variable |

---

# 💻 Basic Examples

## Example 1

```bash
export NAME="Revanth"
```

Create and export an environment variable.

---

## Example 2

```bash
echo $NAME
```

Display the variable.

---

## Example 3

```bash
export PATH=$PATH:/opt/bin
```

Add `/opt/bin` to the executable search path.

---

## Example 4

```bash
export DEBUG=true
python app.py
```

Run a Python application with the `DEBUG` variable available.

---

## Example 5

Display all exported variables.

```bash
export -p
```

---

# 📤 Example Output

```text
$ export -p

declare -x HOME="/home/revanth"
declare -x PATH="/usr/local/bin:/usr/bin:/bin"
declare -x USER="revanth"
declare -x LANG="en_US.UTF-8"
```

---

# 🌍 Real-world Use Cases

- Setting the `PATH` environment variable
- Configuring Java with `JAVA_HOME`
- Providing API keys to applications
- Configuring Docker, Kubernetes, and cloud CLIs
- Setting development or production environments

---

# 🧠 How It Works

Every shell maintains its own variables.

When you run:

```bash
NAME="Linux"
```

the variable exists only in the current shell.

After:

```bash
export NAME
```

or

```bash
export NAME="Linux"
```

the variable becomes part of the environment and is inherited by child processes.

Example:

```bash
export APP_ENV=production
python app.py
```

The Python application can now read the `APP_ENV` environment variable.

---

# ⚠️ Common Mistakes

❌ Forgetting `export`.

```bash
NAME="Linux"
```

Child processes cannot access `NAME`.

---

❌ Adding spaces around `=`.

Incorrect:

```bash
export NAME = Linux
```

Correct:

```bash
export NAME=Linux
```

---

❌ Expecting exported variables to persist after opening a new terminal.

They disappear unless added to:

- `~/.bashrc`
- `~/.profile`
- `~/.bash_profile`
- `~/.zshrc`

---

# ✅ Best Practices

- Use uppercase names for environment variables.
- Store permanent variables in your shell startup files.
- Avoid exporting unnecessary variables.
- Document important environment variables in project documentation.

---

# 🔒 Security Considerations

Environment variables often store sensitive information such as:

- API keys
- Database passwords
- Cloud credentials
- Authentication tokens

Avoid exposing them in screenshots, logs, or version control.

For production systems, use dedicated secret management solutions whenever possible.

---

# 🚀 Performance Notes

Exporting variables has negligible performance impact.

Large numbers of unnecessary environment variables can slightly increase process startup time.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `env` | Display environment variables |
| `printenv` | Print environment variables |
| `unset` | Remove variables |
| `alias` | Create command shortcuts |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `export` | Creates environment variables |
| `env` | Displays variables or runs commands with temporary variables |
| `printenv` | Prints environment variables only |
| `unset` | Removes variables |

---

# 🧪 Practice Exercises

### Beginner

Create and export a variable named `PROJECT`.

---

### Intermediate

Append a directory to your `PATH`.

---

### Advanced

Store a custom environment variable permanently in your shell startup file and verify it after opening a new terminal.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `export` command?

**A:** It marks a shell variable as an environment variable so that child processes can access it.

---

### Intermediate

**Q:** What is the difference between a shell variable and an environment variable?

**A:** A shell variable exists only in the current shell. An environment variable is inherited by child processes and programs.

---

### Advanced

**Q:** Why do developers commonly use `export PATH=$PATH:/new/path`?

**A:** It appends a new directory to the existing executable search path without overwriting the current `PATH`, allowing additional executables to be found by the shell.

---

# 🛠 Troubleshooting

**Problem:** Program cannot access a variable.

**Solution:**

Verify it is exported:

```bash
export -p
```

or

```bash
env
```

---

**Problem:** Variable disappears after reopening the terminal.

**Solution:**

Add the export statement to:

```bash
~/.bashrc
```

or

```bash
~/.zshrc
```

Then reload:

```bash
source ~/.bashrc
```

---

# 📚 Official Documentation

- `help export` (Bash built-in)
- Bash Reference Manual

---

# 📖 Further Reading

- Nexora: `env`
- Nexora: `alias`
- Nexora: Shell Environment Variables
- Bash Manual

---

# 📌 Quick Summary

- `export` makes variables available to child processes.
- Commonly used to configure applications and development environments.
- Variables are temporary unless stored in shell startup files.
- Frequently used with `PATH`, `JAVA_HOME`, and API keys.
- Essential for Linux administration, development, and automation.

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