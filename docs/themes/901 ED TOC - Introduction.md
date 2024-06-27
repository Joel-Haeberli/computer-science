tags: #information-security #general #introduction 

# ED TOC - Introduction

links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]

---

## Introduction

// ToDo technical introduction slides

## Notes for the exam

What is (mainly) relevant for the oral exam:

* How does memory corruption work?
* How does an exploit work?
* What exploit mitigations exist?
* How can these exploit mitigations be circumvented?

More theoretical, not so much the nitty gritty details

Typical question:

* Explain me how a buffer overflow exploit works
* Now we introduce ASLR. What do you need to change?

### Example questions

#### Exploiting Related

Exam relevant example questions with answers:

1. **What types of memory regions exist in processes? What are they used for? Where do they come from?**
	* Stack, heap, code. For local variables, malloc, executable code. From the ELF file.

2. **What exactly is the problem with memory corruptions?**
	* You can overwrite things in a program at runtime that you shouldn't be able to, allowing malicious actions like executing code. The integrity of the program and the computer it runs on is no longer ensured.

3. **Why do memory corruptions occur in the first place?**
	* C does not enforce memory boundaries for arrays.

4. **What is needed for a functional exploit?**
	* Shellcode, address of the shellcode (in the attacked process), location of the SIP.

5. **How does an exploit actually work?**
	* SIP is overwritten via memory corruption, then the uploaded assembly code (shellcode) is executed.

6. **Why is the instruction pointer (RIP) on the stack (SIP)?**
	* So the function knows where to continue after it finishes.

7. **Can you roughly draw a graphic of the stack for the following function?**
   ```c
   int add(int a, int b) {
       int result = a + b;
       return result;
   }
   ```

   | Address     | Content                   | Description                             |
   | ----------- | ------------------------- | --------------------------------------- |
   | 0x7FFF FFF0 | Return Address            | Address to return after function call   |
   | 0x7FFF FFEC | Saved Frame Pointer (SFP) | Previous frame pointer (if any)         |
   | 0x7FFF FFE8 | Local Variable: `result`  | Storage for the local variable `result` |
   | 0x7FFF FFE4 | Parameter: `b`            | Second argument `b`                     |
   | 0x7FFF FFE0 | Parameter: `a`            | First argument `a`                      |

8. **What programs can be attacked with an exploit?**
	* Principally any that accept attacker-supplied data and are written in C/C++.

9. **What is shellcode?**
	* Self-contained, executable assembly code used for attacking other programs, often starts a shell (bash).

10. **Can you convert the number 31337 to hex and store it as little endian?**
   ```
   31337 / 16 = 1958 remainder 9  (9 in hex is 9)
   1958 / 16 = 122 remainder 6   (6 in hex is 6)
   122 / 16 = 7 remainder 10    (10 in hex is A)
   7 / 16 = 0 remainder 7      (7 in hex is 7)

   --> 0x7A69 and in little endian --> 0x697A
   ```

NOT (necessarily) exam relevant example questions:

1. **In which register is the address of the string stored during the write system call?**
	* **RDI** (on x64 systems).

2. **Which GDB command is used to find the address of a buffer?**
	* `p &buffer` or `info address buffer`.

3. **What options does GDB have?**
	* Breakpoints, watchpoints, stepping, variable inspection, disassembly, memory examination.

4. **Can you modify the following assembly code so that it does not contain any 0 bytes?**
	* When asked to modify assembly code to avoid 0 bytes, the task is to rewrite the code so that the resulting machine code does not contain any null bytes. This is often done by breaking down instructions, changing immediate values, or using alternate instructions that achieve the same result without producing null bytes.

5. **Name 5 differences between x32 and x64.**
	* Register size, memory addressing, number of registers, calling conventions, instruction set extensions.

6. **Explain step-by-step how a function call works in x64 (specifically the function prologue and epilogue, with EBP, SFP, etc.).**
	* Prologue: Save old base pointer, set new base pointer, allocate space for local variables.
	* Epilogue: Deallocate local variables, restore old base pointer, return to caller.

