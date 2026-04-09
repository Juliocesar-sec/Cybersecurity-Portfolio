### 🔐 Portfolio Report: Remote Access Setup via SSH

### 📁 Cybersecurity Portfolio
**Author:** [Jota Dev]  
**Date:** April 2026


Project: SSH Server Configuration on a Debian Virtual Machine
Environment: Oracle VirtualBox + Debian 12 (Trixie)
Date: April 2026

## 📌 Objective

Configure a Debian virtual machine to allow secure remote access via SSH from the host, using a Bridged network. The project demonstrates everything from network setup to executing administrative commands remotely.

## Step-by-Step

### Step 1 – Network Configuration (Bridged Adapter)

 ![Step 1 – Network Configuration](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/Passo.1.png)

In the Oracle VirtualBox Manager, I accessed the settings of the VM "DB".
Under Network → Adapter 1, I configured:

Attached to: Bridged Adapter
Name: enp0s31f6 (host network interface)
Adapter Type: Intel PRO/1000 MT Desktop
Promiscuous Mode: Deny
Cable Connected: Enabled

This setup allows the VM to obtain a real IP from the local network, enabling direct SSH access.

### Step 2 – Repository Update

![Step 2 – Repository Update](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/passo.2.png)

On the host terminal (purplghost@DEBIAN): sudo apt update
On the VM (vboxuser@vbox): sudo apt update

Result: Repositories successfully updated on the virtual machine (some warnings appeared on the host, but they did not affect the process).

### Step 3 – OpenSSH Server Installation

 ![Step 3 – OpenSSH Server Installation](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/passo.3.png)

On the VM, I ran:
```bash
sudo apt install openssh-server -y
```
### Step 4 – Enable and Start SSH Service

![Step 4 – Enable and Start SSH Service](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/passo.4.png)

Executed:
```bash
sudo systemctl enable --now ssh
```
### Step 5 – Verify SSH Service Status

![Step 5 – Verify SSH Status](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/main/labs/ssh-lab/prints/passo.4.png?raw=true)

Command:
```bash
sudo systemctl status ssh
```
Result:

Service active (running)
Listening on port 22
Main PID: 6927 (OpenBSD Secure Shell server)

### Step 6 – SSH Connection from the Host

![Step 6 – SSH Connection from Host](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/38e6851acaf3444fd7e36408ba5ddf0d9acb92c2/labs/ssh-lab/prints/passo.6.png)

On the host terminal, I connected:

ssh vboxuser@192.168.8.173

Entered the password for vboxuser, and the remote connection was successfully established.

### Step 7 – Successful SSH Session

![Step 7 – Successful SSH Session](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/38e6851acaf3444fd7e36408ba5ddf0d9acb92c2/labs/ssh-lab/prints/passo.7.png)

Debian GNU/Linux 12 banner appeared
Prompt changed to vboxuser@vbox:~$
Verified inside the VM using:

```bash
hostname -I
```

### Step 8 – Package Search via SSH

![Step 8 – Package Search via SSH](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/main/labs/ssh-lab/prints/passo.8.png?raw=true)

Within the SSH session, executed:
```bash
sudo apt search htop
dpkg -l | grep htop
```
Confirmed that the htop package was not installed on the VM yet.

### Step 9 – Install htop via SSH

![Step 9 – Install htop via SSH](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/main/labs/ssh-lab/prints/passo.9.png?raw=true)

Installed the package remotely:

```bash
sudo apt update && sudo apt install -y htop
```
htop was successfully downloaded and installed through the SSH connection.

### Step 10 – Disable SSH Service

![Step 10 – Disable SSH Service](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/38e6851acaf3444fd7e36408ba5ddf0d9acb92c2/labs/ssh-lab/prints/passo.10.png)

For remote control demonstration, executed:
```bash
sudo systemctl disable --now ssh
```
The SSH service was stopped and disabled successfully.

### Step 11 – Running htop and Checking Logs

![Step 11 – Running htop and Checking Logs](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/38e6851acaf3444fd7e36408ba5ddf0d9acb92c2/labs/ssh-lab/prints/passo.11.png)

Ran htop in the SSH session (interactive process viewer)
On the host, htop returned “command not found” (package not installed locally)
Checked SSH service logs using journalctl

### Step 12 – Closing the SSH Session

![Step 12 – Closing the SSH Session](https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/38e6851acaf3444fd7e36408ba5ddf0d9acb92c2/labs/ssh-lab/prints/passo.12.png)

On the VM: exit → connection closed
Back on the host, executed:
```bash
whoami
pwd
```
Confirmed return to the local user (purplghost) and home directory.

### Conclusion

This project demonstrates the complete setup of an SSH server on a Debian virtual machine, including:

Bridged network configuration in VirtualBox
Installation and management of OpenSSH Server
Service control via systemd
Secure remote access and execution of administrative commands
Remote package installation via SSH
Process monitoring with htop

Technologies used:
Oracle VirtualBox • Debian 12 (Trixie) • OpenSSH • systemd • APT • htop

This type of configuration is commonly used in homelab environments, remote Linux servers, and DevOps infrastructure
