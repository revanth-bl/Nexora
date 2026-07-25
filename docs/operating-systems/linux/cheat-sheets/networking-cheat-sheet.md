# Networking Cheat Sheet

## Overview

Linux provides powerful networking tools for configuring interfaces, testing connectivity, troubleshooting network issues, transferring files, and monitoring network activity. This cheat sheet summarizes the most commonly used networking commands and concepts.

---

# View Network Information

| Command | Description |
|----------|-------------|
| `ip addr` | Show IP addresses |
| `ip link` | Show network interfaces |
| `ip route` | Display routing table |
| `hostname` | Show system hostname |
| `hostname -I` | Show local IP addresses |
| `ifconfig` | Display interface information (legacy) |

---

# Connectivity Testing

| Command | Description |
|----------|-------------|
| `ping host` | Test network connectivity |
| `ping -c 4 google.com` | Send 4 ICMP packets |
| `traceroute host` | Show packet path |
| `tracepath host` | Trace network path |
| `mtr host` | Continuous traceroute |

Example:

```bash
ping google.com
```

---

# DNS

View DNS configuration:

```bash
cat /etc/resolv.conf
```

DNS lookup:

```bash
nslookup google.com
```

Query DNS records:

```bash
dig google.com
```

Reverse lookup:

```bash
dig -x 8.8.8.8
```

---

# Network Interfaces

Enable interface:

```bash
sudo ip link set eth0 up
```

Disable interface:

```bash
sudo ip link set eth0 down
```

Assign IP address:

```bash
sudo ip addr add 192.168.1.100/24 dev eth0
```

---

# Routing

Display routes:

```bash
ip route
```

Add route:

```bash
sudo ip route add 192.168.2.0/24 via 192.168.1.1
```

Delete route:

```bash
sudo ip route del 192.168.2.0/24
```

---

# Port Monitoring

Show listening ports:

```bash
ss -tuln
```

Display processes using ports:

```bash
ss -tulpn
```

Legacy command:

```bash
netstat -tulnp
```

---

# Download Files

Download using wget:

```bash
wget https://example.com/file.zip
```

Download using curl:

```bash
curl -O https://example.com/file.zip
```

View webpage:

```bash
curl https://example.com
```

---

# SSH

Connect to remote machine:

```bash
ssh user@server
```

Use custom port:

```bash
ssh -p 2222 user@server
```

Generate SSH key:

```bash
ssh-keygen
```

Copy public key:

```bash
ssh-copy-id user@server
```

---

# Secure Copy (SCP)

Copy file to remote system:

```bash
scp file.txt user@server:/home/user/
```

Copy file from remote system:

```bash
scp user@server:file.txt .
```

Copy directory:

```bash
scp -r folder user@server:/home/user/
```

---

# Rsync

Copy files:

```bash
rsync file.txt backup/
```

Synchronize directories:

```bash
rsync -av source/ destination/
```

Remote synchronization:

```bash
rsync -av folder user@server:/backup/
```

---

# Firewall

Ubuntu (UFW):

```bash
sudo ufw status
sudo ufw enable
sudo ufw allow 22
sudo ufw deny 80
```

Firewalld:

```bash
firewall-cmd --list-all
```

---

# Network Statistics

Interface statistics:

```bash
ip -s link
```

Network connections:

```bash
ss
```

Bandwidth monitoring:

```bash
iftop
```

Real-time traffic:

```bash
nload
```

---

# Packet Capture

Capture packets:

```bash
sudo tcpdump
```

Capture on interface:

```bash
sudo tcpdump -i eth0
```

Capture specific port:

```bash
sudo tcpdump port 80
```

---

# Common Ports

| Port | Service |
|------|---------|
| 20/21 | FTP |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 67/68 | DHCP |
| 80 | HTTP |
| 110 | POP3 |
| 143 | IMAP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |

---

# IP Commands

```bash
ip addr
ip route
ip link
ip neigh
ip monitor
```

---

# Network Troubleshooting

Check connectivity:

```bash
ping google.com
```

Verify DNS:

```bash
dig google.com
```

Display routing table:

```bash
ip route
```

View listening ports:

```bash
ss -tuln
```

Trace network path:

```bash
traceroute google.com
```

---

# Useful Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + C` | Stop running command |
| `Ctrl + R` | Search command history |
| `Tab` | Auto-complete |
| `Ctrl + L` | Clear terminal |

---

# Common Networking Commands

```bash
ping
ip
hostname
curl
wget
ssh
scp
rsync
ss
netstat
traceroute
tracepath
dig
nslookup
tcpdump
```

---

# Best Practices

- Use SSH instead of Telnet for remote access.
- Keep firewalls enabled.
- Regularly update network packages.
- Use strong SSH authentication keys.
- Monitor open ports periodically.
- Verify DNS before troubleshooting connectivity.
- Use `rsync` for efficient file synchronization.

---

# Related Topics

- Networking
- SSH
- TCP/IP
- DNS
- Firewalls
- Linux Commands
- Network Security
- System Administration