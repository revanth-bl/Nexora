# Shell Scripting Best Practices

## Overview

Shell scripting is a powerful way to automate repetitive tasks, manage systems, and simplify administration in Linux. While shell scripts are easy to write, poorly written scripts can be difficult to maintain, debug, and secure.

Following best practices helps you create reliable, readable, and maintainable shell scripts.

---

# Why Follow Shell Scripting Best Practices?

Good scripting practices help you:

- Improve code readability
- Reduce bugs and errors
- Increase script reliability
- Simplify maintenance
- Enhance security
- Make scripts reusable

---

# 1. Start with a Shebang

Always begin a script with the appropriate shebang.

Example:

```bash
#!/bin/bash
```

or

```bash
#!/usr/bin/env bash
```

This tells the operating system which interpreter should execute the script.

---

# 2. Use Meaningful Variable Names

Choose descriptive names.

Good:

```bash
backup_directory="/home/user/backups"
```

Poor:

```bash
x="/home/user/backups"
```

Clear names improve readability.

---

# 3. Quote Variables

Always quote variables unless word splitting is intended.

Good:

```bash
echo "$filename"
```

Poor:

```bash
echo $filename
```

Quoting prevents issues with spaces and special characters.

---

# 4. Enable Safe Script Options

At the beginning of important scripts, consider using:

```bash
set -euo pipefail
```

These options help by:

- Stopping on errors (`-e`)
- Preventing use of undefined variables (`-u`)
- Detecting failures in pipelines (`pipefail`)

---

# 5. Add Comments Where Necessary

Explain **why** something is being done, not just **what**.

Example:

```bash
# Remove backup files older than 30 days
find backups/ -mtime +30 -delete
```

Avoid excessive or obvious comments.

---

# 6. Keep Scripts Modular

Break large scripts into functions.

Example:

```bash
backup_files() {
    echo "Creating backup..."
}
```

Functions improve readability and reusability.

---

# 7. Check Command Exit Status

Always verify whether important commands succeed.

Example:

```bash
cp file.txt backup/

if [ $? -ne 0 ]; then
    echo "Backup failed."
    exit 1
fi
```

Or use:

```bash
if cp file.txt backup/; then
    echo "Success"
else
    echo "Failed"
fi
```

---

# 8. Validate User Input

Never assume user input is valid.

Example:

```bash
read age

if [[ "$age" =~ ^[0-9]+$ ]]; then
    echo "Valid age."
else
    echo "Invalid input."
fi
```

Input validation improves reliability and security.

---

# 9. Avoid Hardcoding Values

Instead of:

```bash
backup="/home/alice/backups"
```

Use variables:

```bash
BACKUP_DIR="$HOME/backups"
```

This makes scripts easier to modify.

---

# 10. Use Constants for Configuration

Place configuration values at the beginning of the script.

Example:

```bash
LOG_FILE="/var/log/backup.log"
BACKUP_DIR="/home/user/backups"
```

This centralizes configuration and improves maintainability.

---

# 11. Use Functions

Example:

```bash
log_message() {
    echo "$(date): $1"
}
```

Functions reduce code duplication and make scripts easier to understand.

---

# 12. Handle Errors Gracefully

Instead of allowing scripts to fail silently:

```bash
mkdir backup || {
    echo "Failed to create directory."
    exit 1
}
```

Provide clear error messages to users.

---

# 13. Use Temporary Files Safely

Create temporary files using:

```bash
mktemp
```

Avoid predictable file names that could create security risks.

---

# 14. Avoid Running as Root

Run scripts as a regular user whenever possible.

If administrative privileges are required:

```bash
sudo ./script.sh
```

Avoid executing entire scripts as the root user unless absolutely necessary.

---

# 15. Test Scripts Before Deployment

Before using scripts in production:

- Test with sample data.
- Check edge cases.
- Verify error handling.
- Review expected outputs.

Testing prevents unexpected failures.

---

# 16. Follow Consistent Formatting

Use:

- Consistent indentation
- Blank lines between logical sections
- Meaningful spacing
- Descriptive function names

Readable scripts are easier to maintain.

---

# 17. Keep Scripts Small

Instead of one massive script:

- Create multiple focused scripts.
- Separate reusable functions into libraries when appropriate.

Small scripts are easier to debug and maintain.

---

# Useful Practices

Enable debugging:

```bash
bash -x script.sh
```

Check syntax:

```bash
bash -n script.sh
```

Make executable:

```bash
chmod +x script.sh
```

Run script:

```bash
./script.sh
```

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Omitting the shebang | Start every script with a shebang |
| Using unclear variable names | Use descriptive names |
| Forgetting quotes around variables | Quote variables consistently |
| Ignoring command failures | Check exit statuses |
| Hardcoding values | Use variables and configuration constants |
| Writing one huge script | Split logic into functions |
| Running everything as root | Use `sudo` only when needed |
| Skipping testing | Test scripts before deployment |

---

# Best Practices Checklist

- Begin scripts with a shebang.
- Use meaningful variable names.
- Quote variables.
- Enable safe shell options (`set -euo pipefail`).
- Organize code into functions.
- Validate user input.
- Check command exit statuses.
- Handle errors gracefully.
- Use temporary files safely.
- Avoid unnecessary root execution.
- Keep scripts modular and readable.
- Test scripts thoroughly.

---

# Key Takeaways

- Well-written shell scripts are easier to maintain, debug, and reuse.
- Good scripting practices improve reliability, readability, and security.
- Error handling, input validation, and consistent formatting are essential for robust automation.
- Small, modular scripts are generally easier to understand and maintain than large monolithic scripts.

---

## Related Topics

- Shell
- Linux Commands
- Bash
- Process Management
- File Management
- System Administration
- Automation
- Best Practices