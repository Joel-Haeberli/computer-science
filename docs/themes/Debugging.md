tags: #debugging #gdb 

# Debugging

links: [[907 ED TOC - Debugging|ED TOC - Debugging]] - [[themes/000 Index|Index]]

---

## Static analysis

### file

Get generic information about the executable. Example:

- 32 bit
- little endian machine (`LSB`)
- Intel 80386 (x86)
- Dynamically linked
- Not stripped (debug symbols are still there)

```bash
$ file challenge00
challenge00: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=a8dae60baebe49945ea443d4cc4198b946da27fc, not stripped
```

### readelf

Display information about the sections and segments of the program on disk:

```bash
# get segments
readelf -l challenge00

# get segments & sections
readelf -l -S challenge01
```

### objdump

Decompile the program on disk (same as `gdb disas`). It will use the [[Assembler 101#Intel vs. AT&T Assembly Syntax|AT&T syntax]]:

```bash
objump -d challenge00 | less
```

We can create [[shellcode]] from the output of objump:

```bash
# must not contain null bytes (change asm code!)
objdump -d print | grep "^ " \
 | cut -d$'\t' -f 2 | tr '\n' ' ' | sed -e 's/ *$//' \
 | sed -e 's/ \+/\\x/g' | awk '{print "\\x"$0}'
```

### hexdump

Analyse binary data of a file in a textual hexadecimal view:

```bash
# create hexcode of string
echo "Hi there" | hexdump -C

# skip -s bytes (offset), read -n bytes
hexdump -C -s 0x3018 -n 32 challenge01
```

## Dynamic analysis
### gdb

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
