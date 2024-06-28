tags: #memory

# Memory Layout

links: [[903 ED TOC - Memory Layout|ED TOC - Memory Layout]] - [[themes/000 Index|Index]]

---

## Linux Userspace Process Memory Layout

**Memory Layout**

- **x32 Memory Layout**: The memory layout in 32-bit architecture includes the stack, heap, and code sections. The stack grows downwards from the top of the memory space, while the heap grows upwards. The code section is typically located at the lower addresses.
	- **Stack**: A contiguous memory region used for function local variables and control data like the saved instruction pointer (SIP).
		- LIFO - Last in, First out
	- **Heap**: A contiguous region managed by the memory allocator (e.g., malloc()) and used for dynamic memory allocation.
	- **Code**: Contains the compiled program code.

![[memory_overview.png]]

**ELF Format**

- ELF files store program data and instructions in a standardized format. They replace the older "a.out" format and are similar to other executable formats like COFF and PE.
	- **Types**: ET_EXEC (executable), ET_REL (relocatable), ET_DYN (shared object).
	- **Views**:
		- **Sections**: Logical divisions used by the compiler, like `.text` for executable instructions, `.data` for initialized data, and `.bss` for uninitialized data.
		- **Segments**: Physical divisions used by the loader, which map to memory regions. Each segment contains one or more sections.

![[elf_format.png]]

**ELF Structure**

- **Headers**: The ELF file begins with an ELF header, followed by program headers (defining segments) and section headers.
- **Program Headers**: Define segments for the loader.
	- **Types of Segments**:
	    - **LOAD**: Describes segments to be loaded into memory, with permissions like read, write, and execute.
	    - **DYNAMIC**: Holds dynamic linking information.
	    - **GNU_STACK**: Describes stack properties.
- **Sections to Segments Mapping**: Sections like `.text`, `.data`, and `.bss` are mapped into segments like code, heap, and stack by the loader.

![[elf_mapping.png]]

**Memory Example in C**

  - Global variables are located in the data segment.
  - Heap variables are dynamically allocated and located in the heap.
  - Stack variables are local to functions and located in the stack segment.

**ELF File Analysis**

- **readelf** and **objdump** tools are used for examining ELF files, displaying segment and section information and disassembling code sections.

**Summary**

- The process of creating a process from an ELF file is called **Linking and Loading**
- **Sections** are for compiler (gcc), to link several object files together (.o)
- **Segments** are for the loader, to create the process
- Program Code is stored in ELF Files
- ELF Files contain segments
- Segments are copied 1:1 in the memory to create a process (of that program)
- A process has generally three important segments:
	- Code segment (the actual compiled code)
	- Heap (global allocations with `malloc()`)
	- Stack (local variables of functions)

---
links: [[903 ED TOC - Memory Layout|ED TOC - Memory Layout]] - [[themes/000 Index|Index]]
