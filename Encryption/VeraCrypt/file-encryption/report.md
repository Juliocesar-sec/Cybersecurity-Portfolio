# 🔐 Report: Creation and Mounting of an Encrypted Volume with VeraCrypt

### 📁 Cybersecurity Portfolio
**Author:** [Jota Dev]  
**Date:** April 2026

---

## 📌 Introduction

This report documents, in a detailed step-by-step manner, the complete process of **creating, mounting, and functionally validating an encrypted file container** using VeraCrypt in a Linux environment.

The objective is to demonstrate practical knowledge of **data-at-rest encryption**, with emphasis on security best practices, including:
- Selection of strong algorithms (**AES-256 + SHA-512**)
- Generation of a complex password using Proton Pass
- Proper entropy collection during formatting
- Creation of a standard (non-hidden) container
- Secure volume mounting
- Read/write validation
- Secure file behavior outside the software

The process was carried out in a Linux virtual machine for demonstration and portfolio-building purposes.

---

## 🖥️ Environment Used

- Operating System: Linux (XFCE desktop environment)
- Tools used:
  - **VeraCrypt** (latest available version)
  - **Proton Pass** (password generation)
  - **Thunar** (file manager)

---

## ⚙️ Step-by-Step Description with Image Explanations

### 🖼️ Image 1 – VeraCrypt Main Window
![VeraCrypt Main Window](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.png)
The main VeraCrypt window was opened. I clicked **"Create Volume"** to start the volume creation wizard.
This is the software’s initial interface, where the user selects the mount slot for the encrypted volume.

🔐 Security best practice observed:
The “Never save history” option is enabled, preventing storage of usage traces.

### 🖼️ Image 2 – Volume Type
![Volume Type](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.1.arquivo.png)
I selected **"Create an encrypted file container"** → **"Standard VeraCrypt volume"**. I chose a standard (non-hidden) volume as it is sufficient to demonstrate portability and basic protection.
The standard volume was chosen for its simplicity and portability.

🛡️ Security note:
The presence of the hidden volume option demonstrates awareness of advanced plausible deniability techniques, even though it was not used in this scenario.

### 🖼️ Image 3 – Container Location
![Container Location](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.2.arquivo.png)  
I selected the destination folder and named the file `secure-volume.vc`. This will be a single portable container.
A file-based container was chosen, allowing:

portability
easy backup
secure transfer

⚠️ Important event:
VeraCrypt detected an existing file. Overwrite was manually confirmed.

### 🖼️ Image 4 – Encryption Options
![Encryption Options](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.3.arquivo.png)    
I chose **AES-256** as the encryption algorithm and **SHA-512** as the hash function. This combination provides excellent security and performance.
🛡️ Conclusion:
Highly secure configuration suitable for professional use.

### 🖼️ Image 5 – Volume Size
![Volume Size](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.4.arquivo.png)
I set the volume size to **500 MB** (sufficient for demonstration purposes).
A balanced choice for:

practical testing
real-world simulation

📌 Observation:
The size can be adjusted according to operational requirements.

### 🖼️ Image 6 – Volume Password
![Volume Password](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.5.arquivo.png)  
I generated a strong, long password using **Proton Pass**. The password contains uppercase/lowercase letters, numbers, and symbols, with more than 20 characters.
high entropy
use of special characters
automated generation

🛡️ Critical best practice:
Completely avoids predictable or reused passwords.

### 🖼️ Image 7 – Volume Formatting
![Volume Formatting](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.6.arquivo.png)  
During the formatting screen, I moved the mouse randomly for approximately **45 seconds** until the randomness indicator turned green. This collects sufficient entropy to generate strong cryptographic keys. I selected **exFAT** as the filesystem to ensure **cross-platform compatibility** (Linux, Windows, and macOS).

At this stage:
cryptographic keys are generated
entropy ensures unpredictability
the volume is internally structured

🔐 Importance:
The greater the entropy, the stronger the volume security.

### 🖼️ Image 8 – Overwrite Confirmation and Formatting Process
![Overwrite Confirmation](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.7.arquivo.png)  
I confirmed the overwrite and monitored the formatting process.
At this step, VeraCrypt requested confirmation to replace the previously existing container.

⚠️ Important event:
Overwrite was manually authorized, demonstrating operational awareness regarding:

loss of previous contents
complete regeneration of cryptographic keys
reinitialization of the internal volume structure

