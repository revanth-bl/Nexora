# Linux Security Best Practices

## Overview

Security is a fundamental aspect of Linux system administration. Although Linux is designed with strong security features, improper configuration, outdated software, weak passwords, or unnecessary services can introduce vulnerabilities.

Following security best practices helps protect systems from unauthorized access, malware, data breaches, and other cyber threats.

---

# Why Follow Security Best Practices?

Good security practices help you:

- Protect sensitive data
- Prevent unauthorized access
- Reduce attack surfaces
- Maintain system integrity
- Ensure compliance with security policies
- Improve system reliability

---

# 1. Keep Your System Updated

Regular updates include:

- Security patches
- Bug fixes
- Performance improvements
- Kernel updates

Example:

```bash
sudo apt update
sudo apt upgrade
```

Always apply security updates promptly.

---

# 2. Use Strong Passwords

A strong password should:

- Be at least 12–16 characters long
- Include uppercase and lowercase letters
- Include numbers
- Include special characters
- Avoid dictionary words and personal information

Whenever possible, use a password manager to generate and store strong passwords.

---

# 3. Follow the Principle of Least Privilege

Grant users only the permissions they require.

Avoid giving administrative privileges unless necessary.

Example:

```bash
sudo
```

should be used only for tasks requiring elevated permissions.

---

# 4. Disable Root Login

Direct root login increases security risks.

Instead:

- Use a regular user account.
- Perform administrative tasks with `sudo`.

For SSH servers, disable root login in:

```text
/etc/ssh/sshd_config
```

Example:

```text
PermitRootLogin no
```

Restart the SSH service after making changes.

---

# 5. Secure SSH Access

Recommended practices:

- Disable password authentication when using SSH keys.
- Use SSH key authentication.
- Change the default SSH port if appropriate.
- Disable root login.
- Limit access to authorized users.

Example:

```bash
ssh-keygen
```

---

# 6. Enable a Firewall

A firewall restricts unwanted network traffic.

Common Linux firewall tools:

- UFW
- firewalld
- iptables
- nftables

Example (UFW):

```bash
sudo ufw enable
```

Check status:

```bash
sudo ufw status
```

---

# 7. Remove Unnecessary Software

Unused applications:

- Increase the attack surface
- Consume resources
- Introduce unnecessary vulnerabilities

Remove packages that are no longer needed.

---

# 8. Disable Unused Services

View active services:

```bash
systemctl list-units --type=service
```

Disable unnecessary services:

```bash
sudo systemctl disable service-name
```

Fewer running services mean fewer potential entry points.

---

# 9. Secure File Permissions

Protect sensitive files using appropriate permissions.

Examples:

Private files:

```bash
chmod 600 file
```

Executable scripts:

```bash
chmod 755 script.sh
```

Never use:

```bash
chmod 777
```

unless absolutely necessary.

---

# 10. Monitor Log Files

Review logs regularly for suspicious activity.

Useful locations:

```text
/var/log/
```

Useful commands:

```bash
journalctl
```

```bash
tail -f /var/log/auth.log
```

Logs help detect unauthorized access attempts.

---

# 11. Back Up Important Data

Regular backups protect against:

- Hardware failures
- Accidental deletion
- Malware
- Ransomware
- System corruption

Use automated backup schedules whenever possible.

---

# 12. Encrypt Sensitive Data

Encryption protects data even if storage devices are compromised.

Examples:

- LUKS for disk encryption
- GPG for file encryption
- OpenSSL for certificates and encryption tasks

Encrypt both data at rest and data in transit whenever appropriate.

---

# 13. Use Multi-Factor Authentication (MFA)

Whenever supported:

- Enable MFA for remote access.
- Enable MFA for administrative accounts.
- Protect critical services with additional authentication factors.

MFA significantly reduces the risk of account compromise.

---

# 14. Scan for Vulnerabilities

Use security tools such as:

- Lynis
- OpenSCAP
- ClamAV
- rkhunter
- chkrootkit

Regular security assessments help identify weaknesses before attackers do.

---

# 15. Audit User Accounts

Review users periodically.

Useful commands:

```bash
cat /etc/passwd
```

```bash
last
```

Remove unused accounts and disable inactive users.

---

# 16. Monitor Running Processes

Unexpected processes may indicate malware or unauthorized activity.

Useful commands:

```bash
ps aux
```

```bash
top
```

```bash
htop
```

Investigate unfamiliar or resource-intensive processes.

---

# 17. Secure Scheduled Tasks

Review cron jobs and scheduled tasks regularly.

Example:

```bash
crontab -l
```

Ensure scheduled scripts are trusted and have appropriate permissions.

---

# 18. Verify Software Sources

Install software only from:

- Official repositories
- Trusted vendors
- Verified package maintainers

Avoid downloading random scripts or binaries from unknown websites.

---

# 19. Practice Defense in Depth

Security should use multiple layers, including:

- Firewalls
- Strong authentication
- Access control
- Encryption
- Regular updates
- Monitoring
- Backups

No single security measure is sufficient on its own.

---

# Useful Security Commands

Update packages:

```bash
sudo apt update
```

Check firewall status:

```bash
sudo ufw status
```

View logged-in users:

```bash
who
```

List active services:

```bash
systemctl list-units --type=service
```

View authentication logs:

```bash
journalctl -u ssh
```

Monitor running processes:

```bash
ps aux
```

Find open network ports:

```bash
ss -tuln
```

---

# Common Mistakes

| Mistake | Better Practice |
|----------|-----------------|
| Using weak passwords | Use strong, unique passwords |
| Logging in as root | Use a regular account with `sudo` |
| Ignoring updates | Install security updates regularly |
| Leaving unused services enabled | Disable unnecessary services |
| Using `chmod 777` | Apply the minimum required permissions |
| Ignoring logs | Monitor logs for suspicious activity |
| Downloading software from unknown sources | Use trusted repositories |

---

# Security Checklist

- Keep the system updated.
- Use strong passwords.
- Enable multi-factor authentication where possible.
- Disable direct root login.
- Secure SSH access.
- Enable and configure a firewall.
- Remove unnecessary software and services.
- Apply proper file permissions.
- Monitor logs regularly.
- Perform regular backups.
- Encrypt sensitive data.
- Audit user accounts.
- Scan for vulnerabilities.
- Verify software sources.

---

# Key Takeaways

- Linux provides strong built-in security features, but secure configuration and maintenance are essential.
- Regular updates, strong authentication, proper permissions, and continuous monitoring significantly reduce security risks.
- Security is an ongoing process that requires multiple layers of protection rather than relying on a single solution.
- Following these best practices helps create secure, stable, and resilient Linux systems.

---

## Related Topics

- Permissions
- Users and Groups
- SSH
- Package Management
- Logging
- Networking
- System Maintenance
- Troubleshooting