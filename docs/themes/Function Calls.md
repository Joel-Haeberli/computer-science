tags: #exploit #C #function
 
# Function Calls

links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]

---

## Relevant Registers

**EBP (Base Pointer)**
Stores the start of the current stack frame. The current stack frame is just the stack that is used by the current method and the start needs to be stored somewhere.

**EIP (Instruction Pointer)**
Points to the next instruction to be executed

**ESP (Stack Pointer**
Points to the bottom of the stack

## Function call step by step

![[Pasted image 20240626125227.png]]

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

---

links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]