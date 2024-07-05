tags: #malware-analysis
 
# Intro Dynamic Analysis

links: [[807 MAI TOC - Dynamic Analysis|MAI TOC - Dynamic Analysis]] - [[themes/000 Index|Index]]

---

## Intro

Malware analysis techniques are generally categorized into static and dynamic analysis. Both approaches are important for understanding how malware operates, identifying its objectives, and devising strategies for mitigation.

## Static Analysis

Static analysis involves examining the malware code without executing it. This approach can range from simple techniques like string analysis and file header inspection to more advanced techniques like disassembly and reverse engineering. Analysts may use tools such as IDA Pro, Ghidra, or binary file analyzers to inspect the code.

### Techniques in Static Analysis

- **String Analysis**: Extracting and analyzing strings within the malware to infer potential commands, URLs, or other indicators of its behavior.
- **PE Characteristics**: Inspecting the Portable Executable (PE) file format to determine the target operating system, architecture, and potential capabilities.
- **Disassembly**: Converting binary code into assembly language to understand the malware's logic and operations.

### Limitations of Static Analysis

While static analysis can provide useful insights, it has several limitations:

- **Obfuscation and Packing**: Malware often uses obfuscation and packing techniques to hide its actual code, making static analysis difficult and time-consuming.
- **Incomplete Behavior Insight**: Static analysis does not provide real-time behavior of the malware, such as network communications, file operations, or system modifications.

Due to these limitations, static analysis alone is often insufficient for a complete understanding of malware, leading analysts to employ dynamic analysis as a complementary approach.

## Dynamic Analysis

Dynamic analysis involves executing malware in a controlled environment to observe its behavior and interactions with the system. This technique provides real-time insights into the malware's operations, which are crucial for identifying its actual impact and objectives.

### Key Activities in Dynamic Analysis

Dynamic analysis involves monitoring various activities and operations performed by the malware during execution. These activities include:

- **File Operations**: Observing what files are created, modified, deleted, or accessed by the malware.
- **Registry Operations**: Tracking changes made to the Windows registry, which may include adding, modifying, or deleting registry keys and values.
- **Network Communication**: Capturing and analyzing network traffic to identify communication with command and control (C2) servers, data exfiltration, or other malicious network activities.
- **API and System Calls**: Recording sequences of API and system calls made by the malware to understand its behavior and functionality.
- **Process and Thread Activity**: Monitoring process creation, termination, and threading activity to detect process injection or other manipulations.
- **Memory Dumps**: Capturing memory dumps to analyze unpacked or decrypted code that may not be visible in static analysis.

### Tools and Techniques

Several tools and techniques are used in dynamic analysis to capture and analyze the behavior of malware:

- **Process Inspection Tools**: Tools like Process Explorer and Process Hacker provide insights into running processes and their activities.
- **Debuggers**: Debuggers such as binary debuggers, .NET debuggers, and script debuggers help step through the code to observe its execution.
- **Network Capturing Tools**: Tools like Wireshark and Fiddler capture network traffic for analysis.
- **API and System Call Tracers**: Tools like Procmon (Process Monitor) and API Monitor record system and API calls made by the malware.
- **Malware Sandboxes**: Automated environments that execute malware samples and provide detailed reports on their behavior.

### Benefits of Dynamic Analysis

Dynamic analysis offers several advantages in understanding malware:

- **Behavioral Insights**: By observing the malware's behavior, analysts can identify its functionality, such as persistence mechanisms, data theft methods, or destructive actions.
- **Detection of Obfuscated Code**: Malware often uses packing and obfuscation techniques to evade static analysis. Dynamic analysis can reveal the actual code executed at runtime.
- **Identification of Indicators of Compromise (IOCs)**: Dynamic analysis helps in identifying IOCs such as file paths, registry keys, network addresses, and other artifacts that can be used for detection and mitigation.

#### Limitations of Dynamic Analysis
While dynamic analysis provides valuable insights, it has some limitations:

- **Lack of Coverage**: Dynamic analysis can only observe the behavior that is triggered during the execution period. Some parts of the malware may remain dormant or only activate under specific conditions, leading to incomplete analysis.
- **Anti-analysis Techniques**: Malware may employ various anti-analysis techniques to detect and evade dynamic analysis environments, such as sandboxes or debuggers.

---
links: [[807 MAI TOC - Dynamic Analysis|MAI TOC - Dynamic Analysis]] - [[themes/000 Index|Index]]