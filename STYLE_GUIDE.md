# 📚 Nexora Style Guide

> This document defines the writing standards for every page in Nexora.

Following these guidelines ensures every document remains consistent, professional, and easy to navigate.

---

# 🎯 Philosophy

Nexora is designed to be:

- Practical
- Beginner-friendly
- Professional
- Consistent
- Community-driven
- Open Source

Every page should answer not only **how**, but also **why**, **when**, and **where**.

---

# 📁 File Naming

Use:

```
lowercase-with-hyphens.md
```

✅ Correct

```
file-management.md
system-services.md
best-practices.md
```

❌ Incorrect

```
FileManagement.md
File_Management.md
File Management.md
```

---

# 📑 Heading Structure

Use headings consistently.

```
# Title

## Overview

## Learning Objectives

## Syntax

## Examples

## Best Practices

## Troubleshooting

## Official Resources
```

Avoid skipping heading levels.

---

# 😀 Emoji Usage

Emojis improve scanning but should be used consistently.

| Emoji | Meaning |
|--------|----------|
| 📖 | Overview |
| 🎯 | Objectives |
| ⚙ | Syntax |
| 💻 | Examples |
| 🌍 | Real-world Use Cases |
| 🧠 | Explanation |
| ⚠ | Common Mistakes |
| ✅ | Best Practices |
| 🔒 | Security |
| 🚀 | Performance |
| 🧩 | Related Topics |
| 🧪 | Exercises |
| 💼 | Interview Questions |
| 🛠 | Troubleshooting |
| 📚 | Resources |
| 📌 | Summary |

Do not overuse emojis.

---

# 💻 Code Blocks

Always specify the language.

Example:

```bash
ls -la
```

```python
print("Hello")
```

Never use plain triple backticks unless no language exists.

---

# 📊 Tables

Use Markdown tables.

Example:

| Option | Description |
|---------|-------------|
| `-a` | Show hidden files |

Keep tables aligned and readable.

---

# 🔗 Internal Links

Use relative paths.

Example:

```md
[ls](./ls.md)

[File Management](../README.md)
```

Never use absolute GitHub URLs for internal documentation.

---

# 🌐 External References

Prefer official documentation.

Priority:

1. Official Documentation
2. Standards (RFC, POSIX, ISO)
3. Trusted organizations
4. Community resources

Avoid linking to random blogs.

---

# ✍ Writing Style

Write in plain English.

Use:

- Short paragraphs
- Active voice
- Practical explanations
- Real-world examples

Avoid unnecessary jargon.

Explain technical terms before using them.

---

# 🎯 Every Command Page Must Include

- Metadata
- Overview
- Learning Objectives
- Syntax
- Parameters
- Options
- Examples
- Output
- Real-world Use Cases
- How It Works
- Common Mistakes
- Best Practices
- Security
- Performance
- Related Commands
- Comparisons
- Practice Exercises
- Interview Questions
- Troubleshooting
- Official Resources
- Quick Summary

---

# 📖 Every Concept Page Must Include

- Definition
- Why it exists
- How it works
- Architecture
- Examples
- Advantages
- Limitations
- Best Practices
- Common Misconceptions
- Related Concepts

---

# 🧪 Every Lab Must Include

- Objectives
- Prerequisites
- Steps
- Expected Output
- Verification
- Cleanup
- Challenge Tasks

---

# 💼 Every Project Must Include

- Overview
- Requirements
- Architecture
- Folder Structure
- Implementation
- Testing
- Improvements
- References

---

# 📄 Markdown Rules

Always use:

- Bullet lists
- Tables
- Code blocks
- Relative links

Avoid:

- Raw HTML (unless necessary)
- Huge paragraphs
- Deep nesting
- Inconsistent formatting

---

# 🤝 Contribution Standard

Before submitting a Pull Request:

- Check spelling and grammar.
- Verify commands.
- Test code examples.
- Add official references.
- Follow the documentation template.
- Keep formatting consistent.

---

# 🚀 Documentation Principle

Every page should answer these questions:

1. What is it?
2. Why does it exist?
3. When should I use it?
4. When should I avoid it?
5. How does it work?
6. What are the best practices?
7. What mistakes should I avoid?
8. Where can I learn more?

If a page answers these questions clearly, it meets the Nexora documentation standard.