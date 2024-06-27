tags: #DF #acquisition

# Forensic Acquisition Tools

links: [[702 DF TOC - Storage & Acquisition|DF TOC - Storage & Acquisition]] and [[707 DF TOC - Labs & Tools|DF TOC - Labs & Tools]] - [[themes/000 Index|Index]]

---
## [[Forensic Acquisition#Write Blocker|Write Blocker]]

- **Portable Kits**: Compact and portable solutions for field use, allowing investigators to use them on-site.
- **Drive Bay**: Write blockers integrated into drive bays for desktop or lab environments.
- **Duplicator Appliances**: Devices that can duplicate drives while ensuring no data is written to the source drive.
- **Multiple Interface Compatibility**: Write blockers that support various interfaces (e.g., SATA, USB, FireWire) to accommodate different types of storage devices.

## Confirm Attached Evidence Drive

**Double-checking source and destination devices** is critical in forensic investigations to ensure the integrity and accuracy of data acquisition.

**Commands to Identify Attached Drives**

- **`lshw -class disk`**: Lists hardware information about disks.
- **`lspci`**: Displays information about PCI devices, including storage controllers.
- **`lsusb`**: Shows USB devices connected to the system.
- **`lsscsi`**: Lists SCSI devices and hosts.
- **`lsblk`**: Provides a list of all available block devices.
- **`dmesg`**: Displays kernel messages, useful for identifying newly attached hardware.

**Gathering Disk Information**

- **Photograph of Drive**: Take a physical photograph for visual reference and documentation.
- [**S.M.A.R.T Data**](https://en.wikipedia.org/wiki/Self-Monitoring,_Analysis_and_Reporting_Technology) (Self-Monitoring, Analysis, and Reporting Technology): Retrieve health and status data of the drive.
- **`hdparm -I /dev/sda`**: Displays detailed information about the drive.
- **`smartctl -x /dev/sda`**: Provides extensive diagnostics and health information for the drive.

Always double-check the source and destination devices to avoid data corruption or loss. This step ensures that you are working with the correct hardware throughout the forensic process.

## dd

**History**

- **Origin**: The `dd` command originates from the IBM DD command, which stands for "Data Definition."
- **Unix**: Introduced in the 1970s in Unix systems primarily for data conversion tasks.

**Function**

- **Block Copying**: `dd` copies data blocks from an input source to an output destination.
- **Sector Copying**: Used for copying disk sectors, not just individual files. This is crucial for creating exact disk images in forensics.

**Usage**

- **Basic Syntax**: `dd if=myinputfile of=myoutputfile`
- **For Copying Disk Sectors**: `dd if=/dev/sda of=myoutputfile`
- **With Error Handling**: `dd if=/dev/sda of=myoutputfile conv=noerror,sync`
- `conv=noerror` continues operation even if errors are encountered.
- `sync` pads each input block to the full length of the block, ensuring synchronized data.

**Dangerous and Deadly**

`dd` is powerful but must be used with caution. Incorrect usage can lead to data loss or overwriting important data. Always double-check command parameters before execution.

**Variations of dd**

Forensic variations of `dd` have been developed to include additional features such as cryptographic hashing, improved error handling, activity logging, performance optimization, hash verification, and live progress monitoring.

**Forensic Acquisition Tools Based on `dd`**

- **dcfldd**: Enhanced version of `dd` with additional forensic features.
- **dc3dd**: Another improved version used in digital forensics.
- **Data Rescue/Recovery Tools**: Tools like `ddrescue` and `dd_rescue` for recovering data from damaged drives.
- **sfsimage Script**: Used for creating [[Forensic Acquisition#Squashfs Compressed File System|Squashfs]] container files for efficient storage and analysis.

**Additional Notes**

- **Raw Data Output**: The output from these tools is raw data, not formatted in a specific file system or structure.
- **Padding for Bad Sectors**: Bad sectors encountered during copying are padded to maintain data alignment and integrity.

## Other Free and/or Open-Source Tools

**Commercial Forensic Acquisition Tools/Formats**

- **[[Forensic Acquisition#Popular Forensic Formats|ewfacuire]]**: A tool for creating EnCase Evidence File (EWF) format forensic images.
- **ftkimager**: A utility for creating forensic images and verifying data integrity.

**Tools for Partitions and Filesystem Identification**

- **disktype**: Quick check of partition and filesystem types.
- **testdisk**: Recovers deleted partitions.
- **gpart**: Searches for filesystems on a disk.

**Tip**: GPT partitions save a backup copy at the end of the drive.

## Acquisition Cheat Sheet

**Identify Attached Drive and Hardware Details**

- Use commands like `dmesg`, `journalctl`, `lshw`, `lspci`, `lsusb`, `hdparm`, and `smartctl`.

**Acquire a Forensic Image**

- Tools: `sfsimage`, `dc3dd`, `ewfacquire`, `ftkimager`, `guymager`.

**Verify Hash**

- Use `md5sum`, `sha*sum`, or built-in hash verification in acquisition tools.

**Identify Disk Layout and Partition Tables**

- Tools: `img_stat`, `mmstat`, `mmls`, `disktype`, `gpart`, `testdisk`.

**Identify Filesystem Type and Details**

- Tools: `fsstat`, `disktype`.

---
links: [[702 DF TOC - Storage & Acquisition|DF TOC - Storage & Acquisition]] and [[707 DF TOC - Labs & Tools|DF TOC - Labs & Tools]] - [[themes/000 Index|Index]]