# macOS Security Architecture

## Overview

macOS security is built as a layered system that protects the operating system, applications, user data, and hardware.

Security controls exist at multiple levels:

```text
Applications
      │
      ▼
Application Security
      │
      ▼
User / System Services
      │
      ▼
Kernel Security
      │
      ▼
Hardware Security
```

The major security technologies include:

- Secure Boot
- System Integrity Protection (SIP)
- Gatekeeper
- Code Signing
- Notarization
- App Sandbox
- Entitlements
- Privacy permissions
- FileVault
- Keychain
- Address Space Layout Randomization (ASLR)
- Data Execution Prevention / execute protections
- Hardware-backed security

---

# Security Architecture at a Glance

A simplified macOS security architecture looks like:

```text
┌─────────────────────────────────────┐
│            Applications             │
├─────────────────────────────────────┤
│ Sandbox • TCC • Entitlements        │
├─────────────────────────────────────┤
│ Code Signing • Gatekeeper           │
├─────────────────────────────────────┤
│ System Services / Security APIs     │
├─────────────────────────────────────┤
│             XNU Kernel              │
├─────────────────────────────────────┤
│ Secure Boot / Hardware Security     │
├─────────────────────────────────────┤
│              Hardware               │
└─────────────────────────────────────┘
```

Each layer provides different protections.

---

# Security Principles

macOS security is based on several fundamental principles:

- Least privilege
- Process isolation
- Memory protection
- Code integrity
- Secure boot
- User authorization
- Data encryption
- Hardware-backed security
- Application isolation

The goal is not to rely on a single security mechanism.

Instead:

```text
Multiple Security Layers
          │
          ▼
     Defense in Depth
```

If one layer is bypassed, additional layers can still limit the damage.

---

# Secure Boot

Modern Macs use a secure boot architecture that helps ensure trusted software is used during system startup.

A simplified chain is:

```text
Hardware Root of Trust
        │
        ▼
Firmware / Boot ROM
        │
        ▼
Boot Components
        │
        ▼
macOS
        │
        ▼
System Software
```

Each stage helps establish trust in the next stage.

The exact implementation differs between Intel Macs with the T2 Security Chip and Apple silicon Macs.

---

# Apple Silicon Security

Apple silicon Macs integrate significant security functionality into the platform.

Important components include:

- Secure Boot
- Secure Enclave
- Hardware-backed key protection
- Memory protection
- Hardware-assisted cryptography
- Boot security policies

A simplified architecture is:

```text
Apple Silicon
│
├── CPU
├── GPU
├── Secure Enclave
├── Memory Protection
└── Hardware Security Features
```

---

# Secure Enclave

The **Secure Enclave** is a security subsystem designed to protect sensitive cryptographic operations and secrets.

It can help protect:

- Cryptographic keys
- Biometric authentication data
- Keychain-related secrets
- Device security information

Simplified:

```text
Application
     │
     ▼
Security Framework
     │
     ▼
Secure Enclave Services
     │
     ▼
Protected Hardware
```

Applications do not directly control the Secure Enclave.

---

# Code Signing

macOS uses **code signing** to establish the identity and integrity of executable code.

A signed application contains cryptographic information that can be used to verify its publisher and whether protected parts of the application have been modified.

Conceptually:

```text
Application
     │
     ▼
Code Signature
     │
     ▼
Verification
     │
     ├── Valid
     │
     └── Invalid / Modified
```

Code signing is an important part of macOS application security.

---

# Gatekeeper

**Gatekeeper** helps protect users from running untrusted applications downloaded from outside the trusted software distribution channels.

When an application is launched, macOS can evaluate factors such as:

- Developer identity
- Code signature
- Notarization
- Source of the application
- User security settings

Simplified:

```text
Downloaded Application
        │
        ▼
    Gatekeeper
        │
   ┌────┴────┐
   ▼         ▼
 Trusted   Warning / Block
```

Gatekeeper is one component of the broader macOS security architecture.

---

# Notarization

