## SSH Key Creation Report

------------------------------
## 1. Objective

This report documents the process of generating an SSH key for secure authentication on remote servers or services, such as GitHub, GitLab, or a VPS.

------------------------------

## 2. Tools Used

* Linux Terminal (Kali)
* ssh-keygen command
* Text editor (optional)
* Remote service for adding the public key (GitHub, GitLab, etc.)

------------------------------

![step1](https://github.com/Juliocesar-sec/Cybersecurity-Portfolio/blob/fd4cfa06527f6c962af9080b13301fea7b9527b9/labs/ssh-lab/Virtual-Machine/prints/SSH.01.png)


## 3. Command Executed

```
ssh-keygen -t ed25519 -C "oukn79gq4@mozmail.com"
```

Note: Make sure not to add a space between the - and the C.

------------------------------
## 4. Procedure

1- Open the terminal.
2- Execute the command above.
3- Choose the location to save the key (press Enter to use the default ~/.ssh/id_ed25519).
4- Enter a passphrase for the key (optional, you can press Enter to leave it blank).
5- Creation confirmation:

```
Your identification has been saved in /home/kali/.ssh/id_ed25519
Your public key has been saved in /home/kali/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:XXXXXXXXXXXXXXXXXXXXXXXX oukn79gq4@mozmail.com
```

------------------------------

## 5. Location of the Keys

```
Private key: ~/.ssh/id_ed25519 (do not share)
Public key: ~/.ssh/id_ed25519.pub (share with remote services)
```

------------------------------

## 6. Key Validation
To test if the SSH key works with a remote server or service:

```
ssh -T git@github.com
```

The terminal should display a success message after accepting the initial connection.

------------------------------

## 7. Notes

* Always keep the private key secure.
* Use passphrases to protect the private key whenever possible.
* Document and store in a secure backup if you need to migrate the key to another device.

------------------------------
![step2](https://github.com/Juliocesar-sec/Cybersecurity-Portfolio/blob/c490d973c43e0a03b2af9c1a33dbaafb0e49548f/labs/ssh-lab/Virtual-Machine/prints/SSH.02.png)

## 8. Sharing the Public Key (Remote Machine)

### Method 1: Using `ssh-copy-id` (Recommended)

```bash
ssh-copy-id username@VM_IP
```
* **username** → The user on the Ubuntu VM.
* **VM_IP** → The IP address of the Ubuntu VM.

This command automatically copies your public key to the remote user's `~/.ssh/authorized_keys` file.

### Method 2: Manual Process (Alternative)

1. Display your local public key:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
2. Copy the displayed text content.
3. Connect to your Ubuntu VM:
   ```bash
   ssh username@VM_IP
   ```
4. Create the `.ssh` directory and set permissions if it does not exist:
   ```bash
   mkdir -p ~/.ssh
   chmod 700 ~/.ssh
   ```
5. Append your public key into the `authorized_keys` file:
   ```bash
   echo "PASTE_YOUR_KEY_HERE" >> ~/.ssh/authorized_keys
   chmod 600 ~/.ssh/authorized_keys
   ```

---

## 9. Testing SSH Access

Test your connection after completing the configuration:

```bash
ssh username@VM_IP
```
* You will log in without a password if the key is accepted.
* You will be prompted for your passphrase if your private key uses one.

---

## 10. Security Notes

* Never share your private key.
* Use strong passwords or passphrases.
* Back up your private key securely for recovery.
* Create different keys for different machines or services.





