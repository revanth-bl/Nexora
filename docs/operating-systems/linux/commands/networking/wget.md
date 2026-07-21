# wget

> Download files from the web directly from the command line using HTTP, HTTPS, and FTP.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Beginner |
| Reading Time | 7 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`wget` is a non-interactive command-line utility used to download files from the internet. It supports HTTP, HTTPS, and FTP protocols and can resume interrupted downloads, making it one of the most popular tools for downloading software, datasets, backups, and web content.

Unlike a web browser, `wget` is designed for automation and scripting.

- **What does it do?** Downloads files from remote servers.
- **Why does it exist?** To provide reliable, scriptable file downloads from the command line.
- **When is it commonly used?** Downloading software packages, backups, datasets, installation scripts, and mirroring websites.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Download files from the internet
- Resume interrupted downloads
- Save files with custom names
- Download entire websites recursively
- Use authentication when required

---

# ⚙️ Syntax

```bash
wget [options] URL
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| `URL` | The file or webpage to download | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-O <file>` | Save output using a custom filename |
| `-c` | Resume an interrupted download |
| `-P <dir>` | Download into a specific directory |
| `-q` | Quiet mode (minimal output) |
| `-nv` | Less verbose output |
| `-r` | Download recursively |
| `--limit-rate=<speed>` | Limit download speed |
| `--user` | Specify username for authentication |
| `--password` | Specify password for authentication |

---

# 💻 Basic Examples

## Example 1

```bash
wget https://example.com/file.zip
```

Download a file to the current directory.

---

## Example 2

```bash
wget -O ubuntu.iso https://example.com/latest.iso
```

Download a file and save it with a custom name.

---

## Example 3

```bash
wget -c https://example.com/bigfile.iso
```

Resume a previously interrupted download.

---

## Example 4

```bash
wget -P ~/Downloads https://example.com/image.png
```

Download a file into a specific directory.

---

## Example 5

```bash
wget -r https://example.com/docs/
```

Recursively download a website.

---

# 📤 Example Output

```text
--2026-07-09--
Resolving example.com...
Connecting to example.com...
HTTP request sent, awaiting response... 200 OK
Length: 10485760 (10M)
Saving to: 'file.zip'

100%[==========================>] 10.0M  12.4MB/s    in 0.8s

'file.zip' saved
```

Explanation:

- URL resolved successfully.
- Server returned **200 OK**.
- File downloaded successfully.
- Progress bar shows download status.

---

# 🌍 Real-world Use Cases

- Downloading Linux ISO images
- Downloading datasets for machine learning
- Installing software from official repositories
- Downloading backups from remote servers
- Automating scheduled downloads using cron jobs

---

# 🧠 How It Works

`wget` sends an HTTP, HTTPS, or FTP request to the remote server.

After receiving the response, it streams the file directly to disk instead of loading it into memory.

It supports automatic retries, download resumption, recursive retrieval, and authentication.

---

# ⚠️ Common Mistakes

❌ Forgetting the `-c` option when resuming large downloads.

Without it, the download starts from the beginning.

---

❌ Downloading files without verifying the source.

Always download software from trusted websites and verify checksums when available.

---

❌ Using recursive downloads on large websites.

This can consume significant bandwidth and storage.

---

# ✅ Best Practices

- Use HTTPS whenever possible.
- Resume interrupted downloads with `-c`.
- Verify downloaded files using checksums (SHA256, SHA512, etc.).
- Limit bandwidth with `--limit-rate` if downloading on shared networks.
- Use `-O` for meaningful filenames.

---

# 🔒 Security Considerations

Downloading files from untrusted sources may expose your system to malware.

Always:

- Download from official websites.
- Verify digital signatures or checksums.
- Avoid executing downloaded scripts without reviewing them.

---

# 🚀 Performance Notes

`wget` is lightweight and suitable for automated scripts.

It efficiently handles large downloads and network interruptions through download resumption.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| `curl` | Transfers data to and from servers |
| `scp` | Secure file transfer over SSH |
| `rsync` | Synchronize files efficiently |
| `tar` | Extract downloaded archives |
| `unzip` | Extract ZIP archives |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| `wget` | Primarily downloads files |
| `curl` | Transfers data using many protocols and supports API requests |
| `scp` | Copies files securely between remote systems |

---

# 🧪 Practice Exercises

### Beginner

Download a file from a public URL.

---

### Intermediate

Resume an interrupted download using `-c`.

---

### Advanced

Mirror a small documentation website using recursive download.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is `wget` used for?

**A:** It downloads files from remote servers using HTTP, HTTPS, or FTP.

---

### Intermediate

**Q:** How do you resume an interrupted download?

**A:**

```bash
wget -c URL
```

---

### Advanced

**Q:** When would you choose `wget` instead of `curl`?

**A:** `wget` is preferred for downloading files, recursive website downloads, and download resumption, while `curl` is better suited for APIs and transferring data using many protocols.

---

# 🛠 Troubleshooting

**Problem:** `404 Not Found`

**Cause:**

The requested file or URL does not exist.

**Solution:**

Verify the URL and ensure the resource is still available.

---

**Problem:** `Permission denied`

**Cause:**

You do not have write permission in the destination directory.

**Solution:**

Download to a writable directory or use appropriate permissions.

---

# 📚 Official Documentation

- `man wget`
- https://www.gnu.org/software/wget/

---

# 📖 Further Reading

- Nexora: `curl`
- Nexora: `scp`
- Nexora: `rsync`
- GNU Wget Manual

---

# 📌 Quick Summary

- `wget` downloads files from HTTP, HTTPS, and FTP servers.
- Use `-c` to resume interrupted downloads.
- Use `-O` to rename downloaded files.
- Supports recursive website downloads with `-r`.
- Commonly used in automation and server administration.

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