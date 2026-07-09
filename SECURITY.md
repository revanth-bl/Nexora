# 🔒 Security Policy

Thank you for helping keep **Nexora** secure.

Although Nexora is primarily an open-source documentation platform, we take the security of our repository, website, automation, and contributors seriously.

---

# 🛡 Supported Versions

The latest version of the repository is actively maintained and receives security updates.

| Version | Supported |
|----------|-----------|
| Latest (main) | ✅ |
| Older versions | ❌ |

---

# 🚨 Reporting a Security Vulnerability

If you discover a security vulnerability, **please do not open a public GitHub issue.**

Instead, report it privately by contacting the project maintainers.

Please include:

- A clear description of the issue
- Steps to reproduce
- Potential impact
- Screenshots or logs (if applicable)
- Suggested mitigation (optional)

We will acknowledge your report as soon as possible and investigate it responsibly.

---

# 📋 Scope

Security reports may include issues related to:

- GitHub Actions workflows
- Automation scripts
- Website vulnerabilities
- Third-party dependencies
- Repository permissions
- Documentation infrastructure
- CI/CD pipelines

General documentation mistakes or broken links should be reported as normal GitHub Issues.

---

# 🔐 Responsible Disclosure

Please allow the maintainers reasonable time to investigate and resolve security issues before publicly disclosing them.

Responsible disclosure helps protect contributors and users.

---

# 🧰 Security Best Practices

When contributing to Nexora:

- Never commit passwords or API keys.
- Never commit cloud credentials.
- Never commit SSH private keys.
- Never upload sensitive configuration files.
- Never include personal information in examples.
- Use placeholder values in documentation.

Example:

```env
API_KEY=your_api_key_here
PASSWORD=your_password_here
```

Instead of:

```env
API_KEY=abcd123456789
PASSWORD=mySecretPassword
```

---

# 📦 Dependencies

When adding tools, libraries, or packages:

- Prefer official sources.
- Keep dependencies updated.
- Remove unused dependencies.
- Verify package authenticity before use.

---

# 🤖 GitHub Actions

All workflows should:

- Follow GitHub security best practices.
- Use least-privilege permissions.
- Pin action versions where practical.
- Avoid exposing secrets in logs.

---

# 🌍 Third-Party Resources

Only reference trusted and reputable sources whenever possible.

Examples include:

- Official documentation
- RFCs
- Standards organizations
- Vendor documentation
- Well-maintained open-source projects

---

# ❤️ Thank You

Security is a shared responsibility.

Thank you for helping keep Nexora safe, reliable, and trustworthy for everyone.