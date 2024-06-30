tags: #DF
# Forensics Questions

links: [[700 DF MOC|DF MOC]] - [[themes/000 Index|Index]]

---

**Who uses digital forensics and why?**

Police (fedpol), NCSC, Military, Companies (SOC/CISO), Security companies (Trend Micro, antivirus companies), Small expert companies

**What is the difference between forensic acquisition and forensic analysis?**

Mostly separate teams
- Acquisition: collection/getting as much data as possible (storage: usb sticks, IoT devices, .../Staubsuger/...), creation of image (specific format, dd, compressed, ...)
- Analysis: data analysis in specific format (...) or raw (dd image), pre-processing data (index, database for search), understand the data (where it started), decompress (e.g. mail with zip attachment containing a word file contains images), correlate logs/cameras/filesystem timestamps/other data

**What are some advantages and disadvantages of using open source forensic tools?**

- Advantages: easy to automate, free, modifications possible
- Disadvantages: no access to proprietary data, support not always good, mostly not a nice GUI

**What are the requirements of NIST CFTT for a forensic acquisition?**

Forensic sound/completness (e.g. sector 0 to last)

**What kinds of non-forensic tools are good for doing forensic work?**

- *Designed for forensic*: Sleuthkit, dcfldd, dc3dd
- *Not designed with forensic in mind (but brilliant as well)*: password cracking tool, image repair tools, data recovery tools, troubleshooting tools

**What are some typical storage types acquired in digital forensics?**

Cables & Protocols, Smartdata (e.g. there was data written, where is it?)

- Optical: Disks
- Magnetic: Tape
- non volatile memory: NVME SSD, USB

**What are some typical drive interfaces used to connect the storage?**

Modern: SATA, SAS, NVME
Historical: IDE, SCSI, ATA

**What are the common sector sizes on a storage device?**

Traditional 512bytes, now 4096bytes

**What is the job of the flash translation layer (FTL) in SSDs?**

Responsible for mapping logical block addresses used by the operating system to physical block addresses on flash memory devices, managing wear leveling and bad block remapping to optimize performance and extend the lifespan of the storage medium.

**Why is deleted data usually found on magnetic storage devices?**

No TRIM command, only pointer is deleted not data itself

**Why is deleted data usually not found on SSDs?**

TRIM, garbage collection

**How do you preserve the integrity of a forensic image?**

Hash of disk, hash-window

**What is the reason for using a Write-Blocker?**

OS/Computer creates, touches and modifies data which destroys evidence (thumbnail, antivirus, timestamps, ...).

**What old UNIX tool is still used today for forensic imaging? Why?**

dd

**What are some forensic formats, and what advantages do they provide?**

- EnCase EWF, FTK SMART, Afflib $\rightarrow$ investigators, notes, photograph, location found
- RAW (dd)
- Compression is useful to save space but for access a file, the whole disk must be uncompressed which takes time and also storage then.
- Encryption might be necessary to protect data

**Describe a few Sleuthkit tools and where they are used**

Analyze blocks, icat, mmls, ...

**Explain "slack"**

- A 3,5k file needs 4k block $\rightarrow$ slack space is left space of block
- memory slack
- slack space of file system and partition

**Explain different offsets found in forensic work**

Byte offset, Sector offset, Block offset

**Explain the different between a sector, filesystem block, and inode**

- **Sector:** Physical unit of storage on the disk.
- **Filesystem Block:** Logical unit of data storage used by the filesystem, consisting of one or more sectors.
- **Inode:** A data structure that describes files and directories, pointing to where their data blocks are located on the disk.

**What is NSRL?**

- Hash DB / Hash set
- Used to filter out unimportant data (Hashes of Excel Software files for example)
- Find specific files or types of files (illegal images, malware)

**What are hash databases (or hash sets) good for?**

- Ignore known files which are not interesting (common software files)
- Left are modified files, created/new files

**What kind of operating system artifacts are interesting in forensics?**

- Logs shutdown, login, logout, user logs, shell history
- files downloaded
- config
- Software logs (What tools were installed / uninstalled)

**What kind of application artifacts are interesting in forensics?**

- Application cache
- Browsing history
- Previously opened docume

**What is the difference between static and dynamic analysis of executable code?**

- Not part of exam

**Explain forensic carving and what it is**

 - Used when filesystem is corrupted or disk is partially destroyed
- Looking at raw sectors / blocks to recover files
- Looking at header, footer, structure
- Carving files vs carving strings

**What is the UNIX epoch, and why is that important to know in forensics?**

- Seconds since 01.01.1970
- Often used as timestamp

**What are the MACB timestamps and what do they mean?**

- Modified, Accessed, Changed, Birth Timestamps
- File Metadata

**What are some challenges with making timelines?**

- Time not always synced
- Timeszones
- Automatic Sync when user is travelling

**What are the different types of encryption implementations that can be found in a forensic analysis?**

- OPAL (Encryption on firmware level, OS doesn't know anything is encrypted)
- Encryption on Block layer (Bitlocker, Filevault)
- Encrypt files / folders
- One of biggest challenges for forensics

**What are the possibilities for recovering passwords or keys?**

Keys might be on the drive, someone might know it, brute force, rainbow table

**What is steganography?**

- Hide data inside data (z.B. least signification bit in pixels)

**Mobile Forensics**

- Problems
	- Unlocking is very hard
	- Encryption (chipoff won't help)
	- Proprietary interfaces
	- Proprietary file formats
	- Can't remove battery / disable radio (User can still remote wipe) $\rightarrow$ Solution:  Faraday cage to block radio waves
- Mobile forensic companies buy exploits for tools
- Mobile artifacts
	![[mobile-artifacts.png]]

---
links: [[700 DF MOC|DF MOC]] - [[themes/000 Index|Index]]