7. **Explain what components a computer has.**
	* CPU, memory (RAM), storage (HDD/SSD), motherboard, power supply, I/O devices.

8. **Explain how the CPU works.**
	* Fetch, decode, execute, and writeback instructions using control unit, ALU, registers, and cache.

9. **What registers exist? What are they used for?**
	* General-purpose registers (e.g., EAX, EBX), special-purpose registers (e.g., EIP/RIP, ESP/RSP), used for data storage, addressing, and control flow.

10. **What are the sections in an ELF file for?**
 	* Code (.text), data (.data), uninitialized data (.bss), metadata (.rodata), and linking information.

#### Exploit Mitigation Related 

1. **What are the differences between a local and a remote exploit?**
	* Fundamentally, there are none. All exploit techniques work identically. However, with local exploits, you have more information (the binary and its content, the exact program version, system load, etc.). Local attacks potentially have a larger attack surface (loaded files, environment variables, parameters, etc.). Remote exploits send specially crafted packets to the server that trigger and exploit the vulnerable function. The payload is particularly different (needs connect-back shellcode, etc.).

2. **How do network servers behave in the event of a crash? Does this affect exploiting?**
	* Servers create child processes (fork()) that are copies of the parent for each client. Thus, protection mechanism properties are also copied, specifically the secret stack cookie and the offset to segments (i.e., the memory layout). A crashed child process does not affect the server. This allows for brute-force attacks (especially on the stack cookie and the ASLR entropy).

3. **What are the three most important anti-exploit mechanisms?**
	* ASLR, DEP, Stack Canary.

4. **How does ASLR work?**
	* It randomizes the memory layout so that the attacker lacks important information/offsets (address of the shellcode, addresses of functions, etc.).

5. **How does DEP work?**
	* It marks all writable areas as non-executable, preventing the attacker’s uploaded code (shellcode) from being executed.

6. **How does Stack Canary work?**
	* Before a function ends and the stored instruction pointer is fetched from the stack to continue the instruction flow in the parent function, the integrity of a memory location before the SIP is checked.

7. **How can ASLR be bypassed?**
	* Design the exploit so that it does not depend on ASLR-protected areas (exploit non-ASLR areas).
	* Use information disclosure to reconstruct the memory layout.

8. **How can DEP be bypassed?**
	* Do not upload code; instead, jump to existing functions (Ret2plt).
	* Abuse parts of existing code (ROP).

9. **How can Stack Canary be bypassed?**
	* Brute force.
	* Information disclosure.
	* Find another bug instead of a simple stack-based buffer overflow.

10. **Which part of the exploit defeats ASLR/DEP/Stack Canary?**
 	* **ASLR**: Information disclosure or exploiting non-ASLR areas.
 	* **DEP**: Using Ret2plt or ROP techniques.
 	* **Stack Canary**: Brute force or information disclosure.

#### Memory Corruption Related

1. **Why does memory corruption occur at all?**
	* Programming languages like C and C++ do not check if data is written beyond the bounds of an array. With free manipulation of pointers across the entire address space, it's possible to write data to places it shouldn't be allowed.

2. **Are there any functions in C that developers should avoid using?**
	* Generally, all string functions that do not consider the size of the target buffer (e.g., `strcpy`, etc.).

3. **What is the problem with handling strings in C?**
	* The terminating null character that indicates the end of a string can be missing or overwritten. This invalidates assumptions about the string's length.

4. **What about integer overflows?**
	* The simplest case is when an attacker-controlled value is used in a calculation for `malloc`, and the allocated memory is smaller than the number of bytes that are copied.

5. **What are the methods to identify memory corruption vulnerabilities?**
	* Examples include static analysis, fuzzing, manual code review.

6. **How does fuzzing work?**
	* The program is fed more or less random data to produce a crash.

#### ROP Related

1. **What is ROP?**
	* Return Oriented Programming; chaining together existing code parts that end with a RET instruction.

