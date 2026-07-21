# env

> Display the current environment variables available to the running shell or process.

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

`env` displays the environment variables currently available to a process. It can also execute a command with a modified environment.

Environment variables store configuration information such as executable search paths, user information, locale settings, and application-specific settings.

- **What does it do?** Displays or modifies environment variables for a command.
- **Why does it exist?** To inspect and control the environment in which programs execute.
- **When is it commonly used?** Debugging applications, viewing system configuration, setting temporary variables, and scripting.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Display environment variables
- Run commands with temporary environment variables
- Understand common environment variables
- Differentiate `env` from `export`
- Troubleshoot environment-related issues

---

# ⚙️ Syntax

```bash
env [options] [NAME=VALUE]... [COMMAND [ARG]...]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `NAME=VALUE` | Temporary environment variable | No |
| `COMMAND` | Command to execute | No |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-i` | Start with an empty environment |
| `-u VAR` | Remove an environment variable |
| `--help` | Display help information |
| `--version` | Show version information |

---

# 💻 Basic Examples

## Example 1

```bash
env
```

Display all environment variables.

---

## Example 2

```bash
env PATH
```

This is **incorrect**.

To view a single variable, use:

```bash
echo $PATH
```

---

## Example 3

```bash
env DEBUG=true python app.py
```

Run the Python application with the temporary variable `DEBUG=true`.

---

## Example 4

```bash
env -i bash
```

Start Bash with an empty environment.

---

## Example 5

```bash
env -u PATH command
```

Run `command` without the `PATH` environment variable.

---

# 📤 Example Output

```text
$ env

HOME=/home/revanth
USER=revanth
PATH=/usr/local/bin:/usr/bin:/bin
SHELL=/bin/bash
PWD=/home/revanth
LANG=en_US.UTF-8
```

---

# 🌍 Real-world Use Cases

- Debugging application environments
- Running programs with temporary variables
- Testing applications in a clean environment
- Viewing system configuration
- Troubleshooting PATH-related issues

---

# 🧠 How It Works

When a process starts, it inherits environment variables from its parent process.

The `env` command displays these variables or temporarily modifies them before launching another command.

Changes made with `env` affect only the command being executed—they do **not** permanently modify your shell environment.

---

# ⚠️ Common Mistakes

❌ Confusing `env` with `export`.

`env` displays or temporarily modifies environment variables.

`export` permanently sets variables for the current shell session and its child processes.

---

❌ Trying to permanently set variables using `env`.

Use:

```bash
export VARIABLE=value
```

instead.

---

❌ Exposing sensitive environment variables.

Some variables may contain API keys, tokens, or passwords.

---

# ✅ Best Practices

- Use `env` to inspect your current environment.
- Use temporary variables for testing applications.
- Store permanent variables using `export` in shell startup files.
- Avoid exposing sensitive variables in screenshots or logs.

---

# 🔒 Security Considerations

Environment variables often contain:

- API keys
- Database credentials
- Authentication tokens
- Cloud service secrets

Never share sensitive environment variables publicly.

---

# 🚀 Performance Notes

`env` is lightweight and executes almost instantly.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `export` | Create environment variables |
| `printenv` | Display environment variables |
| `echo` | Print individual variables |
| `alias` | Create shell shortcuts |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `env` | Displays variables or runs commands with modified environments |
| `export` | Creates environment variables for child processes |
| `printenv` | Displays environment variables only |

---

# 🧪 Practice Exercises

### Beginner

Display all environment variables.

---

### Intermediate

Run a command with a temporary variable named `MODE=development`.

---

### Advanced

Start a Bash shell with an empty environment and observe which variables are missing.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What does the `env` command do?

**A:** It displays environment variables or runs a command with modified environment variables.

---

### Intermediate

**Q:** What is the difference between `env` and `export`?

**A:** `env` is used to inspect or temporarily modify the environment for a command, while `export` creates or updates environment variables for the current shell and its child processes.

---

### Advanced

**Q:** Why would you use `env -i`?

**A:** To start a program with an empty environment for testing or debugging, ensuring that inherited environment variables don't affect its behavior.

---

# 🛠 Troubleshooting

**Problem:** A command behaves differently in a script than in the terminal.

**Solution:**

Compare the environments:

```bash
env
```

Look for differences in variables such as `PATH`, `HOME`, or `LANG`.

---

**Problem:** Command not found after using `env -i`.

**Solution:**

Since `PATH` is removed, use the command's absolute path or redefine `PATH`.

---

# 📚 Official Documentation

- `man env`
- GNU Coreutils Manual (`env`)

---

# 📖 Further Reading

- Nexora: `export`
- Nexora: `alias`
- Nexora: `history`
- Bash Manual

---

# 📌 Quick Summary

- `env` displays environment variables.
- It can temporarily modify the environment for a command.
- Use `env -i` to start with a clean environment.
- It does not permanently change shell variables.
- Frequently used for debugging, testing, and application configuration.

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