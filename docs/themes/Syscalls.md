tags: #exploiting #syscalls #shellcode 
 
# Syscalls

links: [[905 ED TOC - Shellcode|ED TOC - Shellcode]] - [[themes/000 Index|Index]]

---

# Overview

## Syscalls

- Ask the kernel to do something for us
- The fundamental interface between an application and the Linux kernel
- Generally not invoked directly, but rather via wrapper function in glibc

## Using Syscalls in Shellcode

- Direct interface to the kernel
- makes it easy to create shellcode
- Alternative would be to call LIBC code (e.g. `write()`) but we don't know where `write()` is located

## Syscall in ASM

`int 0x80` executes the syscall and takes arguments in register `eax`, `ebx`, `ecx`, `edx`.

Example of `write()` syscall:

```assembly
mov eax, 4    ; write() syscall number
mov ebx, 1    ; int fd (stdout)
mov ecx, msg  ; char *msg
mov edx, 9    ; unsigned int len
int 0x80      ; invoke syscall
```

Arguments:

- `eax`: syscall nr (write() = 0x04)
- `ebx`: FD (file descriptor, stdout = 0x01) 
- `ecx`: address of string to write
- `edx`: Length of string

## Syscall in C

Example with glibc function `write()`:

```c
# function definition
write(int fd, char *msg, unsigned int len);

# function call
write (1, &msg, strlen(msg));

# similar to
printf("Hi there");
```

## 32bit vs 64bit

- Instruction
	- 32bit: `int 80`
	- 64bit: `syscall`
- Syscall number
	- 32bit: `eax` (e.g. execve = 0xb)
	- 64bit: `rax` (e.g. execve = 0x3b)
- Arguments
	- 32bit: up to 6 inputs: `ebx`, `ecx`, `edx`, `esi`, `edi`, `ebp`, over 6 inputs in RAM (`ebx` points to them)
	- 64bit: `rdi`, `rsi`, `rdx`, `r10`, `r8`, `r9`, over 6 inputs forbidden

---
links: [[905 ED TOC - Shellcode|ED TOC - Shellcode]] - [[themes/000 Index|Index]]