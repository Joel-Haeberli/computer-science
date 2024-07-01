tags: #DF #filesystem
 
# Filesystem Analysis

links: [[703 DF TOC - Analysis & Carving|DF TOC - Analysis & Carving]] - [[themes/000 Index|Index]]

---

## Overview

Filesystems serve several essential functions on a storage device:

- **Organize Data**: Structure data into files and directories (or folders).
- **Maintain Metadata**: Store important information such as timestamps, permissions, and attributes.
- **Provide Additional Features**: Enhance storage capabilities with features like data integrity checks, encryption, volume management, and quotas.

### Examples of Filesystems

1. **Common Filesystems Today**
    - **FAT**: Simple and widely supported.
    - **NTFS**: Used primarily in Windows environments.
    - **EXT4**: Common in Linux systems.
    - **XFS**: Known for high performance and scalability.
    - **HFS+**: Used in older macOS versions.
2. **Newer Filesystems**
    - **BTRFS**: Offers advanced features like snapshotting and self-healing.
    - **APFS**: The default filesystem for newer macOS versions, optimized for SSDs.
    - **ZFS**: Provides high data integrity and scalability, using Copy-on-Write (CoW) technology.

### Special Types of Filesystems

- **Network Filesystems and Distributed Filesystems**
    - Not covered in this forensics class.
- **FUSE (Filesystem in Userspace)**
    - Allows user-level applications to create filesystems.
    - **Pros**: Easy user access.
    - **Cons**: Not suitable for low-level forensics.

Filesystems create a hierarchical abstraction layer, making it easier for users and programs to manage and access data.

## Filesystem Forensics

### Why Perform Filesystem Forensics?

- **Identify the Filesystem Used**: Determine the type of filesystem to understand its structure and capabilities.
- **Analyze Filesystem Metadata**: Extract information like the filesystem label, last mounted date, and other relevant metadata.
- **Analyze File Metadata**: Examine inodes, timestamps, ownership, and other attributes to gather details about individual files.
- **Recover Files**: Retrieve existing and deleted files from the filesystem.
- **Recover File Fragments**: Extract data from slack space and unallocated areas to recover file fragments.
- **Find Attempts to Hide Data**: Detect efforts to disguise files by changing extensions (e.g., renaming *.jpg to *.exe).
- **Hash Individual Files**: Create hashes for files to facilitate searches and eliminate known files from evidence.
- **Extract Evidence from Corrupted or Partially Wiped Filesystems**: Gather data even when filesystems are damaged or partially erased.
- **Reconstruct Past Events with Timelines**: Use timestamps and other metadata to build timelines of file and system activities.
- **Special Topics**: Handle advanced features like RAID, journaled filesystems, and encrypted filesystems.

### Concepts

> Exam question: What concepts are important for filesystem forensics
#### Areas of Forensic Interest on a Storage Drive

- **Sector**: A sector is the smallest accessible unit on a drive or device.
- **Block**: A block consists of consecutive sectors and represents the smallest accessible unit on a filesystem.
- **Allocated Blocks**: Allocated blocks are filesystem blocks that are currently assigned to files.
- **Unallocated Blocks**: Unallocated blocks are filesystem blocks that are not currently assigned to files. However, these blocks may still contain residual data from previously allocated files.
- **Inodes**: Inodes are metadata structures that describe files and directories. In NTFS, this structure is known as the Master File Table (MFT).
- **Interpartition Gaps**: Interpartition gaps are the areas between partitions. These gaps can potentially contain remnants of previously existing filesystems.

#### Forensic Term: "Slack"

- **Partition Slack**: Partition slack is the space between the end of a partition and the end of the disk.
- **Volume Slack**: Volume slack refers to the space between the end of the filesystem and the end of the partition.
- **File Slack**: File slack is the space between the end of a file and the end of the block.
- **RAM Slack**: RAM slack is the space between the end of a file and the end of the sector.
- **Note**: The significance of slack space has decreased in modern systems due to the use of 4k sectors, operating systems' data wiping mechanisms, and the TRIM command, which optimizes storage by managing deleted data on SSDs.

### Filesystem identification

- Using disktype
    - Command: `disktype /dev/sda`
    - This command identifies the partition layout and the filesystems present on the specified device.
- Using fsstat
	- Command: `fsstat -f list`
		- This command lists the filesystems supported by The Sleuth Kit (TSK)
	- Command: `fsstat /dev/sda1`
		- Provides detailed information about the filesystem on the specified partition.
	- Command: `fsstat partition-image.dd`
		- Analyzes a filesystem within an image file.
	- Command: `fsstat -o 2048 /dev/sda`
		- Specifies an offset (2048 in this case) to start analyzing the filesystem.

### Filesystem access

#### Via Normal Kernel Devices

1. **Raw Devices**:
    - Examples: `/dev/sda`, `/dev/mmcblk0`, `/dev/nvme0n1`
