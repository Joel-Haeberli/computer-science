tags: #DF #partition
 
# Partition Analysis

links: [[703 DF TOC - Analysis & Carving|DF TOC - Analysis & Carving]] - [[themes/000 Index|Index]]

---

## Overview

**Why Do We Have Partitions on a Drive?**

Partitions help organize a storage device into sections, each containing its own filesystem. While common, partitions are not strictly required; for instance, USB sticks sometimes lack partitions. Partitions are defined in the "partition table," and in some systems, they may be referred to as "slices" (BSD/Solaris terminology).

**Common Partition Schemes**

- DOS
	- Partition table is defined in sector 0 
	- max disk size of 2TB
	- max 4 partitions (and extended) 
	- bootable partitions use MBR in sector 0
- GPT (GUID Partition Table)
	- 128 partitions  
	- max drive size 8 Zetabytes  
	- allows additional meta data about partitions 
	- backup partition table at end of drive 
	- protective mbr in sector zero (type EE)
	- UEFI booting (small FAT partition)
- BSD
	- Uses the concept of "slices"
	- Common in BSD Unix systems
- SUN (VTOC - Volume Table of Contents)
	- Used in Solaris systems
- APM (Apple Partition Map)
	- Used in older Apple systems

## Partition Analysis

### Partition scheme identification with TSK (The Sleuth Kit)

- List supported partitions: `mmstat -t list`
- Identify partition scheme: `mmstat /dev/sda`
	- Alternatively, analyze sector 0 with a hex editor to manually identify the partition scheme
- `disktype` tool identifies partitions and the filesystems within them

**NVMe Drives**

- NVMe drives have "namespaces" that can partition a drive at a lower layer.
- Unlike traditional partition tables written on disk, namespaces are configured via firmware.
- Most consumer NVMe drives have a single namespace.

### Analyze Partition Table

The following commands can be used for devices and images

- `fdisk -l /dev/sda`
- `disktype image.dd`
- `mmls /dev/sda`
- `hexedit -s /dev/sda` (for real adventures)

### Areas of Forensic interest

1. Deleted Partitions
	-  These are partitions that have been removed but may still contain recoverable data.
2. Inter-Partition Gaps
	-  These are spaces between partitions that can contain residual data.
3. Partition Slack
	- This is the space between the end of the filesystem and the end of the partition, which can also contain residual data.

**Searching for Deleted Partitions**

- Using TSK (The Sleuth Kit)
    - Basic, Generic Patterns
        - Command: `sigfind -t ext2 /dev/sda`
        - This searches for ext2 filesystem signatures to locate deleted partitions.
- Using gpart
    - Identify Partitions
        - Command: `gpart -g /dev/sda`
        - Command: `gpart -f -g /dev/sda`
        - These commands search for partition table entries and attempt to recover deleted partitions.
- Using testdisk
    - List Partitions
        - Command: `testdisk /list /dev/sdb`
        - This command lists partitions and can help in recovering deleted partitions.

**Filesystem identification**

- `disktype /dev/sda`
- `fsstat /dev/sda`
- `fsstat -o 2048 /dev/sda`: with offset of 2048

- **Note**
	- Filesystems start at some offset from the start drive
	- corrupt or partially overwritten filesystems may need [[Carving]]
	- a filesystem can exist without a partition table
	- stacked systems may exist (LVM, encryption, RAID)

---
links: [[703 DF TOC - Analysis & Carving|DF TOC - Analysis & Carving]] - [[themes/000 Index|Index]]