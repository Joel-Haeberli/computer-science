tags: #malware-analysis #processes
 
# Processes DLLs APIs

links: [[802 MAI TOC - Windows & OS background|MAI TOC - Windows & OS background]] - [[themes/000 Index|Index]]

---

## Used Tools

The following tools are used to inspect Windows processes and memory maps:

- Process explorer (Windows Sysinternals)
- VMMap (Windows Sysinternals)
- Process Hacker [https://processhacker.sourceforge.io/](https://processhacker.sourceforge.io/)

TODO: Add link to cookbook or something to show how to use the tools

## Processes

A process is an instance of a running program, with its own isolated virtual memory space, unique process ID (PID), and process name. It contains the code and data necessary for execution, loaded into memory by the OS loader, and includes a command line that may contain arguments and the current directory from which it was started. Processes can have multiple instances, and each process includes at least one thread, which is the actual code executing within the process.

![[process_overview.png]]

## Dynamic-link libraries (DLLs)

Dynamic Link Libraries (DLLs) are files that contain code and data used by multiple programs simultaneously. On Windows, DLLs provide system functionalities, including file operations, process management, networking, cryptography, and user interface elements. Commonly located in `C:\Windows\System32`, examples of DLLs include `NTDLL.DLL`, `KERNEL32.DLL`, and `USER32.DLL`. These libraries enable code reuse, reducing duplication and enabling efficient program execution.

![[dll_overview.png]]

## Application Programming Interface (APIs)

Application Programming Interfaces (APIs) are sets of functions provided by DLLs, facilitating interaction with system services and resources. Windows APIs are  documented on MSDN and are crucial for both legitimate software development and malware analysis. Examples of API usage include file operations, where functions like `CreateFile` and `WriteFile` handle file creation and data writing. Understanding Windows APIs is essential for software developers and security professionals alike.

**C code calling Windows APIs**

![[api_calling_code_example.png]]

**API examples**

- Win32 APIs on files
	- CreateFile
	- WriteFile
	- ReadFile
	- SetFilePointer
	- Delete File
	- Close File
- Win32 APIs on registry
	- RegCreateKey
	- RegDeleteKey
	- RegSetValue
- Win32 APIs on virtual memory
	- VirtualAlloc
	- VirtualProtect
	- NTCreateSection
	- WriteProcessMemory
- Win32 APIs on mutex
	- Create Mutex
	- OpenMutex

Handles are unique identifiers used by the Windows API to represent objects such as files, processes, and memory allocations. For example, `CreateFile` returns a handle that can be used in subsequent operations like `WriteFile` to perform actions on the specified file.

**Handles example**:

```
hFile1 = CreateFile("C:\test1.txt", GENERIC_WRITE, 0, NULL, CREATE_NEW, FILE_ATTRIBUTE_NORMAL, NULL);

hFile2 = CreateFile("C:\test2.txt", GENERIC_WRITE, 0, NULL, CREATE_NEW, FILE_ATTRIBUTE_NORMAL, NULL);

WriteFile(hFile2, DataBuffer, dwBytesToWrite, &dwBytesWritten, NULL); WriteFile(hFile1, DataBuffer, dwBytesToWrite, &dwBytesWritten, NULL);
```

---

links: [[802 MAI TOC - Windows & OS background|MAI TOC - Windows & OS background]] - [[themes/000 Index|Index]]