tags: #malware-analysis
 
# Hooking techniques

links: [[804 MAI TOC - Hooking|MAI TOC - Hooking]] - [[themes/000 Index|Index]]

---

## Introduction

Hooking is a technique used in malware to intercept and modify the execution flow of software. It allows an attacker to manipulate data, steal information, and take control of processes. While often associated with malicious activities, hooking also has legitimate applications in software development and security tools.

## Why Malware Uses Hooking

1. **Control and Manipulation**: Hooking allows attackers to intercept and modify function calls within a victim process, enabling control over the process.
2. **Data Theft**: Attackers can insert malicious code into system and library calls to steal or manipulate data passed through these calls.
3. **Man-in-the-Browser Attacks**: Hooking can be used to steal credentials by intercepting API calls like `HTTPSendRequest()`, or modify web forms to gather sensitive information.
4. **Eavesdropping**: Attackers can monitor network traffic by hooking before encryption or after decryption.
5. **Rootkit Techniques**: Hooking can hide files, processes, and registry keys by manipulating API calls that list these items.
    - For example, by hooking an API that lists directory contents, attackers can filter out specific files from the return values, effectively hiding them from the user.

## Legitimate Applications of Hooking

- **Security Tools**: Some security tools use hooking to monitor and protect systems.
- **Operating Systems**: Windows OS, for example, uses hooking for various system functions.

## Path of a System Call

1. **Process Initiation**: A user-mode process, such as `notepad.exe`, makes a system call like `WriteFile()`.
2. **Kernel32.dll**: The call is directed to the `Kernel32.dll` which handles Windows API functions.
3. **IAT (Import Address Table)**: The call is linked via the IAT, an array of addresses pointing to functions in DLLs.
4. **Execution in Kernel**: The call then proceeds to the Windows kernel where the actual system-level operation is performed.

![[hooking_syscall_path.png]]

## Path of a Library Call

1. **Process Initiation**: A user-mode process, such as `notepad.exe`, calls a library function like `CryptProtectData()`.
2. **crypt32.dll**: The call is directed to the `crypt32.dll` which handles cryptographic functions.
3. **IAT**: Similar to system calls, the call is linked via the IAT.
4. **Execution**: The library function is executed as per the linked address in the DLL.

![[hooking_library_call.png]]

## Hooking: Idea and Placement

- **Concept**: Hooking involves inserting code into the execution path of a legitimate program to divert execution to malicious code. Hooking and code injections are related, as the malicious code is typically injected into the victim process.
- **Placement**: Hooks can be placed in various processes depending on the attacker's goal.
    - **Web Browsers**: To steal credentials from web forms.
    - **Password Managers**: To compromise saved passwords.
    - **Network APIs**: To control network traffic.
    - **File APIs**: To hide files or directories.

![[hooking_idea.png]]

## Hooking Techniques

1. **IAT Hooks (User Mode)**: Modify function pointers in the IAT to point to malicious code.
2. **EAT Hooks (User Mode)**: Modify the Export Address Table (EAT) to redirect function calls.
3. **Inline Hooks (User Mode)**: Insert a jump instruction in the original code to redirect execution to malicious code.
4. **SSDT Hooks (Kernel Mode)**: Modify the System Service Descriptor Table (SSDT) in the kernel to redirect system calls.
5. **IDT Hooks (Kernel Mode)**: Modify the Interrupt Descriptor Table (IDT) to intercept hardware and software interrupts.
6. **Driver IRP (Kernel Mode)**: Intercept I/O request packets (IRPs) in kernel mode drivers.

### IAT Hooking in Detail

- **Concept**: IAT hooking involves modifying entries in the Import Address Table so that function pointers point to malicious code instead of the original function.
- **Implementation**: This is achieved by altering the addresses in the IAT to point to the attacker's code, which then executes instead of the intended function.
- **Ease of Use**: IAT hooking is relatively simple to implement, requiring only modifications to the IAT entries.

![[hooking_iat_detail.png]]

### Example of Inline Hooking

- **Zeus Malware**: Uses inline hooking to intercept function calls and redirect them to malicious code, demonstrating a practical implementation of this technique.

![[hooking_zeus_malware.png]]

## Detection of Hooks

1. **Live Forensics**: Use a debugger to inspect memory and code of running processes.
2. **Memory Forensics**: Use tools like Volatility with the `apihooks` plugin to detect hooks.
3. **IAT Hook Detection**:
    - **Heuristics**: Iterate through IAT entries in the DLLs of the process being analyzed.
    - **Criteria**: If an entry points outside the DLL currently being inspected, a hook is likely present.
4. **Inline Hook Detection**:
    - **Heuristics**: Locate functions in DLLs and analyze the function code.
    - **Criteria**: Check for non-legitimate execution transfers (e.g., JMP, CALL) to code outside the function body.

### False Positives

- Not every hook is malicious. To reduce false positives, it is important to check where a hook points to and whether it is pointing to legitimate or malicious code. For example, hooks pointing to code injection or DLL injection regions are likely malicious.

### HollowsHunter

- **Overview**: HollowsHunter is a versatile tool used to find code injections and hooks.
- **Functionality**: 
    - **Inline Hooks**: Can identify inline hooks using commands like `hollows_hunter32.exe /hooks`.
    - **IAT Hooks**: Can also identify IAT hooks using commands like `hollows_hunter32.exe /iat`.
    - **Output**: The tool generates detailed reports, producing a folder per suspicious process with analysis results.
    - **Details**: Reports include information such as the name of the hooked API, the relative virtual address of the hook, and the module to which the hook points.

---

links: [[804 MAI TOC - Hooking|MAI TOC - Hooking]] - [[themes/000 Index|Index]]