# unzip

> Extract, list, and test ZIP archive files in Linux.

> **Note:** `unzip` is used to extract files from ZIP archives. It works with archives created by the `zip` command and is commonly used for downloading software, documents, and cross-platform file sharing.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Compression |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`unzip` is a command-line utility used to extract files from **ZIP archives**. ZIP is one of the most widely supported archive formats and is compatible with Linux, Windows, and macOS.

Besides extracting files, `unzip` can list archive contents, test archive integrity, and selectively extract files.

- **What does it do?** Extracts files from ZIP archives.
- **Why does it exist?** To provide an easy way to access compressed ZIP files.
- **When is it commonly used?** Extracting downloaded software, project archives, backups, and documents.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Extract ZIP archives
- List archive contents
- Extract files to a specific directory
- Test ZIP archive integrity
- Extract selected files

---

# ⚙️ Syntax

```bash
unzip [OPTIONS] ARCHIVE.zip
```

---

# 📝 Parameters

| Parameter | Description | Required |
|-----------|-------------|----------|
| `ARCHIVE.zip` | ZIP archive to extract | Yes |

---

# 🔧 Common Options

| Option | Description |
|---------|-------------|
| `-l` | List archive contents |
| `-d DIR` | Extract to a specific directory |
| `-o` | Overwrite existing files without prompting |
| `-n` | Never overwrite existing files |
| `-t` | Test archive integrity |
| `-q` | Quiet mode |
| `-j` | Ignore directory structure (junk paths) |

---

# 💻 Basic Examples

## Example 1

Extract a ZIP archive.

```bash
unzip archive.zip
```

---

## Example 2

Extract to another directory.

```bash
unzip archive.zip -d /home/user/extracted
```

---

## Example 3

List archive contents.

```bash
unzip -l archive.zip
```

---

## Example 4

Overwrite existing files.

```bash
unzip -o archive.zip
```

---

## Example 5

Test archive integrity.

```bash
unzip -t archive.zip
```

---

## Example 6

Extract only a specific file.

```bash
unzip archive.zip README.md
```

---

# 📤 Example Output

```text
$ unzip archive.zip

Archive: archive.zip
  inflating: README.md
  inflating: docs/install.md
  inflating: src/main.c
```

---

# 🌍 Real-world Use Cases

- Extracting downloaded software
- Opening project archives from GitHub
- Restoring backups
- Extracting reports and documents
- Working with cross-platform ZIP files

---

# 🧠 How It Works

`unzip` reads the ZIP archive and recreates the files and directories stored inside it.

```text
archive.zip
      │
      ▼
    unzip
      │
      ▼
Extracted Files
```

If directory paths are stored in the archive, they are recreated automatically unless `-j` is used.

---

# ⚠️ Common Mistakes

❌ Trying to extract a non-ZIP archive.

Example:

```bash
unzip backup.tar.gz
```

This will fail because `.tar.gz` archives should be extracted using:

```bash
tar -xzf backup.tar.gz
```

---

❌ Accidentally overwriting files.

Use:

```bash
unzip -n archive.zip
```

to prevent overwriting existing files.

---

❌ Extracting into the wrong directory.

Specify a destination:

```bash
unzip archive.zip -d project/
```

---

# ✅ Best Practices

- List archive contents before extraction.
- Extract archives into dedicated directories.
- Test important archives before use.
- Avoid overwriting existing files unless necessary.
- Verify archives obtained from untrusted sources.

---

# 🔒 Security Considerations

Be cautious when extracting ZIP files from unknown sources.

Potential risks include:

- Malicious files
- Unexpected directory structures
- Overwriting important files

Inspect the archive first:

```bash
unzip -l archive.zip
```

---

# 🚀 Performance Notes

`unzip` is lightweight and efficient.

Extraction speed depends mainly on:

- Archive size
- Compression level
- Storage device performance

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `zip` | Create ZIP archives |
| `tar` | Archive files |
| `gzip` | Compress files |
| `gunzip` | Decompress Gzip files |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `unzip` | Extract ZIP archives |
| `zip` | Create ZIP archives |
| `tar` | Archive multiple files |
| `gunzip` | Decompress Gzip files |

---

# 🧪 Practice Exercises

### Beginner

Extract a ZIP archive into the current directory.

---

### Intermediate

Extract a ZIP archive into a folder named `backup`.

---

### Advanced

List the contents of a ZIP archive, test its integrity, and extract only one file from it.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is the purpose of the `unzip` command?

**A:** It extracts files from ZIP archives.

---

### Intermediate

**Q:** How do you extract a ZIP archive into another directory?

**A:**

```bash
unzip archive.zip -d destination/
```

---

### Advanced

**Q:** How can you check the contents of a ZIP archive without extracting it?

**A:**

```bash
unzip -l archive.zip
```

This lists all files stored in the archive.

---

# 🛠 Troubleshooting

**Problem:** `unzip: command not found`

**Solution:**

Install the package:

Ubuntu/Debian:

```bash
sudo apt install unzip
```

RHEL/CentOS:

```bash
sudo yum install unzip
```

---

**Problem:** Files were overwritten.

**Solution:**

Use:

```bash
unzip -n archive.zip
```

to prevent overwriting existing files.

---

# 📚 Official Documentation

- `man unzip`
- Info-ZIP Documentation

---

# 📖 Further Reading

- Nexora: `zip`
- Nexora: `tar`
- Nexora: `gzip`
- Info-ZIP Project Documentation

---

# 📌 Quick Summary

- `unzip` extracts ZIP archives.
- Use `-d` to specify an extraction directory.
- Use `-l` to list archive contents.
- Use `-t` to test archive integrity.
- It is the standard Linux utility for working with ZIP files.

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