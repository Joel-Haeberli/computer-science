tags: #malware-analysis
 
# Anti-analysis

links: [[807 MAI TOC - Dynamic Analysis|MAI TOC - Dynamic Analysis]] - [[themes/000 Index|Index]]

---

## Intro

Malware authors are aware that their creations will be subjected to analysis by security professionals. To evade detection and prolong their presence on infected systems, they employ various anti-analysis techniques. These methods are designed to identify and evade analysis environments, such as sandboxes, virtual machines (VMs), and debugging tools, preventing the malware from revealing its true behavior.

## Common Anti-analysis Techniques

### Identification of Analysis Tools

Malware can detect the presence of analysis tools commonly used by security professionals, such as debuggers, system monitors, and network analyzers.

- **Detecting Debuggers**: Malware may check for the presence of debuggers by using system calls or specific instructions.
- **Monitoring Tools**: Tools like Process Monitor, Process Explorer, and Wireshark can be detected through process enumeration, file system checks, or registry keys.

### Virtual Machine Detection

Many analysis environments use VMs to safely execute and study malware. Malware can use several techniques to detect whether it is running inside a VM.

- **Hardware Artifacts**: Checking for virtualized hardware components that are different from physical hardware.
- **CPU Instructions**: Using specific CPU instructions (e.g., CPUID) that behave differently in a virtual environment.
- **Guest Additions**: Searching for files, processes, or registry entries related to VM software (e.g., VMware Tools, VirtualBox Guest Additions).

### User Interaction Checks

Malware often expects certain user interactions to confirm it is running on a real user's machine. Without these interactions, it may alter its behavior or remain dormant.

- **Mouse Movements and Clicks**: Checking for mouse activity.
- **Keyboard Input**: Monitoring for keystrokes.
- **GUI Interactions**: Waiting for interactions with dialog boxes or other GUI elements.

### Timing Attacks

Malware can use timing checks to evade automated analysis environments, which typically have a limited analysis duration.

- **Sleep Timers**: Introducing long sleep periods to outlast the analysis time.
- **Execution Delays**: Measuring the time taken to execute certain instructions or API calls to detect the presence of instrumentation or monitoring.

### Sandbox Detection

Malware can identify characteristics unique to sandbox environments, such as consistent configurations, lack of user data, or specific sandbox artifacts.

- **Environment Artifacts**: Checking for specific files, processes, or registry entries associated with sandbox tools.
- **System Configuration**: Detecting unusual system configurations that differ from typical user environments.
- **Network Activity**: Analyzing network behavior to identify patterns indicative of sandbox analysis.

## Examples of Anti-analysis Techniques

### Detecting Analysis Tools

Malware might look for the presence of specific processes or files associated with analysis tools. For example:

- **Process Checks**: Searching for running processes like `wireshark.exe` or `procmon.exe`.
- **File System Checks**: Looking for installation directories or configuration files associated with analysis tools.

### Virtual Machine Detection via CPUID

The CPUID instruction can reveal whether the CPU is virtualized. For example:

- **CPUID Check**: Calling CPUID with specific parameters and examining the results to determine if the system is running in a VM.

### User Interaction Example

Malware might wait for specific user actions before executing its payload:

- **Waiting for Mouse Movement**: The malware could delay execution until it detects mouse movement to ensure it is on a real user's system.

### Timing Attack Example

Malware can implement sleep timers to evade detection:

- **Extended Sleep**: Using sleep functions to pause execution for a duration longer than typical sandbox analysis periods.

## Anti-analysis Measures in Sandboxes

To counteract these anti-analysis techniques, modern sandboxes employ several strategies:

- **User Behavior Emulation**: Simulating user interactions to trigger malware behavior.
- **Stealth Instrumentation**: Reducing the detectable footprint of sandbox instrumentation.
- **Time Manipulation**: Bypassing sleep timers by manipulating the system clock.

---
links: [[807 MAI TOC - Dynamic Analysis|MAI TOC - Dynamic Analysis]] - [[themes/000 Index|Index]]