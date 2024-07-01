tags: #DF #carving
 
# Carving

links: [[703 DF TOC - Analysis & Carving|DF TOC - Analysis & Carving]] - [[themes/000 Index|Index]]

---

## Concept

Carving tools are used as a **last-resort**, best-effort method to extract files from unstructured data blobs. They search for file headers and footers, and sometimes look for file structures or patterns. Some tools also look for partial filesystem structures. The term "carving" comes from the English word "carve," similar to carving wood.

## Tools

> Exam question: Which tools can be used for carving

There are some dedicated forensic carving tools. The most popular are:

- **Scalpel** (Today part of Sleuthkit) [https://github.com/sleuthkit/scalpel](https://github.com/sleuthkit/scalpel)
- **foremost** and several forks of it on github: extract files from disk/unstructured data

Data recovery tools are also good for carving the most popular is **photorec** ([https://www.cgsecurity.org/wiki/PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec)):

- Supports over 400 file formats
- Tries to use filesystem structure if possible
- Does additional checks and validation

There are also network traffic carver like **tcpxtract**: extract files from PCAP (only unencrypted)

## Pros and Cons

**Pros**

- Unsupported filesystems (e.g., btrfs)
- Partially wiped disks
- Corrupted filesystems
- Unknown blobs of data
- Files inside other files
- Page/swap data, memory dumps
- Extracted slack space
- Extracted unallocated blocks

**Cons**

- False positives
- File fragments, corrupt/damaged files
- Lots of manual processing
- Original file names missing

**lost + found**: if `fsck` finds a file (finds it without name)

## Carving for strings

**Tool: Bulk Extractor**

**Function**: Scans files, images, or data blobs to extract interesting information.

**Extracts**:

- Credit card numbers and track 2 info
- Domain names
- Email addresses
- IP addresses
- Ethernet MAC addresses
- URLs
- Telephone numbers
- EXIF data from media files (pictures and videos)
- Custom specified regex strings

**More Info**: [Bulk Extractor on Forensics Wiki](https://forensics.wiki/bulk_extractor/)

**Sleuthkit Tool: srch_strings**

- **Function**: Basic string searching tool.

## Carving for files

### Special File Carving

**Executables**

- **Tool: PE_Carver**
	- **Function**: Carves executable files from data blobs.
	- **More Info**: [PE_Carver on GitHub](https://github.com/Rurik/PE_Carver)

**TrueCrypt Containers**

- **Tool**: Truecrypt-file-carve
	- **Function**: Extracts TrueCrypt containers from unstructured data.
	- **More Info**: [Truecrypt-file-carve on GitHub](https://github.com/gdbelvin/truecrypt-file-carve)

**Crypto Keys**

- **Tools**:
	- **aeskeyfind**: Searches for AES keys in memory dumps.
	- **rsakeyfind**: Searches for RSA keys in memory dumps.
	- **TCT findkey**: An older tool for finding keys (availability limited).

---
links: [[703 DF TOC - Analysis & Carving|DF TOC - Analysis & Carving]] - [[themes/000 Index|Index]]