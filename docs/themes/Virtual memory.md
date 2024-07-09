tags: #malware-analysis
 
# Virtual memory

links: [[802 MAI TOC - Windows & OS background|MAI TOC - Windows & OS background]] - [[themes/000 Index|Index]]

---

## Overview

- **Virtual Memory Allocation**: Each process uses the same linear virtual addresses and receives a standard amount of virtual memory, independent of the physical memory size. For example, Windows 32-bit provides 2GB, and Windows 64-bit provides approximately 8TB of virtual memory per process.
- **Pages and Frames**: Virtual memory is divided into chunks called pages (e.g., 4 KB on Windows 32-bit), which are mapped to physical memory (RAM) frames by the OS and the CPU’s Memory Management Unit (MMU).

## Components of Virtual Memory

**Contents of User Space** (high level):

- **Main Module**: The primary executable file, such as `chrome.exe` for Chrome, mapped into memory.
- **DLLs**: Imported DLLs, such as `user32.dll`, mapped into memory.
- **Stacks**: Each thread has its stack for local variables and argument passing.
- **Heaps**: Used for dynamically allocated data.

![[virtmem_highlevel_userspace.png]]

**Contents of User Space (showed by vmmap)**

  - **Image**: Executable files loaded into a process by the image loader.
  - **Mapped File**: Files on disk shared across processes.
  - **Shareable Memory**: Memory that can be shared with other processes.
  - **Heap**: Managed by the user-mode heap manager for dynamic allocations.
  - **Managed Heap**: Managed by the .NET runtime.
  - **Stack**: Allocated to each thread for function parameters and local variables.
  - **Private Data**: Allocated by `VirtualAlloc`, not shared with other processes.
  - **Free Memory**: Regions that are not allocated.
  - **Unusable Memory**: Free but unusable due to allocation granularity restrictions.

![[virtmem_vmmap.png]]

## Memory Protection Attributes

- **Protection Attributes**: Combinations of Read (R), Write (W), and Execute (X) permissions, such as `PAGE_EXECUTE_READWRITE`. Each memory allocation has specific protection attributes.

## Memory Types and States

**Memory Types**:

- **MEM_PRIVATE**: Private pages not shared with other processes.
- **MEM_IMAGE**: Pages mapped from an EXE or DLL file.
- **MEM_MAPPED**: Pages mapped from non-EXE or non-DLL files or shared memory.

**Memory States**:

- **RESERVED**: Allocated in virtual memory but not yet associated with a physical page.
- **COMMITTED**: Allocated in both virtual and physical memory.
- **FREE**: Not allocated and not addressable by a process.

## Advanced Details

Probably not that important but we include it anyway.
#### Memory Management Data Structures

**VAD Tree (Virtual Address Descriptor Tree)**

- A kernel data structure that keeps track of memory allocations in a process’s virtual address space.
- Entries are created using memory management APIs like `VirtualAlloc`.
- Tracks mapped files, memory attributes, protection attributes, and private memory.

![[VAD_tree_structure.png]]

**PEB (Process Environment Block)**

- Contains information on loaded DLLs and the main executable.
- Organized in three ways: by load order, memory layout, and initialization order.
- Can be modified by malware as it is found in the user mode part of virtual memory.

![[PEB_tree_structure.png]]

---
links: [[802 MAI TOC - Windows & OS background|MAI TOC - Windows & OS background]] - [[themes/000 Index|Index]]