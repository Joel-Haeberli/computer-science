tags: #forensics #tools 

# Forensic Tools

links: [[707 DF TOC - Labs & Tools|DF TOC - Labs & Tools]] - [[themes/000 Index|Index]]

---
## Default tools that can be used for forensics:

- **ls**: Lists directory contents. Useful for quickly viewing files and directories.
- **cat**: Concatenates and displays file content. Can be used to read files.
- **grep**: Searches through text using patterns. Ideal for finding specific data within files.
- **find**: Searches for files and directories. Useful for locating specific files based on various criteria.
- **dd**: Converts and copies files. Commonly used for creating disk images.
- **hexdump**: Displays file content in hexadecimal format. Useful for examining file headers and raw data.
- **stat**: Displays file or filesystem status. Provides metadata like access time, modification time, and size.
- **strings**: Extracts printable strings from files. Can reveal hidden information in binaries.
- **file**: Determines file type. Helps in identifying unknown files.
- **mount**: Attaches file systems to directories. Used for mounting disk images or partitions.
- **umount**: Detaches file systems. Ensures that changes to mounted filesystems are properly saved.
- **ps**: Reports a snapshot of current processes. Useful for identifying running processes and their details.
- **netstat**: Displays network connections, routing tables, and interface statistics. Helps in network forensics.
- **dmesg**: Displays kernel ring buffer messages, useful for diagnosing hardware and system issues.
* **journalctl**: A command to query and display messages from the journal, which logs systemd messages and events.
## Forensic tools

* **disktype**: A command-line utility that provides detailed information about disk images and partitions.
* **dc3dd**: A forensic disk imaging tool similar to `dd` but with additional features such as data verification and logging.
* **dcfldd**: An enhanced version of `dd` developed by the U.S. Department of Defense Computer Forensics Lab (DCFL). It includes features like progress indicators and multiple output files.
* **sfsimage**: A forensic imaging tool that captures images of filesystems.
* **ewfacquire**: Part of the [[[[Forensic Acquisition#Popular Forensic Formats|EWF]] (Expert Witness Format) toolkit, used for acquiring disk images in the EWF format.
* **ftkimager**: A data imaging utility that allows the creation of forensic images of local hard drives, CDs, DVDs, and USB devices.
* **guymager**: An open-source forensic imager for media acquisition. It provides a graphical user interface and supports various image formats.
* **foremost**: A file [[carving]] tool that recovers files based on their headers, footers, and internal data structures.
* **bulk_extractor**: A tool that scans disk images, files, or directories to extract useful information such as email addresses, URLs, and other artifacts.
* **lshw**: Lists detailed information about the hardware configuration of the system.
* **lspci**: Displays information about PCI buses and the devices connected to them.
* **lsusb**: Lists USB devices connected to the system and provides detailed information about each device.
* **lsblk**: Lists information about all available block devices, such as hard drives and their partitions.
* **hdparm**: A command-line utility for displaying and setting hardware parameters of hard disk drives.
* **smartctl**: Part of the Smartmontools package, it is used to monitor and control storage devices using the Self-Monitoring, Analysis, and Reporting Technology (SMART) system built into most modern drives.

### Sleuth Kit

**Autopsy**: A graphical interface to The Sleuth Kit. Helps in analyzing disk images, file systems, and digital artifacts.

**Partitions and Forensic File Formats:**

- **mmcat**: Concatenates partitions.
- **mmls**: Lists partition layout.
- **mmstat**: Displays partition statistics.
- **fsstat**: Displays file system details.
- **img_cat**: Concatenates disk images.
- **img_stat**: Displays disk image details.

**Analyzing by Blocks/Sectors:**

- **blkcalc**: Maps blocks back to their original locations.
- **blkcat**: Displays block contents (similar to `dd`).
- **blkls**: Lists blocks (allocated, unallocated, slack).
- **blkstat**: Displays block details.

**Analyzing by Inodes:**

- **icat**: Extracts file contents by inode number.
- **ifind**: Finds the inode corresponding to a block or filename.
- **ils**: Lists inode details.
- **istat**: Displays inode statistics.
- **tsk_recover**: Recovers deleted files based on inode information.

**Analyzing by Filename:**

- **fcat**: Extracts file contents by filename.
- **ffind**: Finds filename based on inode.
- **fls**: Lists file and directory names.
- **fiwalk**: Walks through file system metadata.

**Journaling Filesystems:**

- **jcat**: Extracts data from a file system journal.
- **jls**: Lists entries in a file system journal.
- **usnjls**: Lists USN journal entries (Windows).

**Timelines:**

- **mactime**: Creates a timeline from metadata.
- **tsk_gettimes**: Extracts timeline information from files.

**Search and Sort:**

- **jpeg_extract**: Extracts JPEG images from unallocated space.
- **sigfind**: Finds file signatures.
- **sorter**: Sorts files based on their metadata.
- **srch**: Searches for a string within files.
- **strings**: Extracts printable strings from files.
- **tsk_comparedir**: Compares directory contents.
- **hfind**: Looks up hash values in a hash database.
- **tsk_loaddb**: Loads TSK data into a database.

**Other Data Extraction:**

- **jls**: Lists entries in a file system journal.
- **jcat**: Extracts data from a file system journal.
- **isoinfo**: Provides information about ISO images.
- **isodump**: Dumps data from ISO images.
- **findkey**: Finds keys in a disk image (part of TCT).

---
links: [[707 DF TOC - Labs & Tools|DF TOC - Labs & Tools]] - [[themes/000 Index|Index]]