Apple provides a **notarization** process for software distributed outside the Mac App Store.

Developers submit software to Apple for automated security checks.

A simplified workflow is:

```text
Developer
    │
    ▼
Build Application
    │
    ▼
Code Sign
    │
    ▼
Submit for Notarization
    │
    ▼
Apple Checks
    │
    ▼
Notarized Application
```

Notarization does not replace code signing; it complements it.

---

# App Sandbox

The **App Sandbox** restricts what an application can access.

A sandboxed application may have limited access to:

- Files
- Network resources
- Hardware
- Other applications
- User data

Simplified:

```text
Application
    │
    ▼
Sandbox
    │
    ├── Allowed Resources
    │
    └── Restricted Resources
```

Sandboxing reduces the impact of a compromised or malicious application.

---

# Entitlements

**Entitlements** define special capabilities granted to applications.

Examples can include permissions related to:

- App Sandbox
- Keychain access
- Network capabilities
- Hardware features
- System services

Conceptually:

```text
Application
    │
    ▼
Code Signature
    │
    ▼
Entitlements
    │
    ▼
Allowed Capabilities
```

An entitlement does not automatically mean unrestricted access. Additional system security controls may still apply.

---

# Transparency, Consent, and Control

macOS uses **Transparency, Consent, and Control (TCC)** to manage access to sensitive user data and system resources.

Examples include:

- Contacts
- Calendar
- Photos
- Microphone
- Camera
- Location
- Desktop
- Documents
- Accessibility features

Simplified:

```text
Application
      │
      ▼
Request Protected Resource
      │
      ▼
       TCC
      │
   ┌──┴──┐
   ▼     ▼
Allow   Deny
```

Users can review many of these permissions through System Settings.

---

# Privacy Permissions

Privacy permissions provide a security boundary between applications and sensitive resources.

For example:

```text
Application
     │
     ▼
Request Microphone
     │
     ▼
Privacy Permission
     │
     ├── Allowed
     └── Denied
```

This prevents applications from automatically accessing certain sensitive resources without authorization.

---

# System Integrity Protection

**System Integrity Protection (SIP)** protects critical system files, directories, and system-level operations from unauthorized modification.

SIP is enforced even against processes with elevated privileges in many situations.

Conceptually:

```text
Root Process
     │
     ▼
Attempts Protected Operation
     │
     ▼
System Integrity Protection
     │
     └── Operation Restricted
```

This reduces the ability of malware or accidental administrative actions to modify critical parts of macOS.

---

# Root Is Not Absolute Power

Traditional Unix systems often treat the `root` user as having extremely broad privileges.

macOS adds additional security mechanisms that can restrict even privileged operations.

```text
root
 │
 ▼
Kernel Security Policies
 │
 ├── Allowed
 └── Restricted
```

SIP and other security controls are important examples of this principle.

---

# FileVault

**FileVault** provides full-volume encryption for Mac storage.

Modern macOS uses encryption technologies integrated with the hardware and operating system.

Simplified:

```text
User Data
    │
    ▼
Encryption
    │
    ▼
Encrypted Storage
```

If the storage device is removed from the Mac, encryption helps prevent unauthorized access to the stored data.

---

# Data Protection

Encryption protects stored information, but macOS security also depends on:

- Authentication
- Key management
- Access controls
- File permissions
- Application sandboxing
- Privacy controls

A simplified model is:

```text
Data
 │
 ├── Encryption
 ├── Permissions
 ├── Authentication
 └── Application Controls
```

---

# Keychain

The **Keychain** securely stores credentials and cryptographic secrets.

Examples include:

- Passwords
- Wi-Fi credentials
- Certificates
- Private keys
- Authentication secrets

Applications access Keychain data through security APIs rather than directly reading a raw password database.

---

# Keychain Access

The command-line utility:

```bash
security
```

provides access to various macOS security functions.

For example:

```bash
security find-generic-password
```

can query a generic password item when the appropriate permissions and arguments are supplied.

Be careful when querying credentials, especially on shared systems.

---

# File Permissions

