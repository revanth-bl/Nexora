# Bash Functions

## Overview

Functions are reusable blocks of code in Bash scripts that perform a specific task. They help organize scripts, eliminate repetitive code, improve readability, and make maintenance easier.

Functions can accept arguments, return exit statuses, and access global variables, making them a fundamental feature for writing modular shell scripts.

---

# Why Use Functions?

Functions provide several advantages:

- Reuse code without duplication
- Improve script readability
- Simplify debugging
- Organize complex scripts
- Reduce maintenance effort
- Make scripts modular

---

# Basic Syntax

```bash
function_name() {
    commands
}
```

Or using the `function` keyword:

```bash
function function_name {
    commands
}
```

Both forms are valid, but the first is more commonly used.

---

# Simple Function

```bash
#!/bin/bash

greet() {
    echo "Hello, World!"
}

greet
```

**Output:**

```text
Hello, World!
```

---

# Function with Parameters

```bash
#!/bin/bash

greet() {
    echo "Hello, $1!"
}

greet Alice
```

**Output:**

```text
Hello, Alice!
```

---

# Multiple Parameters

```bash
show_user() {
    echo "Name: $1"
    echo "Age: $2"
}

show_user Alice 25
```

---

# Using All Arguments

```bash
print_all() {
    echo "Arguments: $@"
}

print_all one two three
```

Output:

```text
Arguments: one two three
```

---

# Counting Arguments

```bash
count_args() {
    echo "Number of arguments: $#"
}

count_args one two three
```

Output:

```text
Number of arguments: 3
```

---

# Returning Status Codes

Functions return an **exit status** (0–255).

```bash
check_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}

check_file notes.txt

echo $?
```

---

# Returning Values

Bash functions cannot directly return strings. Instead, use command substitution.

```bash
get_date() {
    date +%F
}

today=$(get_date)

echo "$today"
```

---

# Local Variables

Use `local` to limit a variable's scope.

```bash
calculate() {
    local sum=10
    echo "$sum"
}
```

Without `local`, variables become global.

---

# Global Variables

```bash
name="Linux"

show() {
    echo "$name"
}

show
```

---

# Conditional Logic

```bash
check_number() {
    if [ "$1" -gt 10 ]; then
        echo "Greater than 10"
    else
        echo "10 or less"
    fi
}

check_number 25
```

---

# Loops Inside Functions

```bash
count() {
    for i in {1..5}
    do
        echo "$i"
    done
}

count
```

---

# Reading User Input

```bash
get_name() {
    read -p "Enter your name: " name
    echo "Hello, $name"
}

get_name
```

---

# Calling Functions

Functions must be called by name.

```bash
backup() {
    echo "Backup started..."
}

backup
```

---

# Function Order

Functions should be defined before they are called.

```bash
hello() {
    echo "Hi!"
}

hello
```

---

# Recursive Functions

```bash
countdown() {
    if [ "$1" -le 0 ]; then
        return
    fi

    echo "$1"
    countdown $(( $1 - 1 ))
}

countdown 5
```

---

# Example: File Backup Function

```bash
backup() {
    tar -czf backup.tar.gz "$1"
    echo "Backup created."
}

backup Documents
```

---

# Example: User Check

```bash
user_exists() {
    id "$1" &>/dev/null
}

if user_exists alice
then
    echo "User exists"
else
    echo "User not found"
fi
```

---

# Example: Logging Function

```bash
log() {
    echo "[$(date)] $1"
}

log "Server started"
```

---

# Best Practices

- Give functions descriptive names.
- Keep each function focused on one task.
- Use `local` variables whenever possible.
- Return meaningful exit codes.
- Validate function arguments.
- Avoid global variables unless necessary.
- Add comments for complex functions.
- Reuse functions instead of copying code.

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Using global variables everywhere | Use `local` variables |
| Very large functions | Split into smaller functions |
| Ignoring exit codes | Check function return values |
| Repeating code | Create reusable functions |
| Poor naming | Use descriptive function names |

---

# Function Cheat Sheet

| Syntax | Purpose |
|--------|---------|
| `func() { }` | Define a function |
| `func` | Call a function |
| `$1` | First argument |
| `$2` | Second argument |
| `$@` | All arguments |
| `$#` | Number of arguments |
| `local var=value` | Local variable |
| `return 0` | Success |
| `return 1` | Failure |
| `$(func)` | Capture function output |

---

# Summary

Bash functions make scripts modular, reusable, and easier to maintain. They allow developers and system administrators to organize code into logical units, pass parameters, return status codes, and simplify automation tasks.

---

# Related Topics

- Bash
- Shell Scripting
- Variables
- Loops
- Conditional Statements
- Input and Output
- Automation
- Linux Commands
- Cron
- DevOps