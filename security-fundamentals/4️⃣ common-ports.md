# Common Network Ports

A beginner-friendly reference guide to commonly used network ports, protocols, and services in networking and cybersecurity.

---

# Table of Contents

- [Introduction](#introduction)
- [What Are Network Ports?](#what-are-network-ports)
- [Common Ports Reference Table](#common-ports-reference-table)
- [Port Categories](#port-categories)
- [Protocol Explanations](#protocol-explanations)
- [Security Considerations](#security-considerations)
- [Important Notes](#important-notes)
- [Recommended Topics to Learn Next](#recommended-topics-to-learn-next)

---

# Introduction

Network ports allow devices and applications to communicate over a network.

Each service or protocol typically uses a default port number so systems know where to send and receive traffic.

Understanding ports is essential for:

- Network troubleshooting
- Firewall configuration
- Penetration testing
- Vulnerability scanning
- Security monitoring

---

# What Are Network Ports?

A network port is a logical communication endpoint used by applications and services.

Ports work together with:
- IP addresses
- TCP
- UDP

### Example

```text
192.168.1.10:443
```

Where:
- `192.168.1.10` = IP address
- `443` = network port

---

# Common Ports Reference Table

| Port | Protocol | Transport | Purpose |
|---|---|---|---|
| 20/21 | FTP | TCP | File transfer |
| 22 | SSH | TCP | Secure remote login |
| 23 | Telnet | TCP | Remote terminal access |
| 25 | SMTP | TCP | Sending email |
| 53 | DNS | UDP/TCP | Domain name resolution |
| 67/68 | DHCP | UDP | Automatic IP assignment |
| 69 | TFTP | UDP | Simple file transfer |
| 80 | HTTP | TCP | Web traffic |
| 110 | POP3 | TCP | Email retrieval |
| 123 | NTP | UDP | Time synchronization |
| 143 | IMAP | TCP | Email retrieval |
| 161/162 | SNMP | UDP | Network management |
| 389 | LDAP | TCP/UDP | Directory services |
| 443 | HTTPS | TCP | Secure web traffic |
| 445 | SMB | TCP | Windows file sharing |
| 3389 | RDP | TCP | Remote Desktop Protocol |

---

# Port Categories

## Well-Known Ports

Range:

```text
0 - 1023
```

Reserved for common services and protocols.

Examples:
- HTTP
- HTTPS
- SSH
- DNS

---

## Registered Ports

Range:

```text
1024 - 49151
```

Used by applications and software vendors.

---

## Dynamic / Ephemeral Ports

Range:

```text
49152 - 65535
```

Temporary ports used for client-side communication.

---

# Protocol Explanations

## SSH (Port 22)

SSH (Secure Shell) provides encrypted remote access to systems.

### Common Uses

- Linux administration
- Secure command-line access
- Secure file transfers

### Security Benefit

Encrypts traffic to prevent credential theft.

---

## HTTP (Port 80)

HTTP is used for standard web communication.

### Characteristics

- Unencrypted
- Plaintext traffic
- Commonly redirected to HTTPS

---

## HTTPS (Port 443)

HTTPS secures web traffic using SSL/TLS encryption.

### Benefits

- Encrypts data
- Protects credentials
- Ensures secure browsing

---

## DNS (Port 53)

DNS translates domain names into IP addresses.

### Example

```text
example.com → 93.184.216.34
```

### Uses Both

- UDP for fast queries
- TCP for larger responses

---

## FTP (Ports 20/21)

FTP transfers files between systems.

### Characteristics

- Older protocol
- Not encrypted by default

### Secure Alternatives

- SFTP
- FTPS

---

## SMTP (Port 25)

SMTP is used to send email between servers and clients.

### Common Secure Ports

| Port | Purpose |
|---|---|
| 25 | Standard SMTP |
| 465 | SMTPS |
| 587 | Secure email submission |

---

## POP3 (Port 110)

POP3 downloads email from a mail server.

### Characteristics

- Stores emails locally
- May remove emails from server

---

## IMAP (Port 143)

IMAP synchronizes email with the mail server.

### Advantages

- Access mail from multiple devices
- Emails remain on server

---

## RDP (Port 3389)

Remote Desktop Protocol allows remote graphical access to Windows systems.

### Common Uses

- Remote administration
- IT support
- Virtual desktop access

### Security Warning

RDP is frequently targeted by attackers and should be protected with:
- MFA
- VPN access
- Strong passwords

---

# Security Considerations

## Why Attackers Scan Ports

Open ports can reveal:
- Running services
- Operating systems
- Potential vulnerabilities

Attackers use port scanning to identify targets.

---

## Common Security Risks

| Risk | Description |
|---|---|
| Open unnecessary ports | Increases attack surface |
| Weak services | Vulnerable software exposure |
| Default configurations | Easier exploitation |
| Unencrypted protocols | Data interception risk |

---

## Best Practices

- Close unused ports
- Use firewalls
- Enable encryption
- Keep services updated
- Monitor network activity
- Restrict remote access

---

# Important Notes

- Ports identify services on a system.
- TCP and UDP use ports differently.
- Recognizing common ports is essential for cybersecurity and penetration testing.
- Many attacks begin with network reconnaissance and port scanning.

---

# Recommended Topics to Learn Next

- TCP vs UDP
- Three-Way Handshake
- Port Scanning with Nmap
- Wireshark Packet Analysis
- Firewalls and ACLs
- Network Segmentation
- IDS/IPS Systems
- Service Enumeration

---

# License

This document is provided for educational purposes.
