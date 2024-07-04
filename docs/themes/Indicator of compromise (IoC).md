tags: #malware-analysis
 
# Indicator of compromise (IoC)

links: [[806 MAI TOC - Malware Identification|MAI TOC - Malware Identification]] - [[themes/000 Index|Index]]

---

**Anatomy of Cyberattacks**

- Infection vectors: email attachments, web, USB keys.
- Malware installation and patient zero.
- Command and control (CC) servers.
- Data exfiltration, deployment of new tools, lateral movement.
- Objectives: steal information, modify transactions, abuse systems, attack other systems.

**Traces of Malware Attacks**

- Compromised endpoints: malware files, registry entries, mutexes, process names, etc.
- Network infrastructure: IP addresses, domain names, URLs used for CC communication.

**Indicators of Compromise (IOCs)**

- Not all indicators are useful; useful ones are called IOCs.
- Examples of non-useful indicators: connection to 8.8.8.8, dropping files named "faq.txt".
- Examples of useful IOCs: specific IP addresses, file hashes, URLs.

**Role of IOCs in Cyber Defense**

- Detection of attacks and identification of compromised systems.
- Examples: scanning for specific mutexes or checking logs for known malicious IPs.
- Availability through continuously updated IOC feeds as part of Cyber Threat Intelligence (CTI).

**Sources of IOC Feeds**

- Information Sharing and Analysis Centers (ISACs).
- Commercial vendors, organizational sources, open-source intelligence.

**Useful Tools and Platforms**

- VirusTotal for IP, domain, URL lookups.
- abuse.ch for free intelligence on malware and attacker infrastructure.
- OSINT reports from vendors like ESET and platforms like Malpedia.

**IOC Lifetime**

- IOCs have limited lifetimes as attackers modify them to evade detection.
- Pyramid of Pain: the ease of changing IOCs determines their value; easier to change means less valuable.


![[pain.png]]
 
---
links: [[806 MAI TOC - Malware Identification|MAI TOC - Malware Identification]] - [[themes/000 Index|Index]]