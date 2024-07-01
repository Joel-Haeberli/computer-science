tags: #DF
 
# Overview of Digital Forensics

links: [[701 DF TOC - Forensics Basics & History|DF TOC - Forensics Basics & History]] - [[themes/000 Index|Index]]

---

## Locard's Exchange Principle

The Locard's exchange principle was a idea from french criminologist Edmon Locard (1877-1966) which states:

- a criminal always brings "something" to a crime scene
- a criminal always takes "something" away from the crime scene

**This principle can be adapted for digital forensics:**

- Crime scene = cyber crime scene
- digital evidence on the client: cookies, cache, data, etc.
- digital evidence on the server: logs, IP addresses other IOCs (Indicator of compromise)

**Adaption to OSINT and Intelligence gathering:**

- when you search for or get information, the provider learns who you are and what you are looking for

## Technical Overview

> Forensics is for Criminals and Victims

There are multiple areas of digital forensics...

**Original areas:**

- Computer forensics (disks, removable media, flash chips...) 
- Network forensics (network intrusions, abuse...)  
- Software forensics (examining malicious code, malware...) 
- Live system forensics (compromised hosts, memory dumps...)

**Modern areas:**

- Mobile forensics (smart phones, tablets)  
- Hardware/IoT forensics (internet connected, tiny devices...) 
- Vehicle forensics (automobiles, drones)  
- Cloud and Social Media forensics

**Future areas:**

- medical devices and implants (smart watch, e.g. exact time of death)
- telemetry data analysis and correlation
- industrial control systems, smart buildings (robots, e.g. hack insulin pump remotely)

## Concepts and Terms

**Abbreviations:**

- DF = Digital Forensic
- DFIR = Digital Forensic Incident Response
- LE = Law Enforcement
- LEA = Law Enforcement Agency
- LEO = Law Enforcement Officer

**Concepts:**

- **Acquisition vs Analysis**: Acquisition collects and preserves digital evidence; analysis examines and interprets it
- **Evidence vs Intelligence**: Evidence is data for legal proof; intelligence is information for decision-making (no reliability)
- **Private vs Public Sectors**: Private sector uses digital forensics for internal investigations; public sector for law enforcement and national security
- **Victims vs Perpetrators (eBanking, CP)**: Victims suffer from cybercrimes like e-banking fraud or child exploitation; perpetrators commit these crimes
- **Limitations vs Requirements (technical, policy, legal, ethical)**: Limitations are challenges in digital forensics or laws (GDPR: General Data Protection Regulation); requirements are standards for technical, policy, legal, and ethical compliance (FINMA, ...)

## Digital Evidence

> Digital evidence refers to any information or data stored or transmitted in digital form that can be used in investigations and legal proceedings. It includes files, emails, logs, and any other electronic data that may support or refute hypotheses in criminal or civil cases.

**Basic forensic process for Digital Evidence:**

- Evidence collection/acquisition
- Preservation, integrity, cain-of-custody
- Analysis, interpretation
- Presentation, reporting

**Why is Digital Evidence Important/useful:**

- Admissible in a court of law
- Usable in internal disciplinary hearings, internal incident reports, other investigations
- Helps reconstruct past events/activities (timelines)
- Shows: possession/handling of digital data, use/abuse of IT infrastructure and services, evidence of policy violation or illegal activities

### Characteristics of Digital Evidence

Digital Evidence is...

**Hard to get:**

- Attacks and intrusions may be cleverly hidden (obfuscation, crypto, steg)
- Anti-forensic activity prevents collection
- Encrypted drives and files
- Proprietary devices or file formats
- Network traffic only exists for milliseconds on the wire
- Over-provisioned areas on flish drives or service areas on disks

**Easy to destroy:**

- Booting a PC updates timestamps and modifies files
- Attaching external drives without a write blocker can modify timestamps, create files or overwrite deleted data
- Volatile memory e.g RAM is lost when a machine is powered off

## Tools and Platforms

- The Sleuth Kit and Autopsy - [https://sleuthkit.org/](https://sleuthkit.org/)
- Forensic Focus - [https://forensicfocus.com](https://forensicfocus.com)
- Kali Linux - OS with tons of forensic tools
- [r/computerforensics](https://www.reddit.com/r/computerforensics/) and [r/digitalforensic](https://www.reddit.com/r/digitalforensics/)

---
links: [[701 DF TOC - Forensics Basics & History|DF TOC - Forensics Basics & History]] - [[themes/000 Index|Index]]