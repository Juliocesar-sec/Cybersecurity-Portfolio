# Networking Basics

A beginner-friendly guide to core networking concepts commonly used in cybersecurity, IT, and certification studies such as Security+ and PenTest+.

---

# Table of Contents

- [Introduction](#introduction)
- [TCP/IP Fundamentals](#tcpip-fundamentals)
- [IP Addressing](#ip-addressing)
- [Common Network Protocols](#common-network-protocols)
- [Network Devices](#network-devices)
- [Important Notes](#important-notes)
- [Recommended Topics to Learn Next](#recommended-topics-to-learn-next)

---

# Introduction

Networking is the foundation of modern communication between computers, servers, and devices.

Understanding networking concepts helps with:

- Troubleshooting systems
- Securing networks
- Ethical hacking
- System administration
- Cybersecurity analysis

---

# TCP/IP Fundamentals

## What is TCP/IP?

TCP/IP (Transmission Control Protocol / Internet Protocol) is the core communication model used on the internet and modern networks.

It defines:
- How data is sent
- How devices communicate
- How packets are routed

---

## TCP (Transmission Control Protocol)

TCP is a **connection-oriented** protocol that ensures reliable communication between devices.

### Key Features

- Reliable delivery
- Error checking
- Ordered data transmission
- Connection establishment before communication

### TCP Process

1. Connection established
2. Data transmitted
3. Delivery confirmed
4. Connection closed

### Common TCP Uses

- Web browsing (HTTP/HTTPS)
- Email
- File transfers
- SSH

### Advantages

- Reliable
- Accurate
- Handles lost packets

### Disadvantages

- Slower than UDP
- More overhead

---

## UDP (User Datagram Protocol)

UDP is a **connectionless** protocol designed for speed and low latency.

### Key Features

- No connection setup
- Faster transmission
- No delivery guarantee
- No packet ordering

### Common UDP Uses

- Video streaming
- Online gaming
- VoIP
- DNS queries

### Advantages

- Fast
- Lightweight
- Low latency

### Disadvantages

- Packets may be lost
- No reliability checks

---

# IP Addressing

IP addresses identify devices on a network.

---

## IPv4

IPv4 uses a **32-bit** address format.

### Example

```text
192.168.1.1
```

### Characteristics

- Most commonly used today
- Supports about 4.3 billion addresses
- Written in dotted decimal notation

### Private IPv4 Ranges

| Range | Purpose |
|---|---|
| 10.0.0.0/8 | Private networks |
| 172.16.0.0 – 172.31.255.255 | Private networks |
| 192.168.0.0/16 | Home/business networks |

---

## IPv6

IPv6 uses a **128-bit** address format.

### Example

```text
2001:0db8::1
```

### Characteristics

- Much larger address space
- Designed to replace IPv4
- Improved efficiency and routing

### Benefits

- More available addresses
- Better scalability
- Built-in security improvements

---

# Common Network Protocols

## HTTP / HTTPS

Used for web communication between browsers and web servers.

### HTTP
- Unencrypted web traffic
- Uses port 80

### HTTPS
- Encrypted using SSL/TLS
- Uses port 443

---

## DNS (Domain Name System)

Translates domain names into IP addresses.

### Example

```text
google.com → 142.250.x.x
```

### Uses Port

- UDP 53
- TCP 53 (sometimes)

---

## SSH (Secure Shell)

Provides secure remote login and command-line access.

### Uses

- Remote administration
- Secure terminal access
- Secure file transfers

### Default Port

```text
22
```

---

## FTP (File Transfer Protocol)

Used to transfer files between systems.

### Characteristics

- Older protocol
- Not encrypted by default

### Default Ports

| Port | Purpose |
|---|---|
| 20 | Data transfer |
| 21 | Control connection |

### Secure Alternatives

- SFTP
- FTPS

---

## Email Protocols

### SMTP (Simple Mail Transfer Protocol)

Used for sending email.

### IMAP (Internet Message Access Protocol)

Allows emails to remain stored on the server.

### POP3 (Post Office Protocol v3)

Downloads emails locally, often removing them from the server.

### Common Ports

| Protocol | Port |
|---|---|
| SMTP | 25 / 587 |
| IMAP | 143 / 993 |
| POP3 | 110 / 995 |

---

# Network Devices

## Router

Routers forward traffic between different networks.

### Functions

- Route packets
- Connect local networks to the internet
- Perform NAT (Network Address Translation)

---

## Switch

Switches connect devices within the same network.

### Functions

- Forward frames using MAC addresses
- Improve network efficiency
- Reduce collisions

---

## Firewall

Firewalls control incoming and outgoing network traffic using security rules.

### Types

- Hardware firewall
- Software firewall
- Next-generation firewall (NGFW)

### Functions

- Block malicious traffic
- Filter connections
- Enforce security policies

---

# Important Notes

- Networking fundamentals are critical for cybersecurity.
- Understanding protocols helps identify attacks and vulnerabilities.
- TCP and UDP behave differently and are important during penetration testing.
- Firewalls, routers, and switches are foundational network infrastructure components.

---

# Recommended Topics to Learn Next

- OSI Model
- Ports and Services
- Subnetting
- NAT and PAT
- VLANs
- ARP
- DHCP
- VPN Technologies
- Packet Analysis with Wireshark
- Network Scanning with Nmap

---

# License

This document is provided for educational purposes.
