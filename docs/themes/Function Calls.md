tags: #exploit #c #function
 
# Function Calls

links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]

---

## Relevant Registers

**EBP (Base Pointer)**

Stores the start of the current stack frame. The current stack frame is just the stack that is used by the current method and the start needs to be stored somewhere.

**EIP (Instruction Pointer)**

Points to the next instruction to be executed

**ESP (Stack Pointer**)

Points to the bottom of the stack

## What is a function?

- Self contained subroutine
- Re-usable
- Can be called from anywhere
- After function is finished: Jump to the calling function (callee)

## Function call step by step

![[function-call.png]]

1. Main method starts and `blubb`is pushed to the stack (function arg)
2. `foobar` is called (Assembler `call` instruction is executed)
	- CPU pushes the return address (address of `return` in `main`)
	- `jmp 0xaddress`: EIP is changed to the address of `foobar`
![[stack_1.png]]
3. Function prologue
	- `push ebp`: EBP is pushed to preserve base pointer of calling function `main`
	- `mov ebp, esp`: Update EBP so that it points to the start of the current stack frame of `foobar`
	- push other relevant registers
4. `sub esp, X`: Make space for local variables (`X` depends on the local variables and compiler)
5. local variables are pushed
![[stack_2.png]]
6. Function epilogue
	- `leave` instruction
		- `mov esp, ebp`: Move the stack pointer to the top of the stack frame
		- `pop ebp`: Restore the save base pointer of the calling function `main`
	- `ret` instruction
		- `pop eip`: Restore the save instruction pointer of the calling function `main`
		- `eip` now points to `return` in the main function again

## Function prologue and epilogue

- Every function has its own little **stack frame**
- stack frame is where local variables, function arguments etc. are
- A function should only access its own stack frame
- most of the function **prologue and epilogue** handle setting up and removing the stack frame

We use following example code in C:

```c
int add(int x, int y) {
	int sum;
	sum = x + y;
	return sum;
}

void main(void) {
	int c;
	c = add(3, 4);
}
```

`add()` function in assmembly:

```assembly
; push arguments before call (or save it in registers)
push 0x...

; call <addr>
push eip          ; save instruction pointer (SIP) to stack
jmp 0x11223344    ; jump to add() function address

; prologue
push ebp          ; save base pointer (SBP) to stack for callee
mov ebp, esp      ; base pointer is now set to stack pointer ("new" stack)

; function (empty function with direct return)
nop

; epilogue
move esp, ebp     ; leave, stack pointer now base pointer again
pop ebp           ; leave, restore old stack base pointer
pop eip           ; ret, restore instruction pointer (callee)
```

**Recap**

- when a function is called: `EIP` is pushed on the stack (`SIP`) via `call`
- at the end of the function: `SIP` is recovered into `EIP` (`pop eip`)
- **arguments** are referenced with a positive number via EBP (e.g. `ebp+0x08`), they are pushed into the stack frame of the calling function (positive numbers leave the actual stack frame and go up the stack).
	- **Function arguments** in C can be either pushed onto the stack or saved in registers before calling the function, depending on the calling convention and architecture in use.
- **local variables** are referenced with negative number via EBP (e.g. `ebp-0x4`), they are pushed in the stack frame of the function
- **return values** of functions are communicated to the parent function by placing it in specific register as defined by the architecture's calling convention (`eax`/`rax` in x86/x86_64)

## Function Calls in x64

- Arguments are in registers (not on stack): `RDI`, `RSI`, `R8`, `R9`
- Different ASM commands doing the same thing: `callq` (`call`), `leaveq` (`leave`), `retq` (`ret`)

**Function Call Convention**

![[function-call-convention.png]]
**EBP Cheat Sheet**

![[ebp-cheat-sheet.png]]

---
links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]