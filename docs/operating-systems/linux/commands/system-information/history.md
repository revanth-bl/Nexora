# history

> Display, search, and manage the command history of the current shell session.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | System Information |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 6 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`history` is a shell built-in command that displays the list of commands previously executed in the current shell. It helps users quickly recall, reuse, and rerun commands without typing them again.

Most Linux shells, including **Bash** and **Zsh**, automatically save command history, making `history` an essential productivity tool.

- **What does it do?** Displays and manages the shell's command history.
- **Why does it exist?** To help users recall and reuse previously executed commands.
- **When is it commonly used?** Reviewing past commands, debugging, repeating tasks, and auditing terminal activity.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- View command history
- Search previous commands
- Re-execute commands from history
- Clear command history
- Configure history behavior

---

# ⚙️ Syntax

```bash
history [options] [N]
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `N` | Display only the last N commands | No |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-c` | Clear the current history |
| `-d OFFSET` | Delete a specific history entry |
| `-a` | Append new history lines to the history file |
| `-r` | Read the history file into the current session |
| `-w` | Write the current history to the history file |

---

# 💻 Basic Examples

## Example 1

```bash
history
```

Display all commands stored in the current shell's history.

---

## Example 2

```bash
history 20
```

Display the last 20 commands.

---

## Example 3

```bash
history | grep ssh
```

Search history for commands containing `ssh`.

---

## Example 4

```bash
!42
```

Re-execute command number **42**.

---

## Example 5

```bash
!!
```

Run the previous command again.

---

## Example 6

```bash
history -c
```

Clear the current shell's history.

---

# 📤 Example Output

```text
$ history

1  pwd
2  ls -lah
3  cd projects
4  git status
5  history
```

The first column is the history number, followed by the command that was executed.

---

# 🌍 Real-world Use Cases

- Reusing long commands
- Auditing previous terminal activity
- Searching for previously executed commands
- Debugging command sequences
- Learning from past terminal sessions

---

# 🧠 How It Works

Most shells store executed commands in memory during a session and periodically write them to a history file.

For Bash, the default history file is:

```text
~/.bash_history
```

The shell loads this file when a new session starts and appends new commands when the session ends (or when explicitly instructed).

---

# ⚠️ Common Mistakes

❌ Assuming every command is automatically saved.

Commands may not be recorded depending on shell settings such as `HISTCONTROL` or if the session terminates unexpectedly.

---

❌ Clearing history doesn't always erase the history file.

To remove both in-memory and saved history:

```bash
history -c
history -w
```

---

❌ Forgetting that commands containing passwords may be stored.

Avoid entering sensitive information directly into the terminal.

---

# ✅ Best Practices

- Use reverse search (`Ctrl + R`) to quickly find previous commands.
- Use `history | grep keyword` to locate specific commands.
- Configure history size using `HISTSIZE` and `HISTFILESIZE`.
- Avoid storing sensitive commands in history.

---

# 🔒 Security Considerations

Command history may contain:

- Passwords
- API tokens
- Database connection strings
- SSH commands
- Administrative operations

Be cautious when sharing your history or `.bash_history` file.

---

# 🚀 Performance Notes

Command history has negligible performance overhead, even with thousands of stored entries.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `alias` | Creates command shortcuts |
| `env` | Displays environment variables |
| `export` | Exports variables |
| `fc` | Edit and re-execute commands from history |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `history` | Displays command history |
| `fc` | Edits and reruns previous commands |
| `Ctrl + R` | Interactive reverse history search |

---

# 🧪 Practice Exercises

### Beginner

Display the last 10 commands.

---

### Intermediate

Search your history for commands containing `git`.

---

### Advanced

Delete a specific history entry and write the updated history to disk.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `history` command?

**A:** It displays the commands previously executed in the current shell.

---

### Intermediate

**Q:** Where does Bash store command history?

**A:** By default, in the `~/.bash_history` file.

---

### Advanced

**Q:** How would you completely clear your Bash history?

**A:** Run:

```bash
history -c
history -w
```

The first command clears the in-memory history, and the second overwrites the history file with the empty history.

---

# 🛠 Troubleshooting

**Problem:** Commands are not appearing in history.

**Solution:**

Check shell settings such as:

```bash
echo $HISTSIZE
echo $HISTFILE
echo $HISTCONTROL
```

---

**Problem:** History isn't saved after closing the terminal.

**Solution:**

Ensure the shell is configured to write to `~/.bash_history` and that the file has appropriate permissions.

---

# 📚 Official Documentation

- `help history` (Bash built-in)
- Bash Reference Manual

---

# 📖 Further Reading

- Nexora: `alias`
- Nexora: `env`
- Nexora: `export`
- Bash Documentation

---

# 📌 Quick Summary

- `history` displays previously executed shell commands.
- Use `history N` to show the last **N** commands.
- Search history with `history | grep keyword`.
- Re-run commands using `!number` or `!!`.
- Bash stores history in `~/.bash_history`.

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