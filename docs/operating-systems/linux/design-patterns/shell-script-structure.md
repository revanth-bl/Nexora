# Shell Script Structure

## Overview

A well-structured shell script is easier to read, debug, maintain, and reuse. Following a consistent structure helps organize code logically, making scripts more reliable and suitable for automation, system administration, and DevOps workflows.

Whether writing a simple utility or a complex deployment script, a clear structure improves readability and reduces errors.

---

# Basic Shell Script Structure

A typical shell script consists of the following sections:

```text
Shebang
│
├── Comments
│
├── Variable Definitions
│
├── Functions
│
├── Main Logic
│
├── Error Handling
│
└── Exit Status
```

---

# 1. Shebang

The first line specifies which interpreter should execute the script.

```bash
#!/bin/bash
```

Alternative:

```bash
#!/usr/bin/env bash
```

The second approach is more portable across different Linux distributions.

---

# 2. Script Comments

Comments describe the script's purpose and usage.

```bash
#!/bin/bash

# Backup Script
# Author: John Doe
# Description: Creates a compressed backup of a directory.
```

Use comments to explain complex logic rather than obvious commands.

---

# 3. Variable Definitions

Define configuration variables near the top of the script.

```bash
SOURCE="/home/user/Documents"
DESTINATION="/backup"
DATE=$(date +%F)
```

Using variables makes scripts easier to modify.

---

# 4. Functions

Group reusable code into functions.

```bash
backup() {
    tar -czf "$DESTINATION/backup-$DATE.tar.gz" "$SOURCE"
}
```

Benefits:

- Reusability
- Better organization
- Easier maintenance

---

# 5. Input Validation

Validate user input before executing operations.

```bash
if [ $# -ne 1 ]; then
    echo "Usage: $0 <directory>"
    exit 1
fi
```

This prevents unexpected errors.

---

# 6. Main Logic

The main section executes the script's primary functionality.

```bash
echo "Starting backup..."

backup

echo "Backup completed."
```

Keep the main logic concise by delegating tasks to functions.

---

# 7. Error Handling

Check command success using exit statuses.

```bash
cp file.txt backup/

if [ $? -ne 0 ]; then
    echo "Copy failed."
    exit 1
fi
```

Or use logical operators:

```bash
cp file.txt backup/ || exit 1
```

---

# 8. Cleanup

Remove temporary files after processing.

```bash
rm -f /tmp/tempfile
```

Cleanup prevents unnecessary storage usage.

---

# 9. Exit Status

Exit with an appropriate status code.

```bash
exit 0
```

Common exit codes:

| Code | Meaning |
|------|---------|
| 0 | Success |
| 1 | General error |
| 2 | Incorrect usage |
| 126 | Permission denied |
| 127 | Command not found |

---

# Complete Example

```bash
#!/bin/bash

# Backup Script

SOURCE="/home/user/Documents"
DESTINATION="/backup"
DATE=$(date +%F)

backup() {
    tar -czf "$DESTINATION/backup-$DATE.tar.gz" "$SOURCE"
}

echo "Starting backup..."

backup

if [ $? -eq 0 ]; then
    echo "Backup successful."
else
    echo "Backup failed."
    exit 1
fi

exit 0
```

---

# Recommended Script Layout

```text
#!/bin/bash

Comments

Constants

Variables

Functions

Input Validation

Main Program

Cleanup

Exit
```

---

# Best Practices

- Always include a shebang.
- Use meaningful variable names.
- Keep functions small and focused.
- Validate user input.
- Check command exit statuses.
- Quote variables to prevent word splitting.
- Use comments for complex logic.
- End scripts with meaningful exit codes.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| No shebang | Specify the interpreter |
| Hardcoded values | Use variables |
| Repeated code | Create reusable functions |
| Ignoring errors | Check exit statuses |
| Unquoted variables | Quote variables consistently |
| Large monolithic scripts | Break into smaller functions |

---

# Real-World Examples

- Automated backup scripts
- User account provisioning
- Log rotation automation
- Package installation scripts
- Deployment pipelines
- System health checks
- Scheduled maintenance tasks
- Server initialization scripts

---

# Summary

A consistent shell script structure improves readability, maintainability, and reliability. By organizing scripts into logical sections—such as variables, functions, validation, main logic, and error handling—you can create robust automation solutions that are easier to debug, extend, and reuse.

---

# Related Topics

- Bash
- Bash Functions
- Shell Scripting
- Variables
- Conditional Statements
- Loops
- Automation
- Cron
- Configuration Management
- Linux Commands