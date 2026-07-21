# crontab

> Schedule commands or scripts to run automatically at specified times and intervals.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Scheduling |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 9 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`crontab` is used to create, view, edit, and manage **cron jobs**—scheduled tasks that run automatically at predefined times. It is one of the most widely used Linux utilities for automating repetitive administrative and maintenance tasks.

The name **crontab** comes from **cron table**, which stores the schedule of jobs for each user.

- **What does it do?** Schedules commands or scripts to run automatically.
- **Why does it exist?** To automate repetitive tasks without manual intervention.
- **When is it commonly used?** Backups, log cleanup, database maintenance, report generation, and system monitoring.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Create and edit cron jobs
- Understand cron scheduling syntax
- View and remove scheduled jobs
- Automate common Linux tasks
- Troubleshoot cron-related issues

---

# ⚙️ Syntax

```bash
crontab [options]
```

---

# 📝 Parameters

`crontab` primarily uses options rather than positional parameters.

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-e` | Edit the current user's crontab |
| `-l` | List scheduled cron jobs |
| `-r` | Remove the current user's crontab |
| `-u user` | Manage another user's crontab (root only) |
| `-i` | Prompt before removing a crontab |

---

# 💻 Basic Examples

## Example 1

```bash
crontab -e
```

Create or edit your cron jobs.

---

## Example 2

```bash
crontab -l
```

Display all scheduled jobs for the current user.

---

## Example 3

```bash
crontab -r
```

Delete all scheduled jobs.

---

## Example 4

```bash
crontab -i -r
```

Prompt before deleting the crontab.

---

## Example 5

Run a backup script every day at 2:30 AM:

```cron
30 2 * * * /home/revanth/scripts/backup.sh
```

---

# 📤 Example Output

```text
$ crontab -l

# Run backup every day at 2:30 AM
30 2 * * * /home/user/scripts/backup.sh

# Clean logs every Sunday at midnight
0 0 * * 0 /home/user/scripts/cleanup.sh
```

---

# 🌍 Real-world Use Cases

- Daily database backups
- Rotating and cleaning log files
- Sending scheduled email reports
- Running maintenance scripts
- Automatically updating application caches

---

# 🧠 How It Works

The **cron daemon (`cron` or `crond`)** continuously runs in the background.

Every minute, it checks each user's crontab for jobs that match the current date and time. If a schedule matches, the specified command or script is executed.

A cron entry has five scheduling fields followed by the command:

```text
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week (0–7, where 0 and 7 are Sunday)
│ │ │ └──── Month (1–12)
│ │ └────── Day of month (1–31)
│ └──────── Hour (0–23)
└────────── Minute (0–59)
```

Example:

```cron
0 3 * * 1
```

Runs every Monday at **3:00 AM**.

---

# ⚠️ Common Mistakes

❌ Forgetting to use absolute paths.

Cron jobs run with a limited environment, so commands like `python` or relative file paths may fail.

---

❌ Assuming cron uses your shell environment.

Environment variables such as `PATH` may differ from your interactive shell.

---

❌ Editing the crontab file directly.

Always use:

```bash
crontab -e
```

---

# ✅ Best Practices

- Use absolute paths for commands and scripts.
- Redirect output to a log file for debugging.
- Test scripts manually before scheduling them.
- Comment cron jobs to describe their purpose.
- Use `crontab -l` periodically to review scheduled tasks.

---

# 🔒 Security Considerations

Only trusted scripts should be scheduled.

Avoid storing passwords or sensitive information directly in cron jobs.

Restrict write permissions on scripts executed by cron.

---

# 🚀 Performance Notes

Cron itself has minimal overhead.

Poorly written or resource-intensive scheduled jobs can impact system performance, especially if multiple jobs run simultaneously.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `systemctl` | Manage the cron service |
| `at` | Schedule a one-time task |
| `systemd timers` | Modern alternative to cron |
| `journalctl` | View cron-related logs on systemd systems |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `crontab` | Repeating scheduled tasks |
| `at` | One-time scheduled task |
| `systemd timers` | Advanced scheduling integrated with systemd |

---

# 🧪 Practice Exercises

### Beginner

Create a cron job that prints "Hello" every hour.

---

### Intermediate

Schedule a backup script to run every night at 2:00 AM.

---

### Advanced

Create a cron job that runs every weekday at 8:30 AM and logs its output to a file.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of `crontab`?

**A:** It schedules commands or scripts to run automatically at specified times.

---

### Intermediate

**Q:** Explain the five time fields in a cron expression.

**A:** They represent minute, hour, day of month, month, and day of week.

---

### Advanced

**Q:** Why do cron jobs sometimes fail even though the script works manually?

**A:** Cron runs with a limited environment and may not have the same `PATH`, working directory, or environment variables as an interactive shell. Using absolute paths and setting required variables usually resolves the issue.

---

# 🛠 Troubleshooting

**Problem:** Cron job doesn't run.

**Cause:**

- Incorrect schedule
- Wrong file permissions
- Missing executable permission
- Relative paths
- Cron service not running

**Solution:**

- Verify the cron entry with `crontab -l`
- Check that the script is executable
- Use absolute paths
- Ensure the cron service is running
- Review system logs for cron-related errors

---

# 📚 Official Documentation

- `man crontab`
- `man cron`

---

# 📖 Further Reading

- Nexora: `systemctl`
- Nexora: `journalctl`
- Linux cron documentation
- systemd Timers

---

# 📌 Quick Summary

- `crontab` manages scheduled tasks.
- Use `crontab -e` to edit jobs.
- Jobs are defined using five time fields.
- Always use absolute paths in cron jobs.
- Cron is ideal for recurring automation tasks.

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