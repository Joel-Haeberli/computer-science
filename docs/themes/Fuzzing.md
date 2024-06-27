tags: #exploiting #fuzzing
 
# Fuzzing

links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]

---

## Overview

- **Fuzzing**: finding bugs (especially exploitable bugs) by bombarding target with non-conform data
- **Fuzzer**: a program which generates new "random" inputs, and feeds it to the target program
	- **Traditional fuzzing**: mutate/generate input, feed to target program $\rightarrow$ dumb, inefficient, brute force
	- **Mutation-based**: modify existing test samples (shuffle, change, erase, insert)
	- **Grammar-based**: define new test sample based on models, templates, RFCs or documentation

## Mutation-based Fuzzer

Take an input file, modify it a bit, continue and identify crashes.

**Examples**: Ffmpeg (movie files), Winamp (MP3 files), *Antivirus* (ELF files)

## Grammar-based Fuzzer

Cannot just bit flip (e.g. `alert(1);` is valid, `alfrt(1);` is garbage) $\rightarrow$ create a random output based on grammar, use it as input file for program, identify crashes.

**Use-Case**s: Browser (JavaScript, HTML), FTP, HTTP

**Examples**: Peach Fuzzer, Domato

## AFL

- American fuzzy lop
- Introduced "Code Coverage" to the masses
- "Observe" program to see if a new input (mutated from corpus) reaches new code path

![[feedback-based-fuzzing.png]]

## Fuzzing Challenges

- good to identify basic blocks or bugs like
	- `malloc(user_data_size)`
	- `if a > 100`
	- `switch(a)`
- low probability of catching
	- `if a == 0x31337`
	- `if a == "CONNECT"`
- Solutions
	- **wordlists**: `CONNECT`, `SEND`, `RECEIVE`, ... $\rightarrow$ use `strings` commands on the binary
	- **translate string comparison to per-byte**: `if a[0] == 0x37){ if (a[1] == 0x13) ...` (LD_PRELOAD, code transformation via compiler plugin, ...)
	- constraint solving in code via **symbolic execution** (angr, KLEE) $\rightarrow$ translate compiled commands (assembly) into a higher-level language (e.g. VEX), perform reasoning on it and use constraint solver to reach certain code paths

## DARPA & CGC Shellphish

CGC Shellphish is a team and their framework that participated in the DARPA Cyber Grand Challenge (CGC), using advanced techniques like symbolic execution and automated vulnerability discovery to identify and exploit security flaws in binary programs. Their tools and methodologies, built on platforms like Angr, enable automated analysis and exploitation of vulnerabilities.

![[fuzzing-symbolic-execution.png]]

## Compiler Flags

There are compiler options to enable advanced error detection routines

- Will slow down the program massively
- Will find bugs which do not directly lead to crash
- Use together with fuzzing

**Examples**

- **AddressSanitizer (ASAN)**: a memory error detector for C/C++ programs that identifies issues like buffer overflows, use-after-free, and memory leaks, helping developers find and fix memory-related bugs $\rightarrow$ for testing only (do not compile public releases with it!)
- **UndefinedBehaviourSanitizer (Bsan)**: a runtime checker for C/C++ programs that detects undefined behavior such as integer overflows, null pointer dereferences, and incorrect type casts $\rightarrow$ for testing only

---
links: [[915 ED TOC - Further Topics|Further Topics]] - [[themes/000 Index|Index]]