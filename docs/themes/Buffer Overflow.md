tags: #exploit #C #buffer #overflow
 
# Buffer Overflow

links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]

---

## Overview

A buffer overflow occurs when more data is written to a buffer than it can hold, causing the excess data to overwrite adjacent memory. The goal of a buffer overflow is often to exploit this behavior to execute arbitrary code or manipulate the program's execution flow.

![[overflow-code.png]]

In the above example the user can provide an arbitrary length username which is then copied into a 128 Byte `name` buffer. Since the `name` buffer is on the stack, if `username` is longer than 128 Bytes, data on the stack will be overwritten (overflown).

![[overflow-stack-3.png]]

Assuming the Username is 129 characters of A, after `strcpy(name, username)` the top of the stack will look something like this:

![[overflow-stack-2.png]]

Even though the password might have been wrong which lead to `isAdmin` being 0 after calling `checkPassword`, the overflow changed the value of `isAdmin` to 0x41 which means the user will see the `You are admin!` prompt

## Program execution flow manipulation

Buffer overflows can also be used to manipulate the program execution flow. This is done by changing the return address. The return address can be changed to the address of a specific function the the attacker wants to execute ([challenge10](https://exploit.courses/#/challenge/10)). It's also possible that the attacker provides shell code as a username and then sets the return address to the `name` variable which will execute the shell code ([challenge11](https://exploit.courses/#/challenge/11))

To change the return address and therefore the program flow the following steps are necessary:

1. **Find the offset between the address of the name buffer and the return address**

One way to find the offset is brute force. Try different lengths of usernames and set a breakpoint at the `ret` call in handleData (`disas handleData`, `break *handleData+115`). Then print `esp` to see where it is currently pointing to (x/1x $esp). If this address is overwritten with the username the username is too long and if it's not overwritten at all it's too short.

It's also possible to calculate the offset by subtracting the address of `name`from the address of the `esp` while it is pointing at the return address (breakpoint at `ret`).

2. **Find the address of the function**

When the function to be executed is part of the running program it can be found with `print function_name`.

If the code to be executed is in the `name` variable itself as shell code then the address of the `name` function can be found with `print &name`

3. **Add the address to the input**

The found address then needs to be appended to the username that is given as input which can be done like this `(gdb) r 'perl -e 'print "A" x 144 . "\xf8\x91\x04\x08"'' password` if the address to be executed is `0x80491f8`.

When executed the `strcpy` call will fill the 128 Byte `name` buffer, 4 Byte `isAdmin` integer, two stored 4 Byte registers and the stored 4 Byte `ebp` with "A", followed by overwriting the stored return address with the address provided in the username.

The program will print that the user is Admin and normally the program would jump back to the `main` function which has initially called the `handleData` function. But because the return address was changed, the program flow also changed.

![[overflow-stack-1.png]]

Here the `leave` call was just executed ([[Function Calls]]). The overwritten `ebp` was popped which means the `ebp`register now contains the address `0x41/0x41/0x41/0x41` and the `esp` now points to the overwritten return address. The next call after `leave`is `ret`which will execute the code at the overwritten address.

---

links: [[900 ED MOC|ED MOC]] - [[themes/000 Index|Index]]