2. **How do you find ROP gadgets?**
	* Search for the RET byte in the code segment, then disassemble backward until valid (and useful) code sequences are found.

3. **How does ROP work?**
	* The overwritten return address points to the first ROP gadget. Each gadget consumes arguments from the stack via pop instructions. Upon reaching a RET in the gadget, the stack provides the address of the next gadget.

4. **What is needed for ROP?**
	* Gadgets and their addresses. For this, the code segment in the target process must not be ASLR-protected (no PIE) or there must be a non-ASLR library on Windows. Alternatively, an information disclosure can be used to obtain these addresses.

5. **How can ROP be prevented?**
	* Ensure no static segments exist. On Linux, compile the program with PIE (libraries are automatically randomized). On Windows, avoid loading non-ASLR DLLs.

6. **How is a ROP-based exploit generally constructed?**
	* The ROP chain is executed first. This contains functionality to execute further code, acting as a stager. For example, it can make the stack executable or resolve libc functions like `system()`.

#### Heap Overflows Related

1. **What is the heap for?**
	* `malloc()` allocations / dynamic, global data structures.

2. **How does the heap work?**
	* `malloc()` allocates some memory pages. Each page is divided into equal-sized pieces (chunks). When `malloc()` is called, a free chunk is returned.

3. **What is a chunk?**
	* A heap element that contains a user-writable area plus heap metadata.

4. **Can you perform heap buffer overflows?**
	* Yes. As with the stack, the heap contains meta/control information. Through clever manipulation of heap metadata and allocation/deallocation of chunks, it may be possible to write arbitrary data to arbitrary locations in memory.

5. **What is a use-after-free attack?**
	* A memory area is used by two different places in the code simultaneously (two pointers to the same memory area). This allows arbitrary manipulation of objects in that memory.

6. **How is a UAF vulnerability often exploited?**
	* A memory area is mistakenly freed. A new object is then created that occupies the freed memory. By manipulating the original pointer, you can change vtable entries (which are simply pointers to functions). For example, you can point them to a ROP gadget, which can then perform a stack flip.

#### Windows Related

1. **Do exploits fundamentally work differently on Windows?**
	* No.

2. **Are there differences between Windows and Linux regarding exploiting?**
	* Windows has structured exception handlers (SEH) on the stack, which were exploitable for a long time.

3. **Are there differences between Windows and Linux regarding exploit mitigations?**
	* Over time, Windows has implemented all the exploit mitigation techniques that Linux currently has. Additionally, Control Flow Integrity (CFI) is more consistently applied.

#### Further questions

1. **Are there ways to completely eliminate memory corruptions?**
	* No, completely eliminating memory corruption is very difficult due to the complexity of modern software and legacy code. Using safer programming languages and rigorous code reviews can reduce but not eliminate them.

2. **Are the current anti-exploit mechanisms adequate?**
	* They are effective to a degree but not foolproof. Advanced exploits can still bypass these mechanisms.

3. **Do you have ideas for improving anti-exploit mechanisms?**
	* Combining multiple layers of defense, improving compiler-based protections, and adopting newer memory-safe programming languages can enhance existing mechanisms.

4. **How do technologies like virtual machines, containers, and sandboxing compare to anti-exploit mechanisms? What are the pros and cons?**
	* **Virtual Machines**: Provide strong isolation but with higher overhead. 
		* **Pros**: Strong isolation, complete environment separation.
		* **Cons**: High resource overhead, slower performance.
	* **Containers**: Offer a lighter form of isolation.
		* **Pros**: Lightweight, less overhead compared to VMs.
		* **Cons**: Weaker isolation than VMs, shared kernel vulnerabilities.
	* **Sandboxing**: Restricts the environment in which code executes.
		* **Pros**: Limits the impact of exploits, fast and efficient
		* **Cons**: May not be comprehensive, possible escape vulnerabilities.

5. **Why is a browser particularly vulnerable to memory corruption attacks?**
	* Browsers handle untrusted input from many sources (web pages, plugins), have complex codebases, and require high performance, making them a prime target for memory corruption attacks.

---
links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]