2. **Partition Devices**:
    - Examples: `/dev/sda1`, `/dev/nvme0n1p1`

#### Create (or Remove) Linux Kernel Loop Devices for a Forensic Image

- Loop devices are created using `losetup`.

**Commands:**

1. Create Loop Device:
   
```bash
sudo losetup --find --partscan --read-only image.dd
```

2. Remove Loop Device:

```bash
sudo losetup -D loop0
```

#### Via Calculated Offsets

Offsets must be carefully calculated, ensuring the correct units are used.

1. **Byte Offsets**:
    - Note: Character offsets could be 2 bytes due to Unicode.
2. **Sector Offsets**:
    - Sector size is not always 512 bytes.
3. **Block Offsets**:
    - Remember to subtract the partition sector offset.

**Example Calculation:**

Using shell math:

```bash
echo $((1024000/512))
```

#### Forensic Analysis Tools

- Tools can act directly on the device or on a forensically acquired image.
- Mounting is not needed for forensic analysis.

### Sectors, Block, Inodes, Filenames

**If I Know X, How to Find Y**

1. **I know the drive sector, what is the filesystem block?**

```bash 
echo $(((sectornumber - partitionoffset) * sectorsize / blocksize))
```

2. **Is the filesystem block allocated?**

```bash
blkstat /dev/sdb1 1025
```

3. **I know the block, what is the allocated inode?**

```bash
ifind -d 1025 /dev/sdb1
```

4. **I know the inode, what is the filename?**

```bash
ffind /dev/sdb1 14
```

5. **I know the filename, what is the inode?**

```bash
ifind -n "hello.txt" /dev/sdb1
```

6. **I want more info about an inode:**

```bash
istat /dev/sdb1 14
```

Always double-check units and offsets!

### Data Extraction Techniques

#### Extracting Sectors and Blocks

**Examples of Extracting Sectors and Blocks**

- **Sleuthkit’s `blkcat`** is similar to `dd` but more filesystem-aware.
- **Sleuthkit’s `blkls`** focuses on filesystem awareness.

**Extract drive sectors using `dd` with offset:**
```bash
dd if=/dev/sda of=data.dd skip=8000 count=25
```

**Extract blocks 1000-1009 from a partition image:**
```bash
blkcat partition.dd 1000 10
```

**Extract all unallocated blocks from a filesystem:**
```bash
blkls -A partition.dd > unalloc.blkls
```

**Extract all file slack space from a filesystem:**
```bash
blkls -s partition.dd > slack.blkls
```

**Extract specific block from an image:**
```bash
blkcat -h image.dd 5436
```

**For `blkls` readable output:**

- `-a` for ASCII
- `-h` for hex
- `-w` for HTML

**Use `blkcalc` to map back to locations in the original image.**

#### Listing and Extracting: Inodes and Files

**Find an Interesting Filename or Inode and Extract It**

List files and directories with `fls`:

- `?/?` indicates a directory/inode entry
- `*` indicates a deleted file

```bash
fls -r -l -p /dev/sdb1
fls -r -d /dev/sdb1
```

**List inodes with `ils`:**
```bash
ils /dev/sdb1
```

**Extract file contents of inode with `icat`:**
```bash
icat /dev/sdb1 14
```

**Extract file contents of filename with `fcat` (-s for slack):**
```bash
fcat hello.txt /dev/sdb1 > hello.txt
fcat -s hello.txt /dev/sdb1 | xxd
```

**Always pipe extracted output to a file or program!**

### Other Data Extraction

**Extracting other data or information from storage or filesystems:**

- **Sleuthkit `jls`:** List the entries in a file system journal.
- **Sleuthkit `jcat`:** Extract data from a file system journal.
- **`isoinfo`, `isodump`:** Tools for analyzing ISO images.
- **TCT The Coroner’s Toolkit:** `findkey` utility.

Data recovery, repair, conversion, and troubleshooting programs can also be useful.

### TSK Commands

#### Partitions and Forensic File Formats
- `mmcat`, `mmls`, `mmstat`, `fsstat`, `img_cat`, `img_stat`

#### Analyzing by Blocks/Sectors
- `blkcalc`, `blkcat`, `blkls`, `blkstat`

#### Analyzing by Inodes
- `icat`, `ifind`, `ils`, `istat`, `tsk_recover`

#### Analyzing by Filename
- `fcat`, `ffind`, `fls`, `fiwalk`

#### Journaling Filesystems
- `jcat`, `jls`, `usnjls`

#### Timelines
- `mactime`, `tsk_gettimes`

#### Search and Sort
- `jpeg_extract`, `sigfind`, `sorter`, `srch`, `strings`, `tsk_comparedir`, `hfind`, `tsk_loaddb`

**Note:** All commands have man pages or provide help with the `-h` option.

---
links: [[703 DF TOC - Analysis & Carving|DF TOC - Analysis & Carving]] - [[themes/000 Index|Index]]