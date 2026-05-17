# Network Security Hardening

This project details the hardening and security optimization process performed on a SFT1200 router running OpenWrt. The primary objective was to mitigate vulnerabilities associated with exposed services and implement robust authentication through a public key infrastructure.

- SSH Key Authentication (RSA): Migration from password-based authentication to 2048-bit RSA cryptographic keys with legacy compatibility parameters.
- Automated Maintenance: Implementation of scheduled reboots for RAM log cleanup and system stability.
- Backup Security: Storage of secrets and private keys inside VeraCrypt-encrypted volumes.

![router-hardening](https://github.com/Juliocesar-sec/Cybersecurity-Portfolio/blob/128dd67bba0b24280c5711dedf972741abb3d86d/labs/ssh-lab/prints/Screenshot_2026-05-12_09-11-33.png)

## Technical Details**

### **1. Package Management and Repositories**

To resolve the wget returned 5 error (common on legacy systems where SSL certificates expire or the system clock becomes unsynchronized), a manual clock correction and package feed update were performed:


### Manual date adjustment for SSL/TLS certificate validation
date 051209302026

# Update package repository indexes
opkg update
```

### **2. Firewall and Perimeter Defense**

Implementation of DROP firewall rules to mitigate port scanning attempts and external exploitation against the WAN interface.

**Blocked Ports**

Transfer/Access Services:
20, 21 (FTP), 22 (SSH), 69 (TFTP), 80 (HTTP)

Database Services:
3306 (MySQL), 5432 (PostgreSQL), 6379 (Redis), 27017 (MongoDB)

Network Services:
25 (SMTP), 53 (DNS), 111 (RPC), 445 (SMB), 5900 (VNC)

```
# OpenWrt CLI (UCI) implementation
uci add firewall rule
uci set firewall.@rule[-1].name='Block-High-Risk-WAN'
uci set firewall.@rule[-1].src='wan'
uci set firewall.@rule[-1].dest_port='20 21 22 25 53 80 111 445 69 3306 2049 5900 5432 6379 27017 1900 5353'
uci set firewall.@rule[-1].proto='tcp udp'
uci set firewall.@rule[-1].target='DROP'
uci commit firewall
/etc/init.d/firewall restart
```

### **3. SSH Hardening (Dropbear)**

Replacement of password-based authentication with RSA public key authentication (2048-bit). Due to the legacy nature of the firmware, compatibility parameters for SHA-1-based algorithms were required.

**Host Login Configuration (Debian)**

A shortcut entry was created inside ~/.ssh/config to automate the required compatibility parameters:

```
Host sft1200
    HostName 192.168.8.1
    User root
    IdentityFile ~/.ssh/id_rsa_sft
    HostKeyAlgorithms +ssh-rsa
    PubkeyAcceptedKeyTypes +ssh-rsa
```
![Host Login Configuration1](https://github.com/Juliocesar-sec/Cybersecurity-Portfolio/blob/b6f706006b321e7d69945eaaf0d163ccc848323d/labs/ssh-lab/prints/Screenshot_2026-05-12_09-17-24.png)

Complete Password Authentication Disablement (SSH Key Only)

```
uci set dropbear.@dropbear.RootPasswordAuth='off'
uci set dropbear.@dropbear.PasswordAuth='off'
uci commit dropbear
/etc/init.d/dropbear restart
```

![Host Login Configuration2](https://github.com/Juliocesar-sec/Cybersecurity-Portfolio/blob/a4c0503a167f5e6a8fb32e9016641f1853d4f932/labs/ssh-lab/prints/Screenshot_2026-05-12_09-22-34.png)

### **4. Maintenance Automation**

To prevent RAM log overflow and ensure periodic connection renewal, a scheduled Cron task was configured:


```
# Daily reboot at 04:00 AM for system and log cleanup
00 04 * * * /sbin/reboot
```

### **🔐 Backup and Encryption**

To ensure Digital Sovereignty and prevent accidental lockout scenarios, RSA private keys were stored on an external physical device protected by a VeraCrypt-encrypted volume mounted through the FUSE interface on Linux.
