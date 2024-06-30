tags: #debugging #asm

# Assembler 101

links: [[904 ED TOC - Assembler|ED TOC - Assembler]] - [[themes/000 Index|Index]]

---

## Intel vs. AT&T Assembly Syntax

Examples: (First line is Intel, second AT&T)

  ```assembly
  mov eax, ebx     ; Move the value in ebx to eax
  movl %ebx, %eax

  add eax, 5       ; Add 5 to eax
  addl $5, %eax

  mov eax, [ebx]   ; Move the value at the address in ebx to eax
  movl (%ebx), %eax

  inc eax          ; Increment eax
  incl %eax
  ```

**Summary**:

- **Operand Order**: Intel has `destination, source`; AT&T has `source, destination`.
- **Prefixes**: Intel doesn't use prefixes for registers and immediate values; AT&T uses `%` for registers and `$` for immediate values.
- **Memory Addressing**: Intel uses `[]` for memory addresses; AT&T uses `()`.
- **Instruction Names**: Intel uses simpler instruction names; AT&T adds letters to show the size (`b` for byte, `w` for word, `l` for long).

## Assembler 101

**Variable Initialization**:

```c
int number;
number += 1;
```

Translates to:

```assembly
number dw 0              ; Declare and initialize variable 'number' to 0
mov eax, number          ; Move the value of 'number' into eax
inc eax                  ; Increment the value in eax by 1
mov number, eax          ; Store the updated value back into 'number'
```

**Array on the Stack**:

```c
char test[5];
test[0] = 1;
test[3] = 9;
```

Translates to:

```assembly
sub esp, 0x10                ; Allocate 16 bytes on the stack for the array 'test'
mov byte ptr [ebp-0x5], 0x1  ; Set the first element of the array (test[0]) to 1
mov byte ptr [ebp-0x2], 0x9  ; Set the fourth element of the array (test[3]) to 9
```

**Array on the Heap**:

```c
char *test = malloc(5);
test[3] = 9;
```

Translates to:

```assembly
sub esp, 0x28            ; Allocate 40 bytes on the stack for function call
mov dword ptr [esp], 0x5 ; Push 5 as the argument for malloc (size of the array)
call malloc              ; Call malloc to allocate 5 bytes on the heap
mov [ebp-0xc], eax       ; Store the address returned in the local variable 'test'
mov eax, [ebp-0xc]       ; Move the address of the allocated memory to eax
add eax, 0x3             ; Move the pointer to the fourth byte in the allocated memory
mov byte ptr [eax], 0x9  ; Set the fourth element of the array to 9
```

**Conditional Statement**:

```c
if (number < 0) {
  <smallerzero>
}
<restofcode>
```

Translates to:

```assembly
mov eax, number          ; Move the value of 'number' into eax
cmp eax, 0               ; Compare the value of eax with 0
jge label                ; Jump to 'label' if eax is greater than or equal to 0
<smallerzero>            ; Code to execute if 'number' is less than 0
label:
<restofcode>             ; Code to execute regardless of the condition
```

**Loop**:

```c
int n;
for(n=0; n<12; n++) {
  printf("A");
}
```

Translates to:

```assembly
sub esp, 0x28                 ; Allocate 40 bytes on the stack for the loop
mov dword ptr [ebp-0xc], 0x0  ; Initialize the loop counter (n) to 0
jmp short loop_cond           ; Jump to the loop condition check
loop_start:
mov dword ptr [esp], 0x41     ; Move the ASCII value of 'A' (0x41) onto the stack
call putchar                  ; Call putchar to print 'A'
add dword ptr [ebp-0xc], 0x1  ; Increment the loop counter (n)
loop_cond:
cmp dword ptr [ebp-0xc], 0xb  ; Compare the loop counter with 11
jle short loop_start          ; Jump to 'loop_start' if counter is less than or equal to 11
```

## Online Assemblers

- **Compile Assembly Online**:
	- [JDoodle NASM](https://www.jdoodle.com/compile-assembler-nasm-online)
	- [TutorialsPoint NASM](https://www.tutorialspoint.com/compile_assembly_online.php)

- **Decompile C Source Code**:
	- [Godbolt](https://godbolt.org/)
	- [RetDec](https://retdec.com/decompilation-run/)

## Compiling options

- **Disable optimization**: `-O0` , tells the compiler to disable all optimization, resulting in a straightforward translation of the source code to machine code, which is useful for debugging.
- **Disable Frame pointer**: `-fno-omit-frame-pointer`, instructs the compiler to generate code that preserves the frame pointer in each function, which is useful for debugging and profiling by maintaining reliable stack traces.
- **32 bit architecture**: `-m32` for 32 bit binary
- **Disable DEP**: `-z execstack`, make stack executable again
- **Disable PIE**: `-no-pie -fno-pie`, ensuring that the output binary is not position-independent and can be loaded at a fixed address
- **Other arguments used in examples**
	- `-ggdb`: instructs the compiler to generate debugging information in the native format (DWARF) for use with GDB, including GDB-specific extensions for enhanced debugging capabilities.
	- `-lcrypt`: tells the linker to link the program with the crypt library

---
links: [[904 ED TOC - Assembler|ED TOC - Assembler]] - [[themes/000 Index|Index]]
