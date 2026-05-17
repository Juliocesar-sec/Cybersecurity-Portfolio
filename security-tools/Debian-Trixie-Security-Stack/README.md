# 🛡 Debian Trixie Security Stack

![Debian](https://img.shields.io/badge/Debian-Trixie-red)
![Security](https://img.shields.io/badge/Security-Hardening-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-success)

A **security stack for Debian servers** using open-source security tools.

This project demonstrates how to build a **basic secure server environment** using:

* 🔥 UFW (Firewall)
* 🕵️ Suricata (IDS/IPS)
* 🦠 ClamAV (Antivirus)
* 🚫 Fail2Ban (Intrusion prevention)

---

# 📦 Features

* Firewall protection
* Intrusion detection
* Malware scanning
* Brute-force protection
* Logging and monitoring

---

# 🧱 Security Architecture

```
              Internet
                  │
            ┌───────────┐
            │   UFW     │
            │ Firewall  │
            └─────┬─────┘
                  │
            ┌───────────┐
            │ Suricata  │
            │ IDS / IPS │
            └─────┬─────┘
                  │
            ┌───────────┐
            │  ClamAV   │
            │ Antivirus │
            └─────┬─────┘
                  │
            Internal Services
```

---

# ⚙️ Installation

Update system first.

```bash
sudo apt update
sudo apt upgrade
```

---

# 🔥 Firewall (UFW)

Install UFW:

```bash
sudo apt install ufw
```

Set default policies:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

Allow essential services:

```bash
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
```

Enable firewall:

```bash
sudo ufw enable
```

Check status:

```bash
sudo ufw status verbose
```

---

# 🕵️ Suricata IDS

Install Suricata:

```bash
sudo apt install suricata
```

Download IDS rules:

```bash
sudo suricata-update
```

Test configuration:

```bash
sudo suricata -T -c /etc/suricata/suricata.yaml
```

Start service:

```bash
sudo systemctl restart suricata
```

Monitor alerts:

```bash
sudo tail -f /var/log/suricata/fast.log
```

---

# 🦠 ClamAV Antivirus

Install ClamAV:

```bash
sudo apt install clamav clamav-daemon
```

Update virus database:

```bash
sudo freshclam
```

Enable automatic updates:

```bash
sudo systemctl enable --now clamav-freshclam
```

Scan directory:

```bash
clamscan -r /home
```

Daemon scan:

```bash
sudo clamdscan --fdpass /home
```

---

# 🚫 Fail2Ban Protection

Install Fail2Ban:

```bash
sudo apt install fail2ban
```

Enable service:

```bash
sudo systemctl enable --now fail2ban
```

Check status:

```bash
sudo systemctl status fail2ban
```

Fail2Ban automatically blocks brute-force attacks on services such as SSH.

---

# 📊 Logs

Important log locations:

```
/var/log/ufw.log
/var/log/suricata/
/var/log/clamav/
```

Monitor logs:

```bash
sudo tail -f /var/log/ufw.log
sudo tail -f /var/log/suricata/fast.log
sudo tail -f /var/log/clamav/clamav.log
```

---

# 🚀 Optional Improvements

Recommended additions:

* Elastic Stack (ELK)
* CrowdSec
* Wazuh
* Netdata monitoring
* Automatic security updates

---

# 📁 Project Structure

```
debian-security-stack
│
├── README.md
├── install.sh
├── configs
│   ├── suricata.yaml
│   └── ufw-rules.txt
│
└── docs
    └── architecture.md
```


# 🤝 Contributing

Pull requests are welcome.

---

# ⭐ Star the Project

If you find this useful, consider starring the repository.
