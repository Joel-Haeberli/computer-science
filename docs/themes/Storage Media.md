tags: #DF #storage

# Storage Media

links: [[702 DF TOC - Storage & Acquisition|DF TOC - Storage & Acquisition]] - [[themes/000 Index|Index]]

---

## Historic Storage

- wire wrap boards, no separate storage
![[wire-wrap-board.png]]
- punch cards, paper tape
- reel-reel magnetic tape

## Modern Storage

> Exam question: which three media types exist?

**Magnetic**

- Magnetic Tape (cartridge)
- Magnetic disks (hard drives)

**Optical**

- Optical discs (CD, DVD, Blu-ray)

**Non-Volatile Memory**

- Flash, SSD, USB sticks

## Historic Interfaces

- ST506/MFM - (1980s, first standard interface)
![[ST506.png]]
- (E)IDE - (Enhanced)Integrated Drive Electronics
- SCSI - Small Computer System Interface ("Scuzzy")
- (P)ATA - (Parallel AT Attachment)

## Modern Interfaces

- SATA - Serial ATA
![[SATA-EIDE.png]]
- SAS - Serial Attached SCSI
- NVME - Non-Volatile Memory Express

## Shift from parallel to serial

- Higher transfer speed
- Smaller cables
- Designed with scalability in mind
- Better drive support (NCQ)

## Bridges and Protocols

In the context of computer storage and interfaces, "bridges" refer to components or software that connect two different systems or data protocols, enabling them to communicate effectively despite having different native languages or operational architectures. These bridges often translate commands and manage data transfer between systems with different standards, ensuring compatibility and functionality across diverse hardware and software environments.

**Common drive interface protocols**
- **ATA Command Set, ATAPI, SCSI, and USB protocols (BOT and UAS)** involve different methods and standards for data transfer and device communication. ATA and ATAPI are more traditional with direct, register-based commands, whereas SCSI and USB (including both BOT and UAS) provide options for networked and peripheral device communications with more advanced features like command queuing.

**Common interface standards**
- **Interface standards like SATA (AHCI), USB (xHCI), and NVMe** define how devices communicate with the computer's operating system through specific controller interfaces, which are crucial for supporting higher speeds and more efficient access to storage media.

In forensics, understanding these protocols and bridges is helpful because they determine how data can be accessed and read from storage devices.

***Forensic tools often need to interface with these various standards to extract data without altering it, which is where write-blockers come into play. Write-blockers are devices or software that prevent data from being written back to the device being examined, thus maintaining the integrity of the data during forensic analysis. This is essential for ensuring that the evidence remains unaltered and is admissible in court.***

## Sector Sizes

- **LBA (Logical Block Addressing)** simplifies the interface by abstracting the physical details of disk storage.
- Drives traditionally use **512-byte sectors**, but modern drives have shifted to **4096-byte sectors** to enhance efficiency and error handling
- **HPA (Host Protected Area, OS inaccessible)** and **DCO (Disk Configuration Overlay)** are specialized areas used by manufacturers that can hide data from the operating system, important for forensic examinations to uncover hidden or manipulated data.
- **ATA security** features help in understanding access controls and security measures on drives, critical for forensic integrity and access.
- drive service area: password in clear text but not easily accessible
- Forensic relevance includes the ability to recover "deleted" data from magnetic disks.

## Non-Volatile Memory (Flash) Drives

- NVME and SATA-Express are different interfaces.
- NVME supports Namespaces, primarily for enterprise use.
- Includes SD cards and USB sticks.
- Flash Translation Layer (FTL) simulates magnetic drives with LBA sectors.
- Over-provisioning in flash memory provides extra blocks to replace defective ones, ensuring data integrity and longevity, which can complicate forensic data recovery efforts.
- "Chip-off" is a forensic technique involving de-soldering chips.
- Memory cells can't be overwritten; they must be deleted first.
- The "TRIM" command allows firmware to delete data in the background.

> Exam question: What is TRIM?
> Answer: On SSDs, the blocks must be erased before they can be used again. This takes some time, which TRIM does in the background.

## Tapes and Optical Disks

**Tapes:**

- **Sequential read and write:** Data is accessed in a linear sequence.
- **EOD (End Of Data) marker:** Indicates the end of the stored data.
- **No need for write-blockers:** If the tape has a read-only lock, additional write protection tools are unnecessary.

**Optical Discs:**

- **Sequential write, random read:** Data is written sequentially but can be read in any order.
- **One long track:** Data is stored in a continuous spiral track, similar to tape.
- **Pits and lands:** Represent binary data, where pits and lands are read by a laser.
- **Read by laser, burned by laser:** Lasers are used to read from and write data to the disc.
- **No need for write-blockers:** Similar to tapes, read-only operations do not require extra write protection.

## Drive Encryption

**Self Encrypting Drives (SEDs):**

- **SED - Self Encrypting Disk:** Uses hardware-based encryption for all data on the disk.
- **Encryption passwords/PINs:** Required for some USB drives.
- **OPAL standard:** Trusted Computing Group standard for managing encryption.
- **Shadow MBR and pre-boot authentication:** Ensures that authentication occurs before booting.
- **Forensic challenges with locked OPAL SEDs:** If an OPAL SED is locked, it cannot be accessed or imaged without the correct encryption keys. This means forensic investigators cannot retrieve any data until the correct credentials are provided. In other words, the drive is essentially inaccessible in its locked state $\rightarrow$ forensically not accessible

**Operating System Full Disk Encryption (FDE):**

- **Examples:**
    - **MS Bitlocker:** Windows-based encryption tool.
    - **Apple FileVault:** Mac OS encryption solution.
    - **Linux LUKS:** Linux-based encryption standard.
- **Forensic imaging of OS-based FDE:** Even though these tools encrypt the entire disk, forensic investigators can create a bit-for-bit copy (forensic image) of the encrypted data. However, this image will remain encrypted. To analyze the data, investigators need the decryption keys or passwords. The difference here is that imaging is possible, but understanding and using the data requires decryption keys $\rightarrow$ forensically accessible

## Other Relevant Topics

1. **Access Methods to Drive Electronics:**
    
    - **JTAG Access:** Utilises the Joint Test Action Group (JTAG) interface for debugging and accessing the inner workings of a device at the hardware level.
    - **TTL/Serial Access:** Employs Transistor-Transistor Logic (TTL) or serial connections to directly communicate with drive electronics.
    - **Security Exploits:** Involves exploiting vulnerabilities in the system's security to gain unauthorized access.
    - **Glitching and Fault Injection:** Introduces faults or glitches deliberately into the system to trigger unintended behaviours that can be exploited for access.
    - **Hardware Hacking:** [https://www.youtube.com/watch?v=dT9y-KQbqi4](https://www.youtube.com/watch?v=dT9y-KQbqi4)

2. **Data Location:**
    
    - **Backups:** Data might be stored in backup systems, either local or remote.
    - **Cloud Sync, Cache, Cluster Distributed:** Data can be synchronized across cloud services, cached for performance, or distributed across a cluster of systems.
    - **Mirrored (RAID):** Redundant Array of Independent Disks (RAID) systems can mirror data across multiple disks for redundancy and improved access speed.

---
links: [[702 DF TOC - Storage & Acquisition|DF TOC - Storage & Acquisition]] - [[themes/000 Index|Index]]