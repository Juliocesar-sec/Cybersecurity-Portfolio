# 🛡️ OWASP Mutillidae II Home Lab

A step-by-step guide to download and run OWASP Mutillidae II, a deliberately vulnerable web application for learning web security, using Docker on Kali Linux.

![Kali Linux](https://img.shields.io/badge/Kali%20Linux-Penetration%20Testing-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containerized%20Lab-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![OWASP](https://img.shields.io/badge/OWASP-Web%20Security-black?style=for-the-badge&logo=owasp&logoColor=white)
![Mutillidae II](https://img.shields.io/badge/Mutillidae%20II-Vulnerable%20Web%20App-darkred?style=for-the-badge)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Status](https://img.shields.io/badge/Status-Home%20Lab-success?style=for-the-badge)

---

# 📋 Prerequisites

Before starting, ensure the following are installed:

- Kali Linux (or any Linux distribution)
- Git
- Docker
- Docker Compose

> Note: If Git or Docker are not installed, follow the installation instructions below.

---

# ⚙️ Installing Git and Docker on Kali Linux

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git docker.io docker-compose -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

# 📥 Step 1: Clone the Mutillidae II Repository

Clone the official repository from GitHub:

```bash
git clone https://github.com/webpwnized/mutillidae.git
```

Move into the cloned directory:

```bash
cd mutillidae
```

---

# 🐳 Step 2: Create the Dockerfile

Create a file named `Dockerfile` with the following content:

```Dockerfile
FROM php:7.4-apache

RUN docker-php-ext-install mysqli pdo pdo_mysql && \
    a2enmod rewrite

EXPOSE 80
```

---

# 📦 Step 3: Create the docker-compose.yml File

Create a file named `docker-compose.yml`:

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8080:80"
    volumes:
      - ./mutillidae:/var/www/html
    depends_on:
      - db

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: mutillidae
      MYSQL_DATABASE: mutillidae
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

---

# 🚀 Step 4: Start the Environment

Build and start the Docker containers:

```bash
docker-compose up --build
```

After startup, open the application in your browser:

```text
http://localhost:8080
```

---

# 🔍 Step 5: Explore and Learn

Use the platform to practice and understand common web vulnerabilities, including:

- SQL Injection
- Cross-Site Scripting (XSS)
- Authentication Weaknesses
- Command Injection
- Session Security Issues
- Input Validation Problems

This lab environment is designed strictly for educational and authorized testing purposes.

---

# 🎯 Learning Objectives

Through this home lab, you can practice:

- Web application security testing
- Docker container deployment
- Local penetration testing environments
- Vulnerability identification
- Secure configuration awareness
- Basic offensive security concepts

---

# ⚠️ Disclaimer

OWASP Mutillidae II is intentionally vulnerable software designed for security education. Only run this environment locally or inside authorized lab environments. Never expose vulnerable applications to the public internet.

---
