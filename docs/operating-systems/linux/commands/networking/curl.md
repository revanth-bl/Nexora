# curl

> Transfer data to or from a server using supported protocols such as HTTP, HTTPS, FTP, and more.

---

## 📋 Metadata

| Property | Value |
|----------|-------|
| Category | Networking |
| Technology | Linux |
| Difficulty | Intermediate |
| Reading Time | 8 min |
| Last Updated | 2026-07-09 |
| Author | Revanth B L |
| Reviewed By | |

---

# 📖 Overview

`curl` (Client URL) is a command-line tool used to transfer data between a client and a server. It supports dozens of protocols including HTTP, HTTPS, FTP, SCP, SFTP, SMTP, LDAP, and more.

- **What does it do?** Sends and receives data over network protocols.
- **Why does it exist?** To interact with web servers, APIs, and remote services directly from the command line.
- **When is it commonly used?** API testing, downloading files, debugging HTTP requests, authentication, automation scripts, and DevOps workflows.

---

# 🎯 Learning Objectives

After reading this guide, you will be able to:

- Download files from the internet
- Send HTTP GET and POST requests
- Work with REST APIs
- Add authentication headers
- Upload files
- Debug HTTP responses

---

# ⚙️ Syntax

```bash
curl [options] <URL>
```

---

# 📝 Parameters

| Parameter | Description | Required |
|------------|-------------|----------|
| URL | Destination URL | Yes |

---

# 🔧 Options / Flags

| Option | Description |
|---------|-------------|
| `-O` | Save file using remote filename |
| `-o` | Save output with custom filename |
| `-L` | Follow redirects |
| `-I` | Fetch headers only |
| `-X` | Specify HTTP method |
| `-H` | Add request header |
| `-d` | Send request body |
| `-u` | Username and password authentication |
| `-k` | Ignore SSL certificate validation |
| `-v` | Verbose output |
| `--compressed` | Request compressed response |

---

# 💻 Basic Examples

## Example 1

```bash
curl https://example.com
```

Downloads and displays the webpage.

---

## Example 2

```bash
curl -O https://example.com/file.zip
```

Downloads the file using its original filename.

---

## Example 3

```bash
curl -L https://example.com
```

Follows HTTP redirects automatically.

---

## Example 4

```bash
curl -I https://example.com
```

Displays only the HTTP response headers.

---

## Example 5

```bash
curl -X POST https://api.example.com/users \
-H "Content-Type: application/json" \
-d '{"name":"Alice"}'
```

Sends a POST request with JSON data.

---

# 📤 Example Output

```text
HTTP/1.1 200 OK
Date: Wed, 09 Jul 2026
Content-Type: application/json
Content-Length: 235

{
  "status":"success"
}
```

---

# 🌍 Real-world Use Cases

- Testing REST APIs
- Downloading software packages
- Monitoring website availability
- Uploading files to cloud services
- Automating deployment scripts
- Debugging HTTP requests

---

# 🧠 How It Works

`curl` opens a network connection to the specified URL using the requested protocol. It sends the request, receives the response, and prints or saves the returned data.

Unlike a browser, `curl` provides full control over headers, request methods, cookies, authentication, and response handling, making it a favorite tool for developers and system administrators.

---

# ⚠️ Common Mistakes

❌ Forgetting `-L` when downloading from URLs that redirect.

❌ Using `-k` permanently instead of fixing certificate issues.

❌ Exposing API tokens directly in shell history.

---

# ✅ Best Practices

- Prefer HTTPS whenever possible.
- Store API tokens in environment variables.
- Use `-L` when downloading files.
- Use `-I` to inspect headers before downloading.
- Use `-v` only while debugging.

---

# 🔒 Security Considerations

Avoid passing passwords or API keys directly in commands because they may be stored in shell history or visible to other users through process listings.

Prefer authentication tokens stored securely in environment variables or configuration files.

---

# 🚀 Performance Notes

`curl` is lightweight and efficient. For large downloads, consider using resume support (`-C -`) if the connection is interrupted.

---

# 🧩 Related Commands

| Command | Relationship |
|----------|--------------|
| wget | Download files |
| ssh | Secure remote login |
| scp | Secure file transfer |
| rsync | Efficient file synchronization |
| ping | Network connectivity testing |

---

# 🔄 Comparison

| Command | Difference |
|----------|------------|
| curl | API requests and data transfer |
| wget | Primarily downloading files |
| scp | Secure file copy |
| rsync | Incremental synchronization |

---

# 🧪 Practice Exercises

### Beginner

Download the homepage of `https://example.com`.

---

### Intermediate

Save a file locally while keeping its original filename.

---

### Advanced

Send a POST request with a JSON payload to a test API.

---

# 💼 Real Interview Questions

### Beginner

**Q:** What is `curl` used for?

**A:** It is used to transfer data between a client and a server using various network protocols.

---

### Intermediate

**Q:** What is the difference between `curl` and `wget`?

**A:** `curl` is designed for data transfer and API interaction, while `wget` focuses primarily on downloading files recursively.

---

### Advanced

**Q:** Why is `curl` commonly used in DevOps pipelines?

**A:** It allows automation scripts to interact with APIs, download artifacts, upload files, and validate web services without requiring a graphical interface.

---

# 🛠 Troubleshooting

**Problem:** SSL certificate verification failed.

**Cause:** The server certificate is invalid or missing trusted CA information.

**Solution:** Verify the certificate configuration. Avoid using `-k` except for temporary testing.

---

# 📚 Official Documentation

- `man curl`
- https://curl.se/docs/
- https://everything.curl.dev/

---

# 📖 Further Reading

- Nexora: `wget`
- Nexora: `ssh`
- Nexora: HTTP Concepts

---

# 📌 Quick Summary

- `curl` transfers data between clients and servers.
- Supports HTTP, HTTPS, FTP, SCP, SFTP, and many other protocols.
- Commonly used for APIs, downloads, and automation.
- Essential tool for developers, DevOps engineers, and system administrators.

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