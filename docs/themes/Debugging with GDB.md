tags: #debugging #gdb

# Debugging with GDB

links: [[907 ED TOC - Debugging|ED TOC - Debugging]] - [[themes/000 Index|Index]]

---

**GDB Commands Summary**

**Starting and Running GDB**

- **Start GDB**: `$ gdb <filename>`
- **Load a file**: `(gdb) file <filename>`
- **Start the program**: `(gdb) run`

**Inspecting Code**

- **Where am I?**: `(gdb) where`
- **Disassemble a function**: `(gdb) disas <function>`
	- Example: `(gdb) disas main`

**Setting and Managing Breakpoints**

- **Set a breakpoint**: `(gdb) break *<address>`
	- Example: `(gdb) break *0x0000000000400be3`
- **List breakpoints**: `(gdb) info breakpoints`
- **Delete a breakpoint**: `(gdb) delete <breakpoint number>`
	- Example: `(gdb) delete 1`

**Controlling Execution**

- **Continue execution**: `(gdb) continue`
- **Single step**: `(gdb) step`

**Handling Breakpoints**

- **Run with arguments**: `(gdb) run <args>`
	- Example: `(gdb) run test test`
- **Backtrace**: `(gdb) backtrace`

**Inspecting Registers**

- **Info registers**: `(gdb) info register`

**Inspecting Memory**

- **Examine memory**: `(gdb) x/<count><format><unit> <address>`
	- Example: `(gdb) x/32x 0x7fffffffe940`
	- Formats: `x` (hex), `d` (decimal), `i` (instructions), `s` (string), `c` (character)
	- Units: `b` (bytes), `w` (words, 4 bytes), `g` (giant words, 8 bytes)

**Debugging Symbols**

- **List source code**: `(gdb) list`
- **Info locals**: `(gdb) info locals`

**Info File**

- **File details**: `(gdb) info file`

**Settings and Attachments**

- **Follow forks**: `(gdb) set follow-fork-mode child`
- **Attach to process**: `(gdb) attach <pid>`
- **Allow core files**: `$ ulimit –c unlimited`
- **Use core file**: `$ gdb <binary> <corefile>`

**GUI and Layouts**

- **Text User Interface**: `$ gdb –tui`
- **Layout asm**: `(gdb) layout asm`
- **Layout regs**: `(gdb) layout regs`

**Helpful GDB Plugins**

- **PEDA**: Python Exploit Development Assistance for GDB
	- [PEDA](https://github.com/longld/peda)
- **GEF**: GDB Enhanced Features
	- [GEF](https://github.com/hugsy/gef)
- **Lisa.py**: Exploit Dev Swiss Army Knife
	- [Lisa.py](https://github.com/ant4g0nist/lisa.py)
- **Voltron**: Extensible debugger UI toolkit
	- [Voltron](https://github.com/snare/voltron)

---
links: [[907 ED TOC - Debugging|ED TOC - Debugging]] - [[themes/000 Index|Index]]
