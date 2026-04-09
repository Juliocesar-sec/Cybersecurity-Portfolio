Portfolio Report: Remote Access Setup via SSH

Project: SSH Server Configuration on a Debian Virtual Machine
Environment: Oracle VirtualBox + Debian 12 (Trixie)
Date: April 2026

Objective

Configure a Debian virtual machine to allow secure remote access via SSH from the host, using a Bridged network. The project demonstrates everything from network setup to executing administrative commands remotely.

Step-by-Step
Step 1 – Network Configuration (Bridged Adapter)

! Image: Step.1.png (https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/Passo.1.png)

In the Oracle VirtualBox Manager, I accessed the settings of the VM "DB".
Under Network → Adapter 1, I configured:

Attached to: Bridged Adapter
Name: enp0s31f6 (host network interface)
Adapter Type: Intel PRO/1000 MT Desktop
Promiscuous Mode: Deny
Cable Connected: Enabled

This setup allows the VM to obtain a real IP from the local network, enabling direct SSH access.

Step 2 – Repository Update

Image: Step.2.png (https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/passo.2.png)

On the host terminal (purplghost@DEBIAN): sudo apt update
On the VM (vboxuser@vbox): sudo apt update

Result: Repositories successfully updated on the virtual machine (some warnings appeared on the host, but they did not affect the process).

Step 3 – OpenSSH Server Installation

Image: Step.3.png (https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/passo.3.png)

On the VM, I ran:

sudo apt install openssh-server -y
Step 4 – Enable and Start SSH Service

Image: Step.4.png (https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/d2f5533b025d2a78a75168c2ce3b2689b586735a/labs/ssh-lab/prints/passo.4.png)

Executed:

sudo systemctl enable --now ssh
Step 5 – Verify SSH Service Status

Image: Step.5.png (https://github.com/Juliocesar-sec/cybersecurity-learning-portfolio/blob/main/labs/ssh-lab/prints/passo.4.png?raw=true)

Command:

sudo systemctl status ssh

Result:

Service active (running)
Listening on port 22
Main PID: 6927 (OpenBSD Secure Shell server)
Step 6 – SSH Connection from the Host

Image: Step.6.png

On the host terminal, I connected:

ssh vboxuser@192.168.8.173

Entered the password for vboxuser, and the remote connection was successfully established.

Step 7 – Successful SSH Session

Image: Step.7.png

Debian GNU/Linux 12 banner appeared
Prompt changed to vboxuser@vbox:~$
Verified inside the VM using hostname -I
Step 8 – Package Search via SSH

Image: Step.8.png

Within the SSH session, executed:

sudo apt search htop
dpkg -l | grep htop

Confirmed that the htop package was not installed on the VM yet.

Step 9 – Install htop via SSH

Image: Step.9.png

Installed the package remotely:

sudo apt update && sudo apt install -y htop

htop was successfully downloaded and installed through the SSH connection.

Step 10 – Disable SSH Service

Image: Step.10.png

For remote control demonstration, executed:

sudo systemctl disable --now ssh

The SSH service was stopped and disabled successfully.

Step 11 – Running htop and Checking Logs

Image: Step.11.png

Ran htop in the SSH session (interactive process viewer)
On the host, htop returned “command not found” (package not installed locally)
Checked SSH service logs using journalctl
Step 12 – Closing the SSH Session

Image: Step.12.png

On the VM: exit → connection closed
Back on the host, executed:
whoami
pwd

Confirmed return to the local user (purplghost) and home directory.

Conclusion

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