macOS inherits Unix-style permission concepts.

Files have permissions for:

```text
Owner
Group
Others
```

For example:

```text
-rwxr-xr--
```

represents:

```text
Owner  → rwx
Group  → r-x
Others → r--
```

Inspect permissions with:

```bash
ls -l
```

---

# Access Control Lists

macOS also supports **Access Control Lists (ACLs)** for more detailed permissions.

View ACL information with:

```bash
ls -le
```

ACLs can provide permissions beyond the basic owner/group/other model.

---

# User and Group Security

macOS uses users and groups to control access to resources.

Conceptually:

```text
User
 │
 ▼
Groups
 │
 ▼
Permissions
 │
 ▼
Resources
```

Useful commands include:

```bash
whoami
```

```bash
id
```

```bash
groups
```

---

# Process Isolation

Each process normally operates within its own virtual address space.

```text
Process A
┌──────────────┐
│ Address Space│
└──────────────┘

Process B
┌──────────────┐
│ Address Space│
└──────────────┘
```

One process cannot normally access another process's memory directly.

The kernel controls access to protected resources.

---

# Memory Protection

macOS uses hardware and kernel mechanisms to protect memory.

Important concepts include:

- Virtual memory
- Page permissions
- Non-executable memory
- Address Space Layout Randomization
- Process isolation

A simplified model:

```text
Process
   │
   ▼
Virtual Memory
   │
   ├── Read
   ├── Write
   └── Execute
```

Memory permissions help limit unauthorized code execution and memory modification.

---

# Address Space Layout Randomization

**ASLR** randomizes important memory locations.

Without ASLR:

```text
Known Memory Layout
        │
        ▼
More Predictable Exploitation
```

With ASLR:

```text
Randomized Memory Layout
        │
        ▼
Harder to Predict Addresses
```

ASLR is a defense-in-depth mechanism rather than a complete security solution.

---

# Execute Protections

Modern processors and operating systems can distinguish memory intended for data from memory intended for executable code.

Conceptually:

```text
Data Memory
   │
   └── Read / Write

Code Memory
   │
   └── Read / Execute
```

Restricting writable memory from also being executable can make certain exploitation techniques more difficult.

---

# Firewall

macOS includes firewall functionality that can control certain incoming network connections.

The firewall can be configured through:

```text
System Settings
    │
    ▼
Network
    │
    ▼
Firewall
```

Firewall behavior should be considered together with application-level networking and other security controls.

---

# Network Security

Network security includes several layers:

```text
Application
    │
    ▼
TLS / Encryption
    │
    ▼
Network Stack
    │
    ▼
Firewall / Network Controls
    │
    ▼
Network Interface
```

For example, HTTPS uses TLS to protect application data during network transmission.

---

# Authentication

macOS supports several authentication mechanisms.

Examples include:

- Password authentication
- Touch ID
- Secure Enclave-backed authentication
- Cryptographic credentials
- Smart cards and enterprise authentication mechanisms

Authentication establishes:

```text
Who are you?
     │
     ▼
Authentication
     │
     ▼
Access Decision
```

---

# Authorization

Authentication and authorization are different.

### Authentication

Determines:

```text
Who are you?
```

### Authorization

Determines:

```text
What are you allowed to do?
```

Simplified:

```text
User
 │
 ▼
Authentication
 │
 ▼
Identity
 │
 ▼
Authorization
 │
 ▼
Resource Access
```

---

# Privacy and Security Layers

A single application may be subject to multiple controls.

For example:

```text
Application
    │
    ├── Code Signing
    ├── Gatekeeper
    ├── Sandbox
    ├── TCC
    ├── File Permissions
    └── Network Controls
```

This is an example of **defense in depth**.

---

# Security Logging

Security-related events may be recorded in macOS logging systems.

The primary command-line interface is:

```bash
log
```

For example:

```bash
log show
```

Logs can be filtered to investigate particular processes or subsystems.

Use caution with large log queries because they can produce substantial output.

---

# Security Inspection Commands

