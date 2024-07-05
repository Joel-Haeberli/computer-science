tags: #malware-analysis
 
# Persistence

links: [[805 MAI TOC - Malware Persistence|MAI TOC - Malware Persistence]] - [[themes/000 Index|Index]]

---

## Introduction

Persistence mechanisms allow malware to survive a reboot and to launch automatically when the system restarts or a user logs in. To achieve persistence, attackers need to store some malware component on disk and use an operating system mechanism to launch the malware. The malware component on disk is an additional artifact left by the attacker. Some malware remains memory-resident to avoid detection and persistence mechanisms entirely.

## Persistence Mechanisms

### Windows Registry

The Windows registry contains system configuration information, such as networking, drivers, startup, and user accounts. It has a hierarchical structure similar to a file system, with keys that act like folders and contain sub-keys or (name, type, data) tuples.

**Registry Hives**: Stored on disk, registry hives contain different parts of the registry and are consolidated in the registry viewer/editor.

**Autostart Information**: The registry includes keys for autostarting programs upon user logon, such as:

- `HKLM\Software\Microsoft\Windows\CurrentVersion\Run`
- `HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce`
- `HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnceEx`
- `HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run`

**Registry Analysis**: From an attack perspective, the registry can contain:

  - Autostart entries for malware persistence.
  - Data stored by malware.
  - Partial information on programs executed and files accessed.
  - Encrypted or obfuscated malware payloads.

Tools like `Regedit.exe` can be used to inspect and modify the registry for live forensic analysis.

### Windows Services

Windows services are processes running independently of user logons, providing various system functions such as system updates, printing, security, and antivirus.

- **Service Types**: Services can be kernel drivers, standalone processes, or shared services. Shared services run multiple services within a single process (`svchost.exe`), with each service loaded as a DLL into the `svchost.exe` process.
- **Service Control Manager**: Managed by `services.exe`, which starts, stops, and restarts services.
- **Malware Usage**: Malware can use services to launch itself, disable security services, or load malicious drivers. It may also stop services for self-defense, such as antivirus or firewall services.
- **Creation of Services**: Malware typically uses tools and techniques like `sc.exe`, `regsvr32.exe`, or the Windows API to create services.

**Example Command to create a service**:

```sh
sc create TestService2 start=auto binpath=C:\Users\Username\Desktop\Sample.exe
sc start TestService2
```

This command requires administrator privileges as creating new services is a privileged action.

### Scheduled Tasks

Scheduled tasks allow periodic execution of commands, similar to cron jobs in Unix. Tasks can be triggered by time or events and are used for legitimate purposes like software updates and data processing.

- **Malware Usage**: Malware can abuse scheduled tasks to achieve persistence.
- **Creation Methods**: Tasks can be created using `schtasks.exe`, WMI, PowerShell, or programmatically via Task Scheduler API.

**Example Command to Create a Scheduled Task**:

```sh
schtasks /create /sc minute /mo 2 /tn "Security Script" /tr "C:\Windows\System32\notepad.exe"
```

This command creates a scheduled task that runs `notepad.exe` every two minutes.

On Windows 10 and later, scheduled tasks are handled by a `svchost.exe` process. XML-based descriptions of tasks can be found in:

- `C:\Windows\System32\Tasks`
- `C:\Windows\SysWow64\Tasks`

##### Binary Patching / File Infections

Binary patching involves adding malicious code to existing executables or DLLs. This method, historically known as a "virus," can make malware start very early in the boot process, especially with MBR patching.

**Detection of Binary Patching**:

- Checking files against a hash database of known good binaries.
- Verifying file signatures (most executables from Microsoft are digitally signed).
- **Example Command Using `sigcheck`**:

  ```sh
  sigcheck c:\windows\system32
  ```

To perform a VirusTotal lookup for unknown files:

  ```sh
  sigcheck -u -vr c:\windows\system32
  ```

### DLL Search Order Hijacking

DLL search order hijacking involves manipulating the order in which the system searches for DLLs to load, allowing malware to be loaded instead of legitimate DLLs.

- **Detection**: Identifying unexpected DLLs loaded into processes and verifying the legitimacy of DLLs can help detect hijacking attempts.

### Autostart Directories

Binaries in Windows startup directories are automatically started by the OS after user login. The directories are:

- `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`
- `C:\Users\Username\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`

Malware can place executables in these directories to achieve persistence.

---
links: [[805 MAI TOC - Malware Persistence|MAI TOC - Malware Persistence]] - [[themes/000 Index|Index]]