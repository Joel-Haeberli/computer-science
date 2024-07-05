tags: #malware-analysis
 
# PE files

links: [[802 MAI TOC - Windows & OS background|MAI TOC - Windows & OS background]] - [[themes/000 Index|Index]]

---

Portable Executable (PE) files are the standard format for executables and libraries (DLLs) in Windows. This chapter includes some images there are many more that can be helpful in the slides!

## Overview

**File Formats**: Different operating systems use different file formats for executables and libraries:

- Windows: PE files
- Linux: [[Memory Layout#Linux Userspace Process Memory Layout|ELF files]]
- MacOS: Mach-O files

PE files are easy to spot in hex dumps:

![[PEfiles_spotting.png]]

## Key Elements of PE Files

![[PEFile_details.png]]

- **Headers**: Contain metadata such as architecture, compile time, load address, and entry point. Headers also include the section table, describing how sections are mapped from disk to virtual memory.
- **Sections**: Contain the actual code and data. Common sections include:
	- `.text`: Executable code
	- `.data`: Initialized data
	- `.rdata`: Read-only data

![[PEFile_sections.png]]

#### Process and DLL Loading

 **Image Loader**: When a process starts, the OS kernel creates process data structures, and the image loader initializes the virtual address space. It loads the main executable and all required DLLs.

1. Load the main image / EXE
2. Identify the DLLs used by the program (import address table, IAT), as well the DLLs used by those DLLs (IAT of DLLs)
3. Load the DLLs into memory (check if desired imports exist, by looking at export table)
4. Link the code, e.g., of the main executable such that the calls to the DLL functions work properly. Technically, this is done by populating the Import Address Table (IAT)
5. Optionally, if a DLL cannot be loaded at its preferred position, it needs to be relocated

**Dependency Chaining**: DLLs required by an executable may, in turn, require other DLLs, forming a chain of dependencies.

#### Import Address Table (IAT)

The IAT holds addresses of imported APIs, allowing the executable to locate and call these functions in memory. The image loader populates the IAT during the loading process (like PLT in Linux).

![[PEFile_IAT.png]]

#### Exported APIs

**Export Directory**: DLLs declare the APIs they export in the export directory of the PE file. This information is used by other executables or DLLs to locate and call the exported functions.

---
links: [[802 MAI TOC - Windows & OS background|MAI TOC - Windows & OS background]] - [[themes/000 Index|Index]]