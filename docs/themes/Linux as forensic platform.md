tags: #DF #linux
 
# Linux as forensic platform

links: [[701 DF TOC - Forensics Basics & History|DF TOC - Forensics Basics & History]] - [[themes/000 Index|Index]]

---

This chapter is mostly about common Linux stuff. I put all the forensic-related information that I think may be useful at the beginning, the rest is just a little Linux cheat sheet.

## Forensics and FOSS

> Exam question: What are advantages and disadvantages of FOSS forensic tools

There are advantages and disadvantages when using (Free) and Open Source Software (FOSS) in the forensic field:

**Advantages:**

- Free of charge
- Transparency
- Can be modified and fixed
- Scripting/automation
- Community support can be great

**Disadvantages:**

- Community support can be horrible
- Weak compatibility with proprietary formats
- Sometimes difficult to use (no fancy GUI)
- Can have poor documentation or no documentation at all (source code = documentation)
- Project might be abandoned
- No guarantee

## Somewhat forensic relevant

### Hardware

**Commands to list hardware:**

- `lsusb`
- `lspci`
- `lshw` (`lshw -businfo`)
- `lsblk`

**Devices can be found in /dev**

- SATA and SCSI are `/dev/sda`, `/dev/sdb`, `/dev/sdc`, ... 
- NVME is `/dev/nvme0n1`, `/dev/nvme1n1`, ...  
- MMC cards are `/dev/mmcblk0`, `/dev/mmcblk1`, ...
- Tapes are `/dev/st0`, `/dev/nst0`, `/dev/st1`

**Partitions are added to the raw device name**

- `/dev/sda1`
- `/dev/nvme0n1p1`

### Tools

> Exam question: Which tools can be used?

There are a vide variety of tools that can be used to perform forensics:

- forensic acquisition/analysis developed tools
- troubleshooting and diagnostic tools
- hacking and pentest tools
- tools for repairing corrupt files
- tools for extracting or converting dat
- tools for debugging and tracing code
- tools for disassembly and decompiling code
- tools for searching (grep)

**Most known tools:**

The SleuthKit (TSK):

- Set of command line tools and libraries
- Focus on partitions and filesystems

Autopsy:

- GUI tool (similar to some commercial tools)
- Analyzing disks, OS, applications, mobiles
- timelines, search, artifacts, carving, media files
- frontend for many other FOSS tools like RegRipper etc.

## Basic shell commands (mentioned in the slides)

- `man`, `apropos`  `ls`, `file`, (dot hidden files) 
- `mkdir`, `cd`, `pwd`, `rmdir` 
- `cat`, `less` (`more`)
- `touch`, `mv`, `rm`
- `clear`, `reset`  
- `w`, `whoami`  
- `ps`, `kill`  
- `date`, `cal`, `dict`  
- `find`, `locate`  
- `alias`
- `exit` (`control-D`)

## Pipes and redirection

**Standard file descriptors:**

- stdin - input (0), data into a program
- stdout - output (1), data from a program
- stderr - error (2), error/debug data from a program

These are the inputs and outputs needed to connect programs and files together.

- `>` send data from a program to a file (create file if needed) 
- `>>` append data from a program to a file (create if needed)
- `<` send data from a file to a program  
- `|` send data from a program to a program

Examples:

- `program file`
- `program < file`
- `program > file`
- `program >> file`
- `program1 | program2`
- `program1 | program2 | program3`
- `program1 < file1 | program2 | program3 > file2`

Special program called `tee` sends to multiple files and stdout: `program | tee file1 file2 file3`

---
links: [[701 DF TOC - Forensics Basics & History|DF TOC - Forensics Basics & History]] - [[themes/000 Index|Index]]