Useful commands include:

```bash
csrutil status
```

to inspect System Integrity Protection status.

```bash
spctl --status
```

to inspect Gatekeeper assessment status.

```bash
codesign -dv <application>
```

to inspect code-signing information.

```bash
codesign --verify <application>
```

to verify a code signature.

```bash
security find-identity
```

to inspect available signing identities.

---

# Inspecting an Application

A basic security inspection can follow:

```text
Application
     │
     ▼
Check Signature
     │
     ▼
Check Gatekeeper Assessment
     │
     ▼
Inspect Entitlements
     │
     ▼
Inspect Permissions
```

Useful commands include:

```bash
codesign -dv --verbose=4 /path/to/Application.app
```

```bash
codesign -d --entitlements :- /path/to/Application.app
```

```bash
spctl -a -vv /path/to/Application.app
```

---

# Security Troubleshooting Workflow

When investigating a security-related issue:

```text
Identify Resource
       │
       ▼
Identify Process
       │
       ▼
Check User / Group
       │
       ▼
Check File Permissions
       │
       ▼
Check TCC Permissions
       │
       ▼
Check Sandbox / Entitlements
       │
       ▼
Check Code Signature
       │
       ▼
Check System Security Controls
       │
       ▼
Review Logs
```

The correct layer should be identified before changing security settings.

---

# Common Security Problems

Common macOS security-related problems include:

- Application blocked by Gatekeeper
- Invalid code signature
- Missing privacy permission
- Sandbox access failure
- Incorrect file permissions
- Keychain access denial
- SIP restrictions
- Firewall blocking connections
- Expired certificates
- Unauthorized application behavior
- Malware or suspicious processes

---

# Security vs Convenience

Security controls can sometimes prevent legitimate software from performing an operation.

For example:

```text
Security Control
       │
       ▼
Operation Blocked
       │
       ▼
Investigate Reason
       │
       ├── Legitimate Requirement
       │
       └── Potentially Unsafe Behavior
```

The correct response is to understand **why** the operation was blocked rather than immediately disabling security protections.

---

# Defense in Depth

macOS security is strongest when multiple independent controls work together.

```text
Secure Boot
     │
     ▼
Code Signing
     │
     ▼
Gatekeeper
     │
     ▼
Sandbox
     │
     ▼
TCC
     │
     ▼
File Permissions
     │
     ▼
Kernel Protections
     │
     ▼
Hardware Security
```

No individual mechanism is expected to provide complete protection.

---

# Key Concepts

| Concept | Description |
|---|---|
| Secure Boot | Establishes trust during system startup |
| Secure Enclave | Hardware security subsystem |
| Code Signing | Verifies software identity and integrity |
| Gatekeeper | Helps prevent execution of untrusted software |
| Notarization | Apple's automated software security checking process |
| App Sandbox | Restricts application access to resources |
| Entitlements | Define special application capabilities |
| TCC | Controls access to sensitive user data and resources |
| SIP | Protects critical system components |
| FileVault | Encrypts Mac storage |
| Keychain | Stores credentials and cryptographic secrets |
| ASLR | Randomizes memory layout |
| Firewall | Controls certain incoming network connections |
| ACL | Provides detailed filesystem access controls |

---

# Security Architecture Summary

The macOS security model can be summarized as:

```text
                    macOS Security
                          │
       ┌──────────────────┼──────────────────┐
       │                  │                  │
       ▼                  ▼                  ▼
   Hardware            Kernel           User Space
   Security           Security           Security
       │                  │                  │
       ├── Secure Boot    ├── SIP           ├── Sandbox
       ├── Secure Enclave ├── Memory        ├── TCC
       └── Crypto         │   Protection    ├── Gatekeeper
                          └── Process       ├── Code Signing
                              Isolation     └── Keychain
```

The central principle is **defense in depth**.

macOS does not rely on one security mechanism. Hardware security, the XNU kernel, code signing, application isolation, privacy controls, encryption, authentication, and filesystem permissions work together to protect the system and its data.