🛡️ Best practice observed:
Explicit confirmation prevents accidental overwrites.

### 🖼️ Image 9 – Volume Successfully Created (Part 1)
![Volume Successfully Created](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.8.arquivo.png)
VeraCrypt pop-up message displayed:

“The VeraCrypt volume has been successfully created.”

Formatting process completed
Main window still open in the background

### 🖼️ Image 10 – Final “Volume Created” Screen
![Final Volume Created](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.9.arquivo.png)  
The volume was successfully created.
✔️ Immediate result:
The volume is now ready for mounting, authentication, and secure use.

### 🖼️ Image 11 – Volume Selection for Mounting
![Volume Selection for Mounting](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.10.arquivo.png)  
I selected slot 1 and chose the container file.
This step begins the encrypted volume mounting process.

The file appears as Unknown because it is a binary encrypted container rather than a standard system-readable file format.

🛡️ Best practice observed:
Using the native file selector reduces path errors and mistyping risks.

### 🖼️ Image 12 – Mount Password Entry
![Mount Password Entry](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.11.arquivo.png)  
I entered the previously generated password.
This step demonstrates a secure authentication flow in which the strong password is retrieved directly from the password manager.

🔐 Security relevance:
Using Proton Pass drastically reduces the risk of reused, weak, or insecurely stored passwords.

### 🖼️ Image 13 – Administrator Privilege Request
![Administrator Privilege Request](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.12.arquivo.png.png)  
The system requested administrator privileges (sudo) to mount the volume.
In Linux systems, mounting under /media/ requires elevated privileges.

⚠️ Important event:
Privilege escalation is required only for the mounting operation and does not affect the container’s cryptographic security.

### 🖼️ Image 14 – Volume Mounted Successfully
![Volume Mounted Successfully](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.13.arquivo.png)  
The volume was mounted correctly and appeared as a removable disk in Thunar.
The volume was successfully mounted and is accessible as a normal directory while open.

The data remains decrypted only in memory during active use, returning to protected state after dismount.

🛡️ Critical best practice:
Immediate dismount after use is recommended to restore at-rest protection.

### 🖼️ Image 15 – Attempt to Open the Container Directly
![Attempt to Open Container Directly](https://github.com/Juliocesar-sec/Criptografia.VeraCrypt/blob/f1de33fdc39fc3fc17f07c7e8468ef653614af36/file-encryption/prints/print-vera.14.arquivo.png)  
When trying to open the `.vc` file directly with the file manager, the content appears as unreadable binary data — proving that the encryption is working correctly.
This demonstrates the expected behavior when attempting to open the container outside VeraCrypt.

The operating system recognizes it as an encrypted binary blob with no associated application.

⚠️ Security warning:
The container should never be directly edited or manipulated through the file manager, as this may compromise its structural integrity.

---

## 🔒 Results Achieved

- Encrypted volume successfully created
- Portable container compatible with multiple operating systems
- Effective data-at-rest protection
- Secure mounting and unmounting performed
- Functional validation: copied text and image files into the volume, read and modified the content, unmounted and remounted the volume without data loss
- Direct access attempt to the container failed (data remains encrypted)

---

## 🛡️ Security Conclusions and Lessons Learned

This exercise demonstrated the following cybersecurity competencies:

- Correct and complete usage of VeraCrypt
- Application of strong cryptographic algorithms (AES-256 + SHA-512)
- Importance of entropy collection during key generation
- Conscious choice of filesystem (**exFAT**) for cross-platform portability
- Secure password generation and management
- Practical validation that the container file reveals no data without the correct password
- Operational best practices: never leave the volume mounted unnecessarily and always unmount after use

**Key Lessons:**
- Entropy is critical for the strength of cryptographic keys — random mouse movement is a simple and effective way to increase it.
- VeraCrypt containers are an excellent solution for secure backups and transportation of sensitive data.
- In corporate environments, this technique can be combined with password policies, keyfiles, or hidden volumes to further increase security.

---

## 📚 Final Considerations

The created volume can be mounted on Linux, Windows, and macOS without issues, making it an efficient solution for:
- Secure storage of sensitive data
- Encrypted backups
- Protection against unauthorized access in case of device loss or theft

This skill is essential for information security professionals.

---

## 🧰 Tools Used

- VeraCrypt
- Proton Pass
- Linux (test environment)


