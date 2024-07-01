tags: #DF #encryption
 
# Encryption

links: [[705 DF TOC - Encryption & Timelines & Find|DF TOC -Encryption & Timelines & Find]] - [[themes/000 Index|Index]]

---

## Overview

Encryption and forensics is a hot topic in the forensics community. On one hand, encryption protects individuals' privacy and security. On the other, it can conceal criminal activity. The debate is polarized, with extremes advocating for either full police access to encrypted data or no access at all.

## Data Encryption

> Exam question: What are typical data encryption tools for the different storage layers
### Typical Data Encryption - Storage

Forensic examiners often encounter various types of encryption when analyzing storage media. These include:

- **Application File Encryption:** Encrypted documents such as protected PDFs and office files.
- **Individual File Containers:** Encryption tools like GPG and encrypted ZIP files.
- **Directories:** File systems with encryption features, such as ecryptfs and ext4 encryption.
- **Volumes:** Encrypted volumes using software like [[Carving#Special File Carving|TrueCrypt]] and Veracrypt.
- **Block Devices:** Full disk encryption technologies like Linux LUKS, Microsoft Bitlocker, and Apple FileVault.
- **Drive Hardware:** [[Storage Media#Drive Encryption|Self-encrypting drives (SEDs)]] following the OPAL standard.

Decrypting these requires various methods, including passwords or passphrases, cryptographic key strings or key files, and hardware tokens such as smartcards. The primary forensic challenge is to locate the necessary decryption keys.

### Encryption and Network Forensics

In network forensics, analysts encounter several types of encryption across different network layers:

- **Application Layer Encryption:** Proprietary protocols and encrypted data fields (e.g. TSIG in DNS)
- **Transport Layer Encryption:** Protocols such as HTTPS, [[TLS]] (including starttls and implicit TLS), and [[SSH]].
- **IP Layer Encryption:** Virtual Private Networks (VPNs) using [[IPSec]], [[Wireguard]], or [[OpenVPN]].
- **Link-Layer Encryption:** Hardware-based encryption in point-to-point connections, such as modem encryptors.

Decrypting network traffic involves capturing network traffic through passive wiretaps, executing man-in-the-middle (MITM) attacks to manipulate traffic, compromising at least one endpoint, or obtaining secret or session keys. These tasks are further complicated by the use of Perfect Forward Secrecy (PFS), which ensures session keys are not compromised even if long-term keys are.

## Finding Passwords and Decryption Keys

### Methods for Password and Key Recovery

> Exam question: Which methods exist to find password/keys

Forensic analysts use various methods to recover passwords and decryption keys:

1. **Brute Force and Dictionary Attacks:** Exhaustively trying all possible passwords or using common password lists.
2. **Cryptanalysis:** Identifying weaknesses in cryptographic algorithms to reduce keyspace.
3. **Locating Stored Passwords:** Finding passwords saved, written down, or transferred (e.g. file was sent per mail, go to other party)
4. **Password Reuse:** Trying known passwords reused across multiple accounts or devices.
5. **Legal Compulsion:** Court orders to produce passwords.
6. **Cooperative Assistance:** Owners or accomplices providing passwords.
7. **Key Backup/Escrow:** Accessing enterprise key backups.
8. **Exploits and Vulnerabilities:** Using software/hardware exploits or backdoors.
9. **Social Engineering:** Tricks like phishing, forced biometrics, or keyloggers.
10. **Observation:** Using high-definition CCTV or telescopes to capture passwords.

### Brute Force Attacks

Brute force attacks systematically guess passwords until the correct one is found. Strategies to improve success include:

- **Reducing Search Space:** Using smart wordlists or dictionaries.
- **Using GPU Clusters:** Leveraging graphics card processing power.
- **Rainbow Tables:** Utilizing precomputed cryptographic hash tables.
- **Memory Extraction:** Extracting keys from memory via PCI-bus DMA (direct memory access) attacks.
- **Network Attacks:** Performing man-in-the-middle or endpoint attacks.

Caution is required with systems that block access or wipe data after failed attempts.

**Examples**

- [[Password Based Key Derivation Function (PBKDF)|PBKDF2]] allows storing passwords in a format that is hard to brute force

### Recovery Tools

There are numerous tools for password and key recovery:

- **Commercial Tools:** Effective but often expensive; some repackage open source tools.
- **Open Source Tools:** Reliable and customizable, such as:
	- **John the Ripper:** Customizable password cracking.
	- **HashCat:** GPU-accelerated password recovery.
	- **[[Carving#Carving for strings|bulk_extractor]]:** Forensic tool creating wordlists from disk images.
	- **Inception:** PCI-based DMA memory dumper.

### Hardware Attacks

Hardware attacks reveal private keys via side-channel analysis or fault injection:

- **Side-Channel Attacks (passive):** Analyzing voltage/current differences or electromagnetic radiation.
- **Fault Injection (active):** Using over-voltage, under-voltage, electromagnetic pulses, or clock manipulation to alter device behavior.

Targets include TPMs, smartcards, bitcoin wallets, and car electronics.

### Current Research

Research focuses on analyzing electromagnetic radiation and electrical signal variations to reduce keyspace, enhancing the efficiency and speed of key recovery.

## Steganography

Steganography is a technique used in anti-forensics to hide data in non-obvious places, making it difficult to detect. Common methods include:

- **Least Significant Bits:** Embedding data in the least significant bits of color values in images or sound samples.
- **Slack Space:** Hiding data in unused areas of files or disk space.
- **Hidden Volumes:** Using tools like Veracrypt to create hidden volumes within existing volumes.

### Tools for Steganography

Several tools are available for steganography:

- **stegdetect:** Detects steganographic content in images.
- **stegsnow:** Hides data in ASCII text files.
- **openstego:** A tool for general-purpose steganography.
- **busysteg:** Embeds data in various file formats.
- **gsteg:** A steganography tool for images.
- **photocrypt:** Hides data in image files.

### Network Steganography

Steganography can also be applied to network communication, using covert channels and anonymization techniques to hide data within regular network traffic, making it difficult to detect and intercept.

---
links: [[705 DF TOC - Encryption & Timelines & Find|DF TOC -Encryption & Timelines & Find]] - [[themes/000 Index|Index]]