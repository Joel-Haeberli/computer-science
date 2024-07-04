tags: #malware-analysis #guest-lecture
 
# Endpoint Detection Evasion

links: [[808 MAI TOC - Guest Lectures|MAI TOC - Guest Lectures]] - [[themes/000 Index|Index]]

---

**Understanding Endpoint Detection and Response (EDR):**

- Modern EDRs use static and dynamic detection mechanisms, often integrated.
- Instrumentation methods include user mode hooks, kernel mode instrumentation, and hypervisor instrumentation.
- On-access scans and emulation are integral parts of EDR operations, scanning files on open, read, write, and execute actions.

**EDR Components and Techniques:**

- **Anti-Malware Scan Interface (AMSI):** Cooperative static scanning through callbacks; popular applications like MS Office, .NET, and PowerShell use AMSI.
- **User Mode Hooking:** Visibility into system API calls using various methods such as inline hooks, breakpoints, and hypervisor-backed hooks.
- **Kernel Callbacks:** Includes process, thread, image load notifications, and registry operation callbacks.
- **NDIS and Minifilter Drivers:** Implement network functionality and filesystem on-access scanning, respectively.
- **Syscall Hooks:** Methods to hook system calls, often bypassed by techniques like hypervisor-backed hooks.

**EDR Evasion Techniques:**

- **Passive Evasion:**
	- Encoding strings and code, dynamic decoding and encryption (sleep masking).
	- Exploiting emulation logic flaws and modifying detected code.
- **Active Evasion:**
	- Direct attacks on EDR components using vulnerable drivers and scan exclusions.
	- Attacks against AMSI, such as hooking or corrupting runtime state.

**Advanced Evasion Techniques:**

- **PowerShell AMSI Unhooking:** Forcing error states to disable AMSI callbacks.
- **Signature Evasion:** Breaking up injection logic, signing malware with stolen certificates, DLL sideloading, and using system calls to avoid detection.
- **System Call Instrumentation:** Direct and indirect system calls, often using frameworks like SysWhispers.

**Active Evasion Methods:**

- Removing or modifying instrumentation code.
- Removing user mode hooks using tools like ScareCrow and PEzor.
- Stack tampering with ROP techniques to simulate different call stacks.
- Attacking ETW subsystems and silencing Sysmon by hooking EtwEventWrite.

---
links: [[808 MAI TOC - Guest Lectures|MAI TOC - Guest Lectures]] - [[themes/000 Index|Index]]