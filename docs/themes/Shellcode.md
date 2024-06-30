tags: #exploiting #shellcode
 
# Shellcode

links: [[905 ED TOC - Shellcode|ED TOC - Shellcode]] - [[themes/000 Index|Index]]

---

# Overview

Shellcode is:

- The code we want to upload to the remote system
- Our **evil code**
- A set of instructions injected and executed by exploited software
- Arbitrary Code Execution
- Also called **payload**
- "A string of bytes" which can be executed

**What we can do with it**

- Execute a shell (bash)
- Add admin user
- Download and execute more code
- Connect back to attacker

**How it works**

- Assembler instructions
- **Native code** which performs a certain action (like starting a shell)
- Example how to create shellcode from `objdump`: [[Debugging#objdump|Debugging]] (or use the [pwntool](https://docs.pwntools.com/en/stable/) python library)

**Properties**

- Should be **small**: maybe we have only a small buffer
- Position **Independent**: don't know where it will be loaded
- **No Null Characters** (`0x00`): strcpy will stop copying after Null bytes
- **Self-Contained:** don't reference anything outside of shellcode

![[shellcode-example.png]]
## Terms

- see [[Syscalls]] first
- **Compile/Assembler**: process of converting source code into a series of instructions/bytes (Assembler $\rightarrow$ Bytes)
- **Disassemble**: process of converting a series of instructions/bytes into the equivalent assembler source code (Bytes $\rightarrow$ Assembler)
- **Decompile**: process of converting instructions/assembler into the original source code (Assembler $\rightarrow$ C/C++)

## Example

- After compiling, the the string is in the `.data` section (Heap) and will be referenced in the assembly instruction.

![[shellcode-formed.png]]

## Fix Null Bytes Problem

- The Null byte (`0x00`) is a string delimiter $\rightarrow$ `strcpy()` etc. will stop copying
- **Fix**: replace instructions with contain `0x00` bytes with equivalent instructions which do not have these (more an art than a technique)

```assembly
; has 0 bytes
mov 0x04, eax            ; bb 01 00 00 00

; equivalent instruction without 0 bytes
xor eax, eax             ; 31 c0
mov 0x04, al             ; b0 04
```

![[null-byte.png]]

## Fix Stack Reference

- We cannot reference a string from the data section, we only execute code
- **Fix**: Remove dependency on the data section by storing the same data directly in the code and **move it to the stack**.

The following example has moved the reference from the `.data` section to the stack by pushing the string "Hi there" in its binary representation (and in little endian) to the stack and copy the address of the ESP to the register `ecx`:

![[shellcode-with-stack.png]]

## Types of shells

Types of shell's provided by shellcode:

- **Local shell**: privilege escalation, gain root access
- **Bind shell**: opens a network port on the target machine and binds a shell to it, allowing an attacker to connect to this port remotely
- **Reverse shell**: causes the target machine to initiate a connection back to the attacker’s machine, providing the attacker with a remote shell on the target machine through this connection
- **Find shell**: This shellcode searches the system’s memory for a shell or command execution function to hijack or reuse, providing the attacker with a shell on the target machine without spawning a new process.

Types of shellcode:

- **Self contained (all in one)**
- **Staged**: minimal initial shellcode (Stager), Stager loads stage 1, stage 1 loads stage 2

## Metasploit

Metasploit is an open source penetration testing framework that provides tools and resources for discovering, exploiting, and validating vulnerabilities in computer systems and networks. It already includes shellcode (payloads) for most exploits, so you don't have to write them yourself. You can also write your own shellcode by using Metasploit to generate it for you.

- Metasploit can generate shellcode
- Pretty much any form of shellcode
- With many useful payloads

```bash
$ msfconsole
msf > use payload/linux/x64/[TAB]
use payload/linux/x64/exec
use payload/linux/x64/shell/bind_tcp
...

# let metasploit create an exec() shellcode
msf > use payload/linux/x64/exec
msf payload(exec) > set cmd = "/bin/bash"
cmd => = /bin/bash
msf payload(exec) > generate
"\x48\xb8\x2f\x62\x69\x6e\x2f\x73\x68\x00\x99\x50\x54\x5f" +
"\x52\x66\x68\x2d\x63\x54\x5e\x52\xe8\x0b\x00\x00\x00\x3d" +
"\x2f\x62\x69\x6e\x2f\x62\x61\x73\x68\x00\x56\x57\x54\x5e" +
"\хба\x3b\x58\x0f\x05"

# without null bytes
msf payload(exec) > generate -b '\x00\x0A'
"\xeb\x27\x5b\x53\x5f\xb0\xe0\xFc\xae\x75\xfd\x57\x59\x53" +
"\x5e\x8a\x06\x30\x07\x48\xff\xc7\x48\xff\xc6\x66\x81\x3f" +
"\x26\x42\x74\x07\x80\x3e\xe0\x75\xea\xeb\xe6\xff\xe1\xe8" +
"\xd4\xfF\xfF\xff\x02\xe0\x4a\xba\x2d\x60\x6b\x6c\x2d\x71" +
"\хба\х02\x9b\x52\х56\х5d\x50\х64\хба\x2f\x61\x56\x5c\x50" +
"\xea\x09\x02\x02\x02\x3F\x2d\x60\x6b\x6c\x2d\x60\x63\x71" +
"\хба\х02\x54\x55\x56\x5c\x68\x39\x5a\x0d\x07\x26\x42"
```

## Detect Shellcode

- Find NOP's (lots of 0x90)
- Find stager
- Find stage1 / stage2
- **NIDS**: Network based Intrusion Detection System
- **HIDS**: Host based Intrusion Detection System

---
links: [[905 ED TOC - Shellcode|ED TOC - Shellcode]] - [[themes/000 Index|Index]]