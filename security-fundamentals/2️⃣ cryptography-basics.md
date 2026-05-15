# Cryptography Basics

A beginner-friendly overview of fundamental cryptography concepts commonly used in cybersecurity, networking, and Security+ studies.

---

# Table of Contents

- [What is Cryptography?](#what-is-cryptography)
- [Key Concepts](#key-concepts)
- [Common Encryption Types](#common-encryption-types)
- [Real-World Uses](#real-world-uses)
- [Important Notes](#important-notes)

---

# What is Cryptography?

Cryptography is the practice of securing information by transforming data into protected formats that unauthorized users cannot read or modify.

It is used to protect:

- Confidentiality
- Integrity
- Authentication
- Secure communication

---

# Key Concepts

## Encryption

Encryption converts readable data (**plaintext**) into unreadable data (**ciphertext**) using an encryption key.

### Example

```text
Plaintext:  Hello123
Encrypted: x8F#2Lm!
```

Purpose:
- Protect sensitive information
- Prevent unauthorized access

---

## Decryption

Decryption converts encrypted data back into readable form using the correct key.

### Process

```text
Ciphertext → Key → Plaintext
```

Without the correct key, the original data should remain unreadable.

---

## Symmetric Encryption

Symmetric encryption uses the **same key** for both encryption and decryption.

### Common Algorithm

- AES (Advanced Encryption Standard)

### Advantages

- Fast
- Efficient
- Good for large amounts of data

### Disadvantages

- Key sharing must be secure

### Example Use Cases

- Disk encryption
- VPN traffic
- Secure file storage

---

## Asymmetric Encryption

Asymmetric encryption uses **two keys**:

- Public Key → encrypts data
- Private Key → decrypts data

### Common Algorithm

- RSA

### Advantages

- More secure key exchange
- Supports digital signatures

### Disadvantages

- Slower than symmetric encryption

### Example Use Cases

- HTTPS/SSL certificates
- Secure email
- SSH authentication

---

## Hashing

Hashing is a **one-way transformation** that converts data into a fixed-length value called a hash.

### Common Algorithm

- SHA-256

### Important Properties

- Cannot be reversed
- Same input = same output
- Small changes produce completely different hashes

### Example

```text
Password123
↓
ef92b778bafe771e89245b89ecbc...
```

### Common Uses

- Password storage
- File integrity verification
- Digital signatures

---

# Common Encryption Types

| Type | Key Usage | Example Algorithms |
|------|------------|-------------------|
| Symmetric | Same key | AES, DES |
| Asymmetric | Public/Private keys | RSA, ECC |
| Hashing | No decryption | SHA-256, MD5 |

---

# Real-World Uses

## SSL/TLS

Used to encrypt web traffic between browsers and servers.

### Example

```text
https://example.com
```

Provides:
- Secure communication
- Data confidentiality
- Authentication

---

## VPNs

Virtual Private Networks encrypt remote network connections.

### Benefits

- Secure remote access
- Hide traffic from attackers
- Protect data on public Wi-Fi

---

## Password Storage

Passwords should never be stored in plaintext.

Best practice:
- Hash passwords
- Add salt values
- Use secure algorithms

### Example Algorithms

- bcrypt
- Argon2
- PBKDF2

---

# Important Notes

- Cryptography protects confidentiality and integrity.
- Strong encryption depends on secure key management.
- Weak algorithms or poor implementation can compromise security.
- Understanding cryptography is essential for cybersecurity certifications like Security+.

---

# Recommended Topics to Learn Next

- Digital Certificates
- Public Key Infrastructure (PKI)
- TLS Handshake
- Digital Signatures
- Certificate Authorities (CA)
- HMAC
- Zero Trust Security

---

# License

This document is provided for educational purposes.
