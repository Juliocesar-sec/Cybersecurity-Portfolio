## SSH Keys Protected with VeraCrypt – Practical Guide


📌 What is this setup?

This setup is a local security architecture where SSH private keys are stored inside an encrypted VeraCrypt volume instead of the default `~/.ssh` directory.

Instead of keeping sensitive authentication keys directly exposed in the home folder, they are moved into an encrypted container and accessed transparently through symbolic links.

This creates a secure “SSH vault” while preserving normal SSH usability.


## What this setup is used for

This architecture is used to improve local system security without changing SSH workflows.

It is commonly used for:

* Protecting SSH private keys at rest
* Reducing exposure of credentials in case of system compromise
* Keeping development workflow unchanged while increasing security
* Separating sensitive cryptographic material from user directories
* Creating portable encrypted key storage (VeraCrypt container)



## Where this setup applies

This configuration is designed for Linux-based environments and can be used in:

* Debian / Ubuntu desktop systems
* Development machines (laptops, workstations)
* Virtual machines (VirtualBox, QEMU)
* Secure home-lab environments
* Dual-boot systems with shared SSH usage



## Why this setup is widely used

This approach is popular because it adds a strong security layer without requiring changes to SSH itself.

Instead of modifying OpenSSH behavior, it relies on filesystem-level encryption.

Key advantages include:

* Transparent usage via symbolic links
* Strong encryption provided by VeraCrypt
* No changes required to SSH configuration
* Full control over when keys are accessible
* Reduced attack surface on `~/.ssh`



## Why use encrypted SSH key storage?

SSH private keys are highly sensitive because they grant authentication access to remote systems.

Storing them in plain text inside `~/.ssh` exposes them to risks such as:

* Local malware or privilege escalation
* Accidental backup leaks
* Unauthorized access in multi-user systems

Using VeraCrypt mitigates these risks by ensuring keys are only accessible when the encrypted volume is mounted.



## Basic Concepts

Understanding this setup requires knowledge of three core components:

### 🔐 VeraCrypt encrypted container

A file-based encrypted volume that acts like a secure virtual disk.

* Stores SSH private keys inside an encrypted filesystem
* Requires mounting before access
* Automatically hides contents when unmounted

Example:

```
~/.ssh/saizoiao.lo
```

### 🔗 Symbolic links (symlinks)

Symlinks act as pointers from `~/.ssh` to the encrypted volume.

Example:

```
~/.ssh/id_ed25519 → /media/veracrypt3/keys/id_ed25519
```

They allow SSH to function normally without knowing where the real file is stored.


### 🔑 SSH agent integration

The SSH agent loads decrypted keys into memory temporarily.

* Keys are unlocked via passphrase
* Stored only in RAM during session
* Used for authentication without retyping password

Command:

```bash
ssh-add ~/.ssh/id_ed25519
```

**Installation / Setup Summary**

1. Create or mount VeraCrypt volume

```
veracrypt ~/.ssh/saizoiao.lo /media/veracrypt3
```

2. Create secure key directory inside volume

```
mkdir -p /media/veracrypt3/keys
chmod 700 /media/veracrypt3/keys
```

3. Move SSH private keys into encrypted storage

```
mv ~/.ssh/id_ed25519 /media/veracrypt3/keys/
mv ~/.ssh/id_rsa_sft /media/veracrypt3/keys/
```



