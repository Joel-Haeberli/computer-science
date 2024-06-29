tags: #web #network #security-tool #security-protocol   

# SPA TOC - Exam Questions with Answers

links: [[600 SPA MOC|SPA MOC]] - [[themes/000 Index|Index]]

---
## Part 1

### Topic 1: Information Security

1. **What is meant with Information Security?**
     - Information Security refers to the protection of information and information systems from unauthorized access, use, disclosure, disruption, modification, or destruction, in order to ensure confidentiality, integrity, and availability.
2. **What are the goals of Information Security?**
     - Preservation of confidentiality, integrity, availability and in addition authenticity (non-repudiation), accountability and auditability
3. **What are older terms for Information Security?**
     - Computer security, data security and IT security
4. **Whats an information asset?**
     - In a nutshell, an **information asset** is an atomic piece of information that has meaning/value to an organization or individual. Information assets have manageable and recognizable value, risk, content and life-cycles. Examples: Database with contacts of the organization, all financial records of a company
5. **Who is responsible to protect information assets?**
     - In many organizations one of these departments (depending on size): IT department, Information security department or Information risk management department.
     - Additionally in many bigger organizations the Chief Information Security Officer (CISO) is the main responsible.
6. **What is an ISMS?**
    - The Information Security Management System (ISMS) is the basis for the development of the information security program. It involves the 4 Ps (People, Process, Products and technology, Partners and suppliers)
7. **Do you now Information Security Standards? Which?**
     - NIST 800 Series, ISO/IEC 27000 group of standards (ISO/IEC 27001 is the certification), BSI Grundschutz, CIS Controls
8. **What are Risks?**
     - A risk is the potential for loss or damage when a threat exploits a vulnerability in information systems or processes, resulting in an impact on the confidentiality, integrity, or availability of Information and information systems. Risks can be calculated: risk = costs of potential damage * probability of this damage occurring
9. **What are Security Controls?**
     - Security controls in information security are measures implemented to reduce risks to an organization's information assets. They encompass a mix of technical, administrative, and physical safeguards designed to protect against threats, prevent vulnerabilities, and ensure the confidentiality, integrity, and availability of data. These controls can be preventative, detective, or responsive in nature.
10. **Do you know some important Security Controls? Explain them.**
     - **Data Encryption**: Encrypting data at rest and in transit to protect its confidentiality and integrity. This prevents unauthorized access to sensitive information.
     - **Access Controls**: Implementing mechanisms like user authentication and authorization to restrict access to information based on user roles and privileges.
     - **Audit Logs**: Keeping detailed records of system activities, enabling the monitoring and analysis of security events and potential breaches.
     - **Antivirus and Anti-malware Software**: Protecting systems from malicious software, including viruses, worms, and ransomware, through detection, prevention, and removal
	 - **Security Incident Response Plan**: A predefined plan for managing information security incidents, ensuring a prompt and effective response to minimize impact
	 - **Network Security Controls**: Implementing measures like firewalls, intrusion detection and prevention systems (IDS/IPS), and secure VPNs to protect network infrastructure.
	 - **Regular Patch Management**: Keeping software and systems updated with the latest security patches to address vulnerabilities and reduce the risk of exploitation.
	 - **Data Backup and Recovery Procedures**: Ensuring that critical data is regularly backed up and can be recovered quickly in the event of data loss, corruption, or a security breach.
	 - **User Training and Awareness**: Educating employees about information security risks and best practices to foster a security-aware culture.
	 - **Physical Security Measures**: Protecting physical access to information systems and data storage areas to prevent unauthorized access, damage, or theft.
11. **What's the job of a Security Professional?**
	 1. Understand the requirements of business (for information asset protection)
	 2. Understand the risk for the particular information asset
	 3. devise and understand the countermeasures for risks
	 4. Protecting information assets by implementing security controls
12. **Which Security Controls should be implemented immediate if no other controls are in function (e.g., according to the NSA)?** 
     - Malware defenses, Data recovery capability, Security skills assessment and appropriate training to fill the gaps
13. **What do the acronyms CIA and AAA in connection with Information Security mean?**
     - **C**onfidentiality **I**ntegrity **A**vailability **A**uthenticity (non-repudiation) **A**ccountability **A**uditability
14. **Are you able to explain the meaning of the abbreviated words?**
     - **Confidentiality** = Ensuring information is not disclosed to unauthorized individuals or systems.
     - **Integrity** = Maintaining and assuring the accuracy and completeness of data over its lifecycle.
     - **Availability** = Ensuring that information is accessible and usable upon demand by an authorized entity.
     - **Authenticity (Non-repudiation)** = Verifying the identity of users and the origin of data, ensuring that actions or communications cannot be denied later.
     - **Accountability** = Holding individuals or systems responsible for their actions, typically enforced through traceable and auditable processes.
     - **Auditability** = The ability to track and document system activities and changes, crucial for detecting security violations or operational issues.
15. **What is an "information security incident"?**
     - Is a information security event (breach of information security or failure of controls) that can harm an asset or compromise operations.
16. **What is the difference between an "information security event" and an "information security incident"?**
     - An information security event is a **possible** breach of information security or failure of controls. On the other hand an information security incident is an information security event that can harm an asset or compromise operations.
17. **What are the goals of "security incident management"?**
	 1. Minimize damage of information security incidents
	 2. Detection/dealing with information security vulnerabilities
	 3. Detection/dealing with information security events
	 4. Information security incidents are assessed and responded
	 5. Escalation process is established
	 6. Lessons are learnt

### Topic 2: Hacking Basics

1. **Recently, there were more and more cyber security attacks against critical infrastructures. What is a critical infrastructure? Provide some examples. What are the targets of such attacks?**
     - Power grid
	* Airport
	* Harbour
	* Railway
	* Hospital
	* Core router
	* DNS root NS
	* Cloud Provider
	* Attacks against those often target industrial control systems (ICS) such as supervisory control and data acquisition (SCADA) systems.
2. **From where do external attackers (outside attackers, remote attackers) attack networks and computers?**
     - Can attack from the internet, wireless network or via a physical break-in
3. **Do you know some intrusion techniques? Can you explain these techniques in detail?**
     - Physical intrusion
     - Through Software bugs
     - Through configuration bugs
     - Through design flaws
     - Through weak passwords
4. **List known vulnerabilities of systems. Can you explain these vulnerabilities in more details.**
     - Buffer Overflow
     - Unpatched Software
     - Insecure APIs
     - Misconfiguration
     - Weak Authentication
5. **What authentication methods do you know?**
     - Password-based
     - Two-Factor
     - Biometric
     - Token-based
     - Certificate-based
     - Challenge and Response-based (FIDO)
6. **List and explain the five stages / phases of an intrusion into a system.**
	1. **reconnaissance** (appearing as a normal user, hard to detect)
	2. **scanning** (ICMP scan, Port scan, identify OS and software)
	3. **running exploits** (exploit a vulnerability that was found, you cross the line here)
	4. **establish a foothold** (hide evidence, rootkit installation, replace services, hack other systems from here)
	5. **playing for profit**
7. **Do you know "shortcuts" to the five stages / phases of an intrusion?**
	- Use automated tools for scanning and break in
	- Create fake websites to harvest credentials
	- Infect vulnerable websites with malware
	- Scam mails and messages for social engineering
	- Or directly by phone, as a fake support agent

### Topic 3: Layered Security

1. **Do you know layer specific vulnerabilities (vulnerabilities, which occur on one of the seven layers of the ISO / OSI network reference model)?**
     - Physical Layer: Power outages, theft of hardware and data, unauthorized physical data connection disruptions​​.
     - Data Link Layer: MAC address spoofing, VLAN circumvention, unauthorized network access due to weak authentication​​.
     - Network Layer: Route spoofing, denial of service, IP address spoofing​​.
     - Transport Layer: Transport protocol fingerprinting, vulnerabilities to packet spoofing and hijacking​​.
     - Session Layer: Weak authentication mechanisms, plaintext transmission of credentials, vulnerability to session hijacking​​.
     - Presentation Layer: Poor handling of unexpected input, cryptographic flaws​​.
     - Application Layer: Backdoors and design flaws bypassing security controls, inadequate or overly complex security mechanisms​​.
2. **Can you explain countermeasures?**
     - Physical Layer: Backup power systems, secure hardware storage, secure physical data connections.
     - Data Link Layer: MAC filtering, secure VLAN configurations, strong authentication for network access.
     - Network Layer: Anti-spoofing measures, secure routing protocols, IP address validation.
     - Transport Layer: Secure transport protocol implementations, protection against packet spoofing.
     - Session Layer: Strong authentication, encrypted transmission of credentials, monitoring for unusual session activities.
     - Presentation Layer: Robust input validation, up-to-date cryptographic methods.
     - Application Layer: Secure software design, implementation of thorough security controls, regular checks for logic flaws.
3. **Which vulnerability is the most critical?**
     - The most critical vulnerability can depend on the specific context and environment. However, vulnerabilities in the Application Layer, such as backdoors and design flaws bypassing security controls or inadequate security mechanisms, can be particularly critical. They directly affect the software and services that users interact with and can lead to significant breaches of data and functionality. This layer is often the final defense and the point of interaction for end-users, making it security crucial​​.

### Topic 4: Host and Network Security

1. **What are well known computer-based security mechanisms (Host-based security mechanisms)?**
	- os hardening/updating, host firewall, host IDS/IPS, virus scanner, endpoint security, SIEM
2. **What are well-known network-based security mechanisms?**
	- network firewalls (subnets, segments, zones) against external attackers
	- access control against internal attackers (network IDS/IPS, network access control)
	- SIEM
3. **What are capabilities of network firewalls?**
	- connect two or more network segments
	- control, log, modify (mangle), filter packages
4. **What are limitations of network firewalls?**
	- cannot protect against internal attackers
	- malware which came in through applications
	- secured/tunneling connections (IPsec, SSH, TLS)
5. **Which other terms are used for network layer firewalls?**
	- packet filters
6. **Explain briefly the operation of network layer firewalls.**
	- checking of header entries (L2, L3, L4), has to reassembling fragmented packages to analyse all headers
7. **Which protocol header fields are usually evaluated by a packet filter?**
	- L2 (MAC): source/destination, ethertype (`0x0800` IPv4, `0x0806` ARP, `0x086DD` IPv6, `0x8100` VLAN), tag protocol identifier (VLAN 802.1Q) 
	- L3 (IP): source/destination, protocol/next header (`1` ICMP, `6` TCP, `17` UDP)
	- L3 (ICMP): control messages (`0/0` Echo Reply, `3/X` Destination unreachable, `8/0` Echo Request, `11/X` Time Exceeded)
	- L4 (TCP): source/destination port, sequence number, connection establishment (`SYN`, `SYN-ACK`, `ACK`, `FIN`, `RST`, ...)
	- L4 (UDP): source port/destination
8. **What is a stateful inspection firewall?**
	- Recording state information of connections and modify filter rules dynamically to accept expected answer packets
9. **What is meant by "deep inspection"?**
	- do stateful packet inspection (SPI) by analyzing and modifying the application layer content $\rightarrow$ no only inspecting basic header fields, inspecting actual data payload. important for identifying malware or application-layer attacks
10. **What are the features of a "Next Generation Firewall"?**
	- can apply configuration modifications without interruptions
	- has an integrated IPS
	- provide application intelligence
	- can consider external sources in rules (e.g. allow-/blocklists of IP addresses)
11. **Explain the term "Unified Threat Management UTM"**
	- Can perform multiple security functions within one single appliance:
		- firewall
		- IDS/IPS
		- antivirus
		- anti-spam
		- content-filtering
		- VPN
12. **What's the intention of threat protection firewalls? How do they work?**
	- Enhancement of Next Generation Firewall
	- Can detect malicious content/code (executing content in sandbox environment, behavioral analysis)
	- Protection against APTs
13. **What's an advanced persistent threat (APT)?**
	- An Advanced Persistent Threat (APT) is a highly sophisticated and targeted cyberattack in which malicious actors gain unauthorized access to a network or system and remain undetected for an extended period. APTs are characterized by their persistence, often involving well-funded and organized attackers, making them difficult to detect and mitigate.
14. **What is an application layer firewall? How does it work?**
	- Unpack an analyze the content of the application layer protocol
	- act as a relay station or proxy between sender and recipient
	- allow authentication and authorization on user level
	- referred to as application layer gateway, proxy server, application firewall
15. **How do proxy servers work, what are non-/transparent proxy servers?**
	- MITM for protocol specific traffic (HTTP, DNS, ...)
	- *Non-Transparent proxy servers*: sender must send the packets directly to the proxy server, configuration inside the application/host system
	-  *Transparent proxy servers*: transparent for client, no configuration needed
16. **What are "Web Application Firewalls" for?**
	- special case of an application layer firewall
	- protect web applications against attacks over HTTP/S (Injection, tampering, cookie poisoning, buffer overflow attack, unauthorized access)
17. **Which basic firewall architectures do you know?**
	- Screened Host: Access from Internet only to services on one host. Host has access to intranet (be aware!)
	- Screened Subnet: Firewall $\leftrightarrow$ Host $\leftrightarrow$ Firewall $\leftarrow$ Internet access (additional firewall before Intranet)
	- Dual Homed Host: "all in one" firewall instead of two firewalls
	- Tri- & Multi Homed Host: multiple network zones with one firewall (DMZ)
18. **What are scurity zones?**
	 - **Security Zones** are segments within a network infrastructure that have distinct levels of security controls. They separate and manage access between different parts of the network based on security requirements. Common examples include public-facing areas (like DMZs), internal networks, sensitive data zones, and isolated environments for critical systems.
19. **You enable the access to an internal web server through your home router / firewall via port forwarding. Which firewall architecture corresponds to this setup? What dangers does it offer?**
     - **Setup**: Dual Homed Host (with an "all in one" firewall)
     - **Architecture**: This setup typically corresponds to a Packet-Filtering Firewall architecture.
     - **Dangers**:
	    - Exposes the internal server to the Internet, potentially to malicious traffic.
	    - If the server has vulnerabilities, it can be exploited.
	    - Increases the risk of attacks like port scanning, brute force, or exploiting server-specific vulnerabilities.
	    - If an attack can gain access to the host, it also has access to the internal network
20. **What are advantages/disadvantages of a IDS/IPS?**
    - **Advantages**:
	    - Detect and potentially prevent a wide range of attacks.
	    - Provide visibility into network traffic patterns.
	    - IDS can alert on suspicious activities without affecting network performance.
	- **Disadvantages**:
	    - False positives/negatives can occur, leading to unnecessary alerts or missed threats.
	    - IPS can inadvertently block legitimate traffic.
	    - Require regular updates and management to stay effective against new threats.
	    - can have a negative impact on system performance and stability
21. **Explain the term "endpoint security"**
    - Refers to securing endpoints or entry points of end-user devices like desktops, laptops, and mobile devices from being exploited by malicious actors. It involves technologies, processes, and strategies to protect devices connected to the corporate network.
22. **What's the function of an SIEM?**
    - Provide real-time analysis of security alerts generated by applications and network hardware. They aggregate and analyze log data, providing centralized reporting and alerting on security incidents, thereby aiding in incident detection and response.
23. **Explain the "Zero Trust" approach to improve network security**
    - Security concept centered on the belief that organizations should not automatically trust anything inside or outside its perimeters. Instead, they must verify anything and everything trying to connect to its systems before granting access. It involves continuous authentication, least-privilege access, micro-segmentation of networks, and prevents unauthorized access to data and services. All data sources and services are considered resources on which access is granted on a per-session basis.

### Topic 5: Linux firewall (netfilter / iptables / nftables)

1. **Explain the structure of "netfilter (-hooks)"**
	- Netfilter is a framework provided by the Linux kernel that allows various networking-related operations to be implemented in the form of customized handlers. Netfilter hooks are specific points in the network stack where these handlers can be registered to filter and modify network packets.
2. **Which are the predefined rule chains of "netfilter" / "iptables"?**
	- **INPUT**: Manages incoming packets destined for the local system.
	- **FORWARD**: Handles packets being routed through the system.
	- **OUTPUT**: Deals with packets generated by the system and going out.
	- **PREROUTING**: Used for altering incoming packets before routing.
	- **POSTROUTING**: Applied to packets as they are about to leave the system.
3. **Can you draw a schema of the rule chains in the filter table? Where do they have an effect?**
	- The filter table has following built-in chains: INPUT, FILTER, OUTPUT
4. **What is the "nat" table of "netfilter" / "iptables" for?**
	The "nat" table in iptables is used for network address translation (NAT). It primarily handles the modification of source or destination addresses of packets as they pass through the system (SNAT, DNAT)
5. **Which predefined rule chains belong to the "nat" table?**
	- PRE-ROUTING, OUTPUT, POST-ROUTING
6. **What is the structure of a rule in an "iptables" chain?**
	- one or multiple **criteria/matches for a traversing packet** (e.g. source/destination IP address and ports, protocol type, interface name, ...)
	- one **action/target** (ACCEPT, DROP, QUEUE, RETURN, user chain, ...)
7. **What happens, if a rule matches/does not match a packet?**
	- if the packet does not match the criteria's, the next rule in the chain is examined
	- At the end of the chain, the default policy of the chain is applied
8. **Which predefined targets are known with "iptables" and what do they do?**
	- `ACCEPT`: packet is let through (no further processing of the following rules)
	- `DROP`: packet is dropped (no further processing of the following rules)
	- `QUEUE`: packet is passed to the user space
	- `RETURN`: means stop traversing this chain and resume at the next rule in the previous/calling chain
	- call of a user-defined chain
	- iptables can use extended target modules (e.g. `AUDIT`, `DNAT`, `CT`, ...)
9. **Do you know some "match/target extensions" and their work?**
	- `AUDIT`: creates audit records for packets hitting the target. It can be used to record accepted, dropped, and rejected packets.
	- `CT`: The CT target sets parameters for a packet or its associated connection. Used for stateful filtering.
	- `SNAT`: Alters the source address of packets, used for Source NAT.
10. **What is the purpose of the match extension "state"/"conntrack" of iptables?**
	- filter packets based on their connection tracking status:
11. **What states of connections can be checked by iptables using the match extension "conntrack"?**
	- `NEW`: the packet has started a new connection
	- `ESTABLISHED`: the packet is associated with an established connection, both directions
	- `RELATED`: new connection created as a result of an associated connection (e.g. FTP data connection)
	- `INVALID`: the packet is associated with no known connection
	- `SNAT`: virtual state, matching if the original source address differs from the reply destination
	- `DNAT`: virtual state, matching if the original destination differs from the reply source
	- ...
12. **How can packets be marked for further processing?**
	- Packets in iptables can be marked for further processing using the "MARK" target extension.
	- This extension sets a mark value on a packet, which is a form of metadata that does not alter the packet content itself. This mark can then be used by other parts of the network stack, like routing decisions (with iproute2, for instance)
13. **Which kind of processing can be done?**
	- Routing Decisions
	- Quality of Service (QoS) and Traffic Control
	- Further Filtering or Modification
	- Logging and Monitoring
14. **Explain presented iptables/nftables rules or rule chains.**
	- see [[iptables utility]] and [[nftables utility#Examples|nftables examples]]
15. **Why is "nftables" more flexible then "iptables"?**
	- unified framework `nft`
	- simplified and cleaner syntax
	- tables and chains are fully configurable
	- no distinction between matches and targets anymore $\rightarrow$ several actions in one single rule can be specified
	- efficient rule processing
16. **What are the main differences between "nftables" and "iptables"?**
	- unified framework `nft` instead of `iptable`, `ip6tables`, `ethertables`, ...
	- nftables uses a new syntax
	- nftables has advanced features like native sets, maps
	- nftables integrates connection tracking more seamlessly
	- nftables offers a compatibility layer for iptables
17. **What happens with my "iptables"-rules if "nftables" is deployed?**
	- there is a compatibility layer, allowing iptables command to be translated into nftables rules
	- iptables rules can be converted to the nftables syntax
18. **Explain what the presented "nftables" firewall does (e.g., lab sample solutions).**
	- see [[nftables utility#Examples|nftables examples]] and [[Lab 3 - Firewalls, Proxies, IDS]]

### Topic 6: DNSSEC and DNS privacy

1. **Why is DNSSEC used? What problem does it solve?**
     - DNSSEC (Domain Name System Security Extensions) is used to protect against DNS spoofing or cache poisoning attacks. It ensures the integrity and authenticity of DNS responses, confirming they haven't been tampered with during transit.
2. **What is the purpose and function of a validating resolver?**
     - A Validating Resolver checks the authenticity of DNS responses using DNSSEC. It validates the digital signatures in DNSSEC-protected DNS data to ensure the data's integrity and authenticity.
3. **What are the new DNSSEC Resource Records? What are they for?**
     - **RRSIG**: Contains a digital signature that verifies a record set's authenticity.
     - **DNSKEY**: Holds the public key used in the DNSSEC validation process.
     - **DS (Delegation Signer)**: Holds the hash of a DNSKEY record, used in the chain of trust.
     - **NSEC** and NSEC3: Lists the next record in the zone, used to prove non-existence of a record.
     - **CDNSKEY** and CDS: For a child zone requesting updates to DS record(s) in the parent zone
4. **What is the purpose of the RRSIG/DNSKEY/NSEC/DS RR? Explain how they work.**
     - See above or [[DNSSEC]]
5. **What is a Resource Record Set (RRSet) and where is it used?**
     - An RRSet is a set of DNS records with the same name, class, and type. It's used in DNSSEC to group records for signing purposes.
6. **What problem is caused by the NSEC RR? How can it be solved?**
     - NSEC records can inadvertently reveal all valid names in a zone, leading to zone walking, where an attacker discovers all subdomains. NSEC3 addresses this by hashing record names, obscuring them from attackers.
7. **What is the purpose of the Zone Signing Key ZSK?**
     - The ZSK is used to sign DNS record sets (RRSets) within a zone. It's a cryptographic key that generates a signature, which is verified against the DNSKEY record in the zone.
8. **What is the purpose of the Key Signing Key KSK?**
     - The KSK is used to sign the DNSKEY record itself, providing a layer of trust and security. It's generally used less frequently and is more heavily protected than the ZSK.
9. **How are DNS entries validated on a validating resolver?**
     - A validating resolver uses DNSSEC to validate DNS entries by checking the digital signature in the RRSIG record against the corresponding DNSKEY. If the signature is valid, the data is considered authentic.
10. **How does the Chain of Trust for DNSSEC work?**
      - The Chain of Trust starts from a trusted root (like the root DNS servers) and extends downwards. Each level of DNS hierarchy signs the keys of the level below it, creating a trust path from the root to the queried DNS record.
11. **What response does a client receive if the resolver used cannot validate a response?**
      - If a validating resolver cannot validate a DNS response, it generally returns a SERVFAIL error, indicating the validation failure.
12. **What is the purpose of the AD or the CD flag in the DNS protocol header?**
      - An inquired name server can indicate the successful authentication of the DNS data using the AD-bit. The AD-bit is controlled by a name server.
      - The CD-bit is set in a query to indicate, that no DNS authentication should be made by the inquired name server i.e., the questioner is able, to do the authentication itself. The CD-bit is controlled by the resolver.
13. **Explain use cases for DNSSEC such as SSHFP or DANE?**
      - SSHFP: Securely publish SSH fingerprints in DNS, allowing clients to verify the identity of SSH servers.
      - DANE (DNS-Based Authentication of Named Entities): Uses DNSSEC to secure information about where to find secure services like TLS certificates.
14. **Do you know methods to improve the confidentiality and privacy of DNS communication?**
      - DNS-over-HTTPS (DoH) and DNS-over-TLS (DoT) are methods to encrypt DNS queries, enhancing confidentiality and privacy.
15. **Explain mechanisms/protocols that ensure the confidentiality of DNS transactions.**
      - TLS and HTTPS
16. **How can DoT be implemented on a DNS resolver (which does not support it natively)?** 
      - For resolvers not natively supporting DoT, you can set up a proxy service that accepts DNS queries and forwards them over TLS to a DoT-supporting DNS server. This requires additional configuration and potentially third-party software.

### Topic 7: DNS RPZ

1. **What is a Response Policy Zone (RPZ) and how does it work?**
     - RPZ is a DNS feature that allows a DNS server to alter DNS responses based on policies. It functions by using specially crafted DNS zone files that define certain actions for given DNS queries. When the DNS resolver receives a query, it checks the RPZ: if there's a match, the response is modified according to the policy defined in the RPZ.
2. **What do you use RPZs for?**
     - Blocking Malicious Sites, Content Filtering, Redirecting Traffic, Phishing Protection
3. **How do you get valuable RPZ information?**
     - Subscription Services, Community-Based lists or custom policies based on your own monitoring
4. **What responses can a resolving name server respond to a client out of a RPZ?**
     - **PASSTHRU:** Do nothing (allow-list).
     - **DROP:** No response (block-list).
     - **TCP-Only:** Please try again with TCP.
     - **NXDOMAIN:** Domain does not exist / block access.
     - **NODATA:** Empty response.
     - **Local Data:** An ordinary DNS record set that can be used to answer queries, often for redirections to a safer page or information site (walled garden).
5. **How can you block/redirect access to "badhost.baddom.com" using RPZ?**
     -  **Blocking:** Add a QNAME trigger in the RPZ zone file that specifies "badhost.baddom.com". Set the action to NXDOMAIN or DROP to block access.
     - **Redirecting:** Specify "badhost.baddom.com" in the RPZ zone file and associate it with the IP address of a safe server or a warning page. When a DNS query matches this rule, the DNS server will respond with the IP address of the redirect target instead of the actual IP address of "badhost.baddom.com".

### Topic 8: Tools

1. **Why is a centralized logging important? How can it be done?**
     - Centralized logging is important for consolidating log data from multiple systems into a single location, which simplifies management, analysis, and monitoring. This aids in detecting security incidents, troubleshooting issues, and ensuring compliance with various standards. Centralized logging can be achieved using protocols like syslog, which allow devices and servers to send their log files to a centralized log management system for aggregation and analysis.
2. **What is a syslog facility and a syslog severity?**
     - **Facility**: Indicates the subsystem or application that generated the message (e.g., kernel, mail system).
     - **Severity**: Represents the priority level of the message, ranging from emergency (highest priority) to debug (lowest priority).
3. **Which tools can you use to capture traffic?**
     - TCPDUMP, Wireshark (Tshark), WinPcap/Npcap, Microsoft Network Monitor, Azure Network Watcher
4. **How do vulnerability scanners work? Can they find every vulnerable system?**
     - Vulnerability scanners are software tools that find security weaknesses in computer systems, networks, and applications. They work by scanning, probing, and checking for known vulnerabilities in target systems. However, they may not find every vulnerability and can sometimes produce false results. Scanners generate reports for analysis and prioritization, helping organizations address security issues.
5. **What is nmap for? What is a stealth scan?**
     - Nmap is a versatile network scanning tool used for finding devices and assessing their security. It allows network-wide ping sweep, port, OS detection scans  
     - A "stealth scan" in Nmap is a method that attempts to scan a network discreetly to gather information without triggering security alarms or intrusion detection systems. It's useful for reconnaissance while avoiding detection.
6. **What is "netflow" or "IPFIX"? How does it work and why is it an important mean to rise host and network security?**
     - "NetFlow" and "IPFIX" (IP Flow Information Export) are protocols used for monitoring and analyzing network traffic. They work by collecting metadata about the packets flowing through a network device like a router or a switch.
     - **How They Work:**
	     - **NetFlow:** Developed by Cisco, it collects information about IP traffic entering and leaving network interfaces. Key elements include source/destination IP, source/destination ports, protocols, and class of service. NetFlow typically operates in three stages: flow data capture, flow data export, and data analysis.
	     - **IPFIX:** An IETF standard derived from NetFlow v9. It's designed to be a universal standard for exporting flow information. IPFIX allows for more flexible and extensible means of flow information collection and is interoperable across different vendors.
     - **Importance for Host and Network Security:**
	     - **Traffic Analysis:** By analyzing flow data, anomalies or unusual patterns indicative of security threats like DDoS attacks, network scans, or data exfiltration can be detected.
	     - **Volume Metrics:** Helps in identifying spikes in traffic that could signal a security breach.
	     - **Trend Analysis:** Over time, NetFlow/IPFIX data can be used to establish a baseline of "normal" network behavior, making it easier to spot deviations.
	     - **Forensic Analysis:** In the event of a security incident, historical NetFlow/IPFIX data can help in tracing the source and understanding the nature of the attack.
	     - **Capacity Planning:** Helps in ensuring network resources are sufficient and not compromised by malicious activities.
7. **Explain an ARP MITM attack. What are countermeasures?**
     1. **Client E** sends to **Client A** "**Client B** can be found @ my MAC address"
     2. **Client E** sends to **Client B** "**Client A** can be found @ my MAC address"
     - All traffic between A and B are redirected to E. E is the MITM (man-in-the-middle)
     - Countermeasures: Static ARP entries, DHCP snooping and enforcement, passive sniffing/monitoring, reverse ARP (RARP)
8. **What is the purpose of "arpwatch"?**
     - Tracks ARP activity on a network. It helps detect and alert administrators about unexpected or potentially malicious changes in the mapping of IP addresses to MAC addresses, aiding in network security and troubleshooting.
9. **Why and when is SNMP dangerous?**
     - Wrongly configured network devices can be queried and/or reconfigured using SNMP attacks. E.g snmpwalk can find out different attributes of the device. 
10. **How do you capture packets of a DNS request / response on Interface "eth0" using "tcpdump"?**
    - Run this command: `sudo tcpdump -i eth0 port 53`
	- This command captures DNS traffic on port 53 while displaying minimal information.

### Topic 9: Lab Exercises

1. **How can a centralized syslog be implemented?**
	  - A centralized syslog can be implemented using a syslog server that collects logs from multiple devices. Syslog clients on these devices are configured to send their log data to this central server. This centralization aids in efficient log management, monitoring, and analysis.
1. **Explain how you tested arp spoofing, did it work?**
     - ARP spoofing was tested by creating false ARP messages and observing the redirection of network traffic. By associating the attacker's MAC address with the IP address of another host (like a gateway), all traffic meant for that IP was redirected to the attacker, confirming the success of the ARP spoofing.
3. **What does a specific "iptables" or "nftables" firewall rule do (see also the provided sample solutions)?**
     - Each rule in "iptables" or "nftables" specifies conditions for packet matching and decides what action to take when a packet matches these conditions. For example, a rule can be set to drop packets from a specific IP address, effectively blocking access.
4. **How do you redirect traffic to a filtering proxy using "iptables" or "nftables"?**
     - In "iptables" or "nftables", you can redirect traffic to a proxy server by setting up NAT (Network Address Translation) rules that reroute incoming or outgoing traffic to the proxy's IP address and port. This is commonly used for web filtering or caching.
5. **Which criteria did you use for your filtering proxy?**
     - For Squid, criteria can include URL patterns, IP addresses, or protocols. For example, you might configure Squid to block all access to certain websites or to only allow browsing during specific hours.
6. **Which means do you know to explore networks?**
     - Network exploration can be done using tools like Nmap for port scanning, Wireshark for packet analysis, traceroute for path tracking, and network mapping tools that visualize network topology.
7. **Which vulnerability scanner was used in the lab exercises?**
     - In the lab, Greenbone OpenVAS was used. It's a comprehensive vulnerability scanning tool that helps in identifying vulnerabilities in network services and software.
8. **What data of your router can you analyze using "nfsen"?**
     - "nfsen" allows you to analyze network flow data from your router. It can display traffic patterns, bandwidth usage, and type of traffic (e.g., HTTP, FTP) over time, aiding in network monitoring and troubleshooting.
9. **What is "softflowd" and how can it be used to export flow data?**
    - "softflowd" is a flow-based network traffic analyzer. It can be used to export flow data from network interfaces, tracking various aspects of traffic like source/destination IP, ports, and protocols.
10. **Explain how "softflowd" and "nfcap/nfsen" interact.**
	  - "softflowd" captures flow data from network traffic and exports it in a format compatible with "nfcapd", a collector component of "nfsen". "nfsen" then uses this data for analysis, visualization, and reporting.
11. **Which security distributions where used in the lab? Explain their main focus.**
	  - Kali Linux was used, which is a distribution designed for digital forensics and penetration testing. It comes with numerous tools for network analysis, vulnerability scanning, and security auditing. Its main focus is to provide a comprehensive suite for cybersecurity professionals to test network defenses and security measures.

## Part 2

### Topic 10: TLS

1. **Name 5 protocols based on TLS.**
	- HTTPS, FTPS, SMTPS, LDAPS, DTLS
2. **What is meant with «Opportunistic TLS»? What is meant with «implicit TLS»? What kind of risks / attacks do you know?**
	- Opportunistic TLS: Refers to a system that uses TLS encryption if available but can fall back to an unencrypted connection if TLS isn’t supported by the other party. It's often used in email transmission. The risk is that it can be subject to downgrade attacks, where an attacker forces the connection to revert to an unencrypted state.
	- Implicit TLS: In this mode, TLS is a mandatory part of the connection from the start (as opposed to being negotiated with STARTTLS). The connection starts with the TLS handshake, and no unencrypted communication is permitted. It is considered more secure than opportunistic TLS as it doesn’t allow falling back to an unencrypted connection.
3. **What does «HTTP Strict Transport Security» (HSTS) stands for? How is it supposed to work? Describe the OSI layer in general and where the TLS communication takes place.**
	- HSTS is a web security policy mechanism that helps to protect websites against protocol downgrade attacks and cookie hijacking. It allows web servers to declare that web browsers (or other complying user agents) should only interact with it using secure HTTPS connections, and never via the insecure HTTP protocol.
	- In the OSI model, HSTS operates at the application layer (Layer 7), where it instructs the browser on how to handle connections to the server. The TLS communication itself occurs at the session layer (Layer 5) and the presentation layer (Layer 6), where it provides privacy and data integrity between two communicating applications.
4. **TLS is composed of the handshake protocol and the record protocol. Describe what happens on each layer?**
	- Handshake Protocol: This part of TLS is responsible for the initial negotiation between client and server. It establishes which cryptographic algorithms will be used, authenticates the server (and optionally the client), and sets up a secure encryption key.
	- Record Protocol: Once the handshake is complete, the Record Protocol is used to secure the actual data being transmitted. It uses the encryption key established during the handshake to encrypt the data and ensures that it is transmitted securely and intact.
5. **What information do we find in a «Client Hello» message?**
	- Protocol Version: The highest TLS version supported by the client.
	- Random: A client-generated random string used for key generation.
	- Session ID: An identifier to resume previous sessions for faster handshakes.
	- Cipher Suites: A list of cryptographic algorithms supported by the client.
	- Compression Methods: Information about the compression methods available.
	- Extensions: Optional additional features like server name indication (SNI) or maximum segment size.
6. **What information contains the CipherSuite such as TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 (128-bit AES encryption with SHA-256 message authentication and ephemeral ECDH key exchange signed with an RSA certificate)?**
	- TLS: Indicates the protocol is TLS.
	- ECDHE (Elliptic Curve Diffie-Hellman Ephemeral): Specifies the key exchange mechanism using ephemeral keys with Elliptic Curve cryptography for secure key agreement.
	- RSA: Indicates the use of RSA for digital signatures and certificate verification.
	- AES_128_CBC: Specifies the encryption algorithm (AES) with a 128-bit key size, using Cipher Block Chaining (CBC) mode.
	- SHA256: Indicates the use of the SHA-256 algorithm for message authentication and integrity verification.
7. **How does a TLS mutual authentication works? Which additional handshake messages are exchanged?**
	- In TLS mutual authentication, both client and server authenticate each other. This is usually done in environments where security requirements are higher.
	- Additional Handshake Messages: In addition to the standard TLS handshake messages, both the client and server present certificates. After the server sends its certificate, the server requests the client's certificate (CertificateRequest), and the client responds with its certificate (Certificate). The client then sends a CertificateVerify message to prove ownership of the private key associated with the certificate.
8. **How does a TLS resume session looks like. What are the prerequisites? What is a anonymous TLS session such as TLS_ECDH_anon?**
	 - TLS session resumption is a mechanism to speed up repeated TLS connections between the same client and server. Prerequisites: A previously established TLS session with agreed-upon session keys and a session ID or session ticket. In a resumed session, the client and server use the session ID or session ticket from a previous session to skip the full handshake and quickly re-establish encryption keys. Anonymous TLS Session (e.g., TLS_ECDH_anon): These are TLS sessions that do not authenticate one or both parties. They use ECDH for key exchange without RSA or other certificate-based methods. These sessions are vulnerable to man-in-the-middle attacks as they lack authentication.
9. **What does the term Forward Secrecy stands for. What has to be done to get perfect forward secrecy (PFS)?**
	- Forward Secrecy (FS), or Perfect Forward Secrecy (PFS), refers to a property of secure communication protocols where session keys cannot be compromised even if the private key of the server is compromised in the future.
	- Achieving PFS: This is typically done by using ephemeral key exchange mechanisms (like Diffie-Hellman or ECDHE) where a new key pair is generated for each session and not based on a static server key.
10. **What do you have to do respectively think off to implement a TLS reverse proxy for a company?**
    - Certificate Management for the proxy, protocol and cipher configurations for TLS, secure communication between the proxy and internal servers, logging and monitoring and compliance and policy enforcement.
11. **What is a bit flipping attack? Which ciphers are vulnerable?**
    - A bit flipping attack is a form of cryptographic attack where the attacker changes bits in the encrypted message in a predictable way to manipulate the decrypted plaintext. This type of attack is typically used against cipher modes like CBC (Cipher Block Chaining) where alterations in one block can predictably affect the decryption of subsequent blocks.
    - Ciphers Vulnerable: Cipher modes that do not authenticate message integrity, such as CBC, are particularly vulnerable to this attack. This vulnerability led to the development of authenticated encryption modes like GCM (Galois/Counter Mode) that combine encryption and message authentication.
12. **What information do you need to inspect and decipher all TLS packets e.g. with wireshark (TLS private key corresponding to the server certificate, pre-master key, master key)?**
    - If using traditional RSA key exchange, having the server's private key allows you to decrypt the session. For sessions using Diffie-Hellman key exchange, you need the pre-master key or master key, as these sessions cannot be decrypted using just the server's private key.
13. **What information is exchanged with Diffie-Hellman key exchange in a TLS session? Describe which information is used for a JA3 fingerprint?**
    - This exchange involves each party sending a public value (computed from their private value and a common base) and then combining their private value with the received public value to compute a shared secret. JA3 Fingerprint: It's a method to fingerprint SSL/TLS clients based on specific details of their TLS handshake process. This includes the TLS version, accepted cipher suites, list of extensions, elliptic curves, and elliptic curve point formats.
14. **How is the master secret derived for the pre-master secret?**
    - In a TLS handshake, the master secret is derived from the pre-master secret through a secure hashing process. This involves using a pseudo-random function (PRF) that combines the pre-master secret with nonces (random numbers) from both client and server, plus a string literal. The result is a master secret that is then used to generate encryption keys, MAC (Message Authentication Code) keys, and initialization vectors.
15. **Describe how a HMAC function works.**
    - HMAC is a type of message authentication code (MAC) that uses a cryptographic hash function (like SHA-256) combined with a secret key. It works by applying the hash function in two steps: The key is combined with the message and hashed. The hash output is then combined with the key again and re-hashed. This process provides both data integrity and authentication of the message. HMAC ensures that the message has not been altered and that it was sent by a holder of the secret key.
16. **What is meant with «Authenticated Encryption» (AE)?**  
    - Authenticated Encryption refers to encryption methods that ensure both confidentiality and integrity of the data.
17. **What is the difference between AE and AEAD (Authenticated Encryption Associated Data)?** 
    - While Authenticated Encryption (AE) ensures data confidentiality and integrity, Authenticated Encryption with Associated Data (AEAD) goes a step further by also protecting additional associated data's integrity (but not its confidentiality). This associated data is typically header or other metadata.
18. **Describe a «Padding Oracle Attack».**
    - This is an attack method on cryptographic systems where the attacker makes use of a 'padding oracle' - a side channel giving them hints about whether a given decryption attempt was correct based on the padding's validity. The attacker can iteratively guess and decrypt data, exploiting the way some encryption algorithms handle padding.
19. **Describe a «Padding Oracle On DOwngradeD Legacy Encryption» (POODLE) attack.** 
    - Padding Oracle On Downgraded Legacy Encryption (POODLE) is a security vulnerability that exploits the fall-back to SSL 3.0 in TLS. When a secure connection attempt fails, a server might fall back to older protocols like SSL 3.0. POODLE can force this downgrade and then use padding oracle attacks (exploiting SSL 3.0's vulnerabilities) to decrypt sensitive data like cookies.
20. **Describe the changes between TLS 1.2 and TLS 1.3 in respect of: Key exchange, Cipher suites, Round trip time, Authenticated Encryption , Authentication / Signature**
    - Key Exchange: TLS 1.3 removes RSA key exchange for forward secrecy, focusing on Diffie-Hellman and ECDH (Elliptic Curve Diffie-Hellman) instead.
	- Cipher Suites: TLS 1.3 streamlines cipher suite negotiation, supporting only AEAD cipher suites. It removes many older cipher suites and hashing algorithms, increasing overall security.
	- Round Trip Time: TLS 1.3 reduces the number of round trips (handshake messages exchanged between client and server) needed to establish a secure connection, making the handshake process faster.
	- Authenticated Encryption: TLS 1.3 mandates the use of AEAD ciphers for encrypting and authenticating all data, ensuring better security and efficiency.
	- Authentication/Signature: TLS 1.3 improves the way certificates are authenticated and signed, requiring digital signatures even when a previous session is resumed. This enhances the overall security of the authentication process.

###  Topic 11: Certificates and PKI

1. **How can you choose a public RSA key?**
     - Public RSA keys are chosen based on a pair of large prime numbers and a modulus operation. A key generation algorithm is used, ensuring that the keys are large enough to prevent brute force attacks. The size of the key (like 2048-bit or 4096-bit) is crucial for security.
2. **In which areas are asymmetric keys used?**
     - Encryption and decryption of data
     - Digital signatures for authenticity and integrity
     - Secure key exchange (e.g., in TLS protocols)
     - Identity verification in various authentication systems
3. **How scales the key distribution process for (a) symmetric keys and (b) for asymmetric keys?**
     - (a) **Symmetric Keys**: Scaling is challenging because each pair of users needs a unique key, leading to a quadratic growth of keys with the number of users. 
     - (b) **Asymmetric Keys**: Scales better as each user needs only a public/private key pair, regardless of the number of other users they communicate with.
4. **Describe the 3 types of trust model: (a) Direct trust, (b) Web of Trust and (c) Hierarchical trust.**
     - (a) **Direct Trust**: Trust established directly between users, without intermediaries. 
     - (b) **Web of Trust**: Trust is established in a decentralized manner, users vouch for the authenticity of others' keys. 
     - (c) **Hierarchical Trust**: Involves a central authority (like a Certificate Authority in PKI) that validates identities and issues certificates.
5. **Describe the 3 types of certificates: (a) Root certificate, (b) Intermediate certificate, (c) End-entity certificate.**
     - (a) **Root Certificate**: Issued by a top-level Certificate Authority (CA); it's self-signed. 
     - (b) **Intermediate Certificate**: Issued by an intermediate CA, creating a chain of trust to the root CA. 
     - (c) **End-entity Certificate**: Issued to the final user or entity (like a website).
6. **What information contains a X509v3 certificate?**
     - Subject's name
     - Issuer's name
     - Serial number
     - Validity period
     - Public key information
     - Signature algorithm
     - Optional extensions for additional functionality
7. **What is the difference between a certificate fingerprint and TBS certificate fingerprint?**
     - The certificate fingerprint is a hash of the entire certificate, whereas the TBS (To Be Signed) certificate fingerprint is a hash of the portion of the certificate that is actually signed, excluding the signature itself.
8. **Provide some samples of trusted root certificates and where they are used.**
     - VeriSign
     - DigiCert
     - Let’s Encrypt
     - They are used in web browsers and operating systems as a trust anchor.
9. **How are X509v3 certificates encoded?**
     - They are typically encoded in DER (Distinguished Encoding Rules) format, a binary format, or sometimes in PEM (Privacy Enhanced Mail) format, which is base64 encoded DER with header and footer lines.
10. **Provide an example of a «critical certificate extension». How should «critical certificate extension» be dealt with?**
      - An example is the Basic Constraints extension in CA certificates. It indicates whether the certificate is for a CA or not. "Critical" means the extension must be understood and processed, or the certificate should be rejected.
11. **Issuers and subjects are represented as «Distinguished Names». What is a «Distinguished Name» (DN)?**
      - A DN is a string in an X.509 certificate that uniquely identifies an entity (like a person or organization) in the certificate. It includes elements like common name, organization, and country.
12. **What is the certificate extension subjectAltName used for?**
      - The subjectAltName extension is used to specify additional identities (like email addresses, IP addresses, or other domain names) associated with the entity to which the certificate is issued, beyond the common name (CN) in the DN.
13. **What is defined in PKCS#1, PKCS#7, PKCS#10, PKCS#11, PKCS#12?**
     - **PKCS#1: RSA Cryptography Specifications** Defines the mathematical properties and implementation for RSA public key cryptography. It includes specifications for encryption and signing, RSA keys, and other related cryptographic operations.
     - **PKCS#7: Cryptographic Message Syntax Standard** Specifies a general syntax for data encryption and digital signatures. It's widely used for digital certificates, in S/MIME for secure email, and in other applications requiring secure data exchange.
     - **PKCS#10: Certification Request Standard** Describes a syntax for certification requests. It is used when an entity (like a person or organization) requests a digital certificate from a Certificate Authority (CA).
     - **PKCS#11: Cryptographic Token Interface Standard** Defines a platform-independent API, called Cryptoki, for cryptographic tokens like hardware security modules (HSMs) and smart cards. It allows for integration with various cryptographic hardware to perform operations like encryption and signing.
     - **PKCS#12: Personal Information Exchange Syntax Standard** Provides a format for storing and transporting a user's private keys, certificates, and miscellaneous secrets. It's commonly used for exporting and importing a user's digital identity across different systems.
14. **What is the life cycle of a X509 certificate?**
     - **Creation and Request**
         - **Key Pair Generation:** The entity (person or organization) generates a public-private key pair.
	     - **Certificate Signing Request (CSR):** The entity creates a CSR, which includes the public key and identifying information.
     - **Validation**
         - A Certificate Authority (CA) validates the entity's identity. The depth of this validation varies (Domain Validation, Organization Validation, Extended Validation).
     - **Issuance**
	     - **Certificate Generation:** The CA signs the CSR with its private key, creating an X.509 certificate.
	     - **Distribution:** The certificate is sent to the entity.
     - **Usage**
	     - The certificate is used for its intended purposes, like SSL/TLS for web servers, email encryption, or code signing.
     - **Revocation (if necessary)**
	     - If compromised or no longer needed, the certificate can be revoked. The CA updates its Certificate Revocation List (CRL) or updates the Online Certificate Status Protocol (OCSP) database.
     - **Expiration**
	     - X.509 certificates have a predetermined validity period. After expiration, they are no longer trusted and must be renewed.
     - **Renewal (if required)**
	     - The entity must generate a new key pair and CSR, repeating the cycle if continued use is needed.
15. **What protocols do you know to check the status of a certificate (CRL-DP, OSCP)? Describe them.**
     - **CRL-DP (Certificate Revocation List Distribution Point):**
	     - **Mechanism:** CRL-DP refers to the location (usually a URL) where a Certificate Revocation List (CRL) is published by the Certificate Authority (CA).
	     - **CRL:** This list contains serial numbers of certificates that have been revoked before their scheduled expiration date.
	     - **Usage:** Clients download the CRL to check if a particular certificate is listed. If it is, the certificate is considered revoked and untrustworthy.
	     - **Drawbacks:** The main issue with CRLs is their size and the frequency of updates. As a result, downloading and parsing CRLs can be resource-intensive, especially for large organizations.
     - **OCSP (Online Certificate Status Protocol):**
	     - **Mechanism:** OCSP allows clients to query the status of a specific certificate in real-time. It operates over HTTP.
	     - **OCSP Request:** The client sends a request to the OCSP server (specified in the certificate) containing the serial number of the certificate in question.
	     - **OCSP Response:** The OCSP server checks  the status and responds with the certificate's status: valid, revoked, or unknown.
	     - **Advantages:** OCSP is more efficient than CRLs, as it doesn't require downloading a complete list and is more up-to-date.
	     - **Stapling:** To reduce OCSP lookup overhead and privacy concerns, a technique called OCSP stapling is used, where the server periodically queries the OCSP server and then "staples" the response to the TLS handshake.
16. **What is a Extended Validation SSL (EV SSL) certificate?**
     - An Extended Validation SSL (EV SSL) certificate is a type of SSL certificate offering the highest level of authentication. It involves a rigorous verification process where the issuing Certificate Authority checks the applicant's legal, operational, and physical existence. EV SSL certificates were known for providing distinct browser indicators (like a green address bar), but recent browser updates have minimized these visual distinctions. They are most suitable for entities handling sensitive transactions, offering enhanced trust and credibility.
17. **What problems are addressed with the «Certificate Transparency» (CT) standard?**
     1. **Undetected Issuance of Fraudulent Certificates:** CT helps in detecting certificates that have been mistakenly or maliciously issued by a Certificate Authority (CA).
     2. **Lack of Public Oversight:** It enables public monitoring and auditing of certificates, increasing transparency in certificate issuance.
     3. **Mitigating CA Compromise:** By making certificate issuance public, CT makes it harder for attackers to misuse a compromised CA without detection.
     - CT achieves this by requiring CAs to publicly log all issued certificates, allowing domain owners and the public to monitor and verify the certificates issued for their domains.
18. **How does CT works? Where is it implemented? Who is enforcing checks?**
     -  Certificate Transparency (CT) works by requiring Certificate Authorities (CAs) to log every SSL/TLS certificate they issue in public, append-only logs. These logs can be independently monitored and audited.
     - **Implementation:** CT is implemented in web browsers and by CAs. Browsers like Google Chrome require CT compliance for new SSL/TLS certificates to be trusted.
     - **Enforcement:** The enforcement of CT checks is primarily done by web browsers. They validate if a new certificate is logged in CT logs and may distrust certificates that are not CT-compliant. Additionally, independent monitors and auditors play a role in ensuring log integrity and detecting anomalies.
19. **Which components and processes are required for a PKI?**
	 1. **Certificate Authority (CA):** Issues digital certificates to entities (individuals, organizations, devices).
	 2. **Registration Authority (RA):** Validates the identity of entities before they receive a certificate from the CA.
	 3. **Validation Authority (VA):** The VA handles the validation of certificates, often through protocols like OCSP, serving as an intermediary between the CA and entities verifying certificate status.
	 4. **End Entities (EE):** These are the final users in the PKI, such as individuals or systems, holding and utilizing digital certificates for secure communication and transactions.
	 6. **Certificate Repositories:** Secure storage locations where issued certificates and Certificate Revocation Lists (CRLs) are kept.
	 7. **Key Management:** Processes for generating, distributing, storing, and destroying cryptographic keys.
	 8. **Certificate Lifecycle Management:** Processes for issuing, renewing, suspending, and revoking certificates.
20. **How to you generate a «Certificate Signing Request» (PKCS#10)? What attributes are checked by the RA?**
     - To generate a Certificate Signing Request (CSR) as per PKCS#10:
	 1. **Key Pair Generation:** Generate a public-private key pair using a cryptographic algorithm, typically RSA or ECC.
	 2. **Create CSR:** Using tools like OpenSSL, create the CSR. This includes:
	     - **Public Key:** Embed your public key.
	     - **Subject Name:** Include details like Common Name (CN), Organization (O), Organizational Unit (OU), Country (C), State (ST), and Locality (L).
	     - **Optional Attributes:** May include email address, domain names (SAN - Subject Alternative Name), and others.
     - The Registration Authority (RA) checks these aspects of the CSR:
         1. **Authenticity of Information:** Verifies the accuracy of the subject name and other details against official documents or databases.
         2. **Authorization:** Confirms that the entity requesting the certificate is authorized to use the domain or has the rights to the specified names.
         3. **Compliance with Policies:** Ensures that the CSR adheres to the policies of the CA, including key length, algorithm type, and usage.
21. **What are «Advanced Digital Signature» (AdES) and «Qualified Electronic Signatures» (QES). Who can issue such certificates in Switzerland?**
     - **Advanced Digital Signatures** (AdES) are electronic signatures that offer higher security levels and are compliant with specific standards like PAdES, CAdES, and XAdES. They ensure the integrity and authenticity of the signed data.
     - **Qualified Electronic Signatures** (QES) are a subset of AdES. They are legally equivalent to handwritten signatures in many jurisdictions, including the EU. QES requires a secure signature creation device and a certificate from a Qualified Trust Service Provider (QTSP).
     - In Switzerland 4 entities can issue such certificates (Schweizerische Eidgenossenschaft, Digicert, Swisscom, SwissID)

### Topic 12: Identification Authentication Authorization

1. **What is Identification, Authentication and Authorization?**
     - **Identification** is the process of claiming an identity (e.g., username).
     - **Authentication** is verifying the identity (e.g., password, biometric data).
     - **Authorization** is granting or denying permissions based on the authenticated identity (e.g., access to resources).
2. **What factors are distinguished for authentication? What is required for 2FA / MFA?**
     - **Knowledge**: Something the user knows (e.g., password, PIN).
     - **Possession**: Something the user has (e.g., token, smartphone).
     - **Inherence**: Something the user is (e.g., fingerprint, facial recognition).
     - **2FA/MFA** requires at least two different factors for authentication, enhancing security.
3. **What is meant in the PSD2 regulation with «strong authentication with linking»?**
    - In the PSD2 regulation, "strong authentication with linking" refers to the need for strong customer authentication (SCA) that dynamically links the authentication to specific transaction details, such as the amount and the payee, ensuring the security of electronic payments.
4. **What has to be met to get a high «Level of Assurance» (LoA)?**
     - To achieve a high LoA, multiple factors of authentication are typically required, along with strong mechanisms to verify identity (like government-issued IDs), secure registration and issuance processes, and robust protection against fraudulent use.
5. **What can go wrong with shared secrets? How should you store credentials used for password based authentication?**
     - They can be guessed, intercepted, or stolen. 
     - Use secure, hashed storage for credentials. Hashing (with a salt) transforms the password into a unique, irreversible hash.
6. **Describe «online» and «offline» attacks against passwords.** 
     - **Online Attacks**: Attempt to access accounts through the network (e.g., brute-force login attempts).
     - **Offline Attacks**: Access stolen data (like a database) and try to crack passwords without interacting with the system.
7. **How do you calculate the Entropy of a password?**  
     - It's calculated based on the number of possible symbols and password length. Formula: `Entropy = Log2(N^L)`, where N is the number of possible symbols, and L is the length of the password.
8. **How is the password transferred with «HTTP Basic Authentication»?** 
     - The username and password are concatenated with a colon, base64 encoded, and sent in the HTTP header. It's not encrypted, so it should always be used with HTTPS to ensure security.
9. **How does the OATH standard HOTP (HMAC-based One Time Password) works?**
     - It's based on HMAC (Hash-based Message Authentication Code) and a counter value. Each time a password is used, the counter increments, ensuring that each OTP is unique.
10. **How does the OATH standard TOTP (Time-based One Time Password) works?**
      - Similar to HOTP but uses the current time as the moving factor instead of a counter. The password changes at fixed time intervals (e.g., every 30 seconds), offering a constantly updating password.
11. **What is a Challenge-Response-Protocol and why do we need it?** 
      - A security mechanism where one party presents a question (challenge) and another party must provide a valid answer (response/signature) to be authenticated. It's used to verify the identity of a user or device, often in a way that prevents eavesdropping or replay attacks, since the challenge is typically random and changes each time. Based on public key cryptography. 
12. **FIDO2 consists of the standards WebAuthn and CTAP. Describe the function of the two standards.**
      - **WebAuthn**: A web standard for authentication. It allows users to log in to web services using biometrics, mobile devices, or FIDO security keys, instead of a password.
      - **CTAP (Client To Authenticator Protocol)**: Allows an external device (like a security key or a mobile phone) to act as an authenticator to a client device via USB, NFC, or Bluetooth.
13. **What is meant with attestation?**
      - Refers to the process where a device (like a security key) proves to a verifier (like a server) that it is what it claims to be, often by providing a certificate or signature from a trusted manufacturer or authority.
14. **What information / LoA do we get with a FIDO2 registration with a YubiKey?** 
      - The YubiKey, as a FIDO2 authenticator, provides high assurance of user identity by verifying user presence (and potentially user biometrics, depending on the model) during the registration and authentication processes.
      - There are some YubiKey with the highest possible level of LoA.
15. **What does the Relying Party (RP) need for verifying the attestation?**
      - To verify attestation, the RP needs the attestation statement from the authenticator (YubiKey), which typically includes the authenticator's public key, a signed certificate, and other metadata for verification. And to do that it needs the corresponding public key.
16. **What communication protocols are supported by CTAP? What options are displayed when resisting on a FIDO2 page with an Android device?**
      - USB, NFC and Bluetooth. When registering on a FIDO2 page, Android devices may display options to use the phone itself as an authenticator (if it supports FIDO2) or to connect an external authenticator via USB, NFC, or Bluetooth.
17. **What is needed to access resources over OAuth from a «Resource Server»?**
      - The client needs an access token from the authentication server. This token is then presented to the resource server to access the resources on behalf of the resource owner (user).
18. **What is a «bearer token»?**
      - A bearer token is a type of access token that allows the holder of the token to access resources without additional proof of identity. It is assumed that whoever possesses the token has the right to use it.
19. **Describe the trust relations between the 4 parties: resource holder, client, authentication server and resource server.**
      - The **Client** trusts the **Auth Server** to authenticate users and issue tokens.
      - The **Resource Holder** trusts the **Auth Server** to securely authenticate and not misuse credentials.
      - The **Resource Server** trusts the **Auth Server** to correctly validate users and trusts the token for access control.
      - The **Resource Holder** must also trust the **Client** to act on their behalf appropriately.
20. **What kind of CSRF attack would be possible if the client would not check the session state?**
      - If the client doesn't check the session state, a CSRF attack could trick a user into unknowingly executing an action on a different site where they are authenticated. For example, an attacker could forge a request to transfer money or change settings in the context of the user's session on a banking site. Checking the session state helps ensure that the request is made intentionally by the user and not by an attacker.
21. **How can a resource holder revoke his consent?**
      - A resource holder can revoke their consent, typically through the service that originally granted it. Most platforms have a security or privacy settings page where users can view and manage their consent to third-party applications. Here, they can revoke access rights previously granted to applications or services.
22. **Outline how you can use «OpenID Connect» as authentication layer. What is the benefit. How are the trust relations?**
      - Just read it [[OAuth#OpenID Connect|here]]
23. **Outline how you can leverage OAuth as Identity Provider interface.**
      - OAuth can be used to facilitate identity management by allowing a client to request access to resources controlled by the resource owner but hosted by a resource server. The identity provider, in this case, would authenticate the resource owner and issue tokens that the client can use to access the resources.
24. **On what security mechanism is OAuth relying on?**
      - OAuth relies on tokens for security. The tokens are used instead of credentials for accessing resources, thus providing a layer of abstraction that enhances security by not exposing user credentials to clients. OAuth also uses SSL/TLS for secure communication between all parties involved.

### Topic 12.5: Kerberos

1. **How does Kerberos works? Why does Kerberos need shared secrets? What are these shared secrets?**
     - Kerberos is a network authentication protocol that works on the basis of tickets to allow nodes to prove their identity securely over a non-secure network. Kerberos needs shared secrets for secure communication between the client and the server. These are typically passwords or keys known both to the user's client and the Kerberos server.
2. **The Key Distribution Center (KDC) is composed of the Authentication Server (AS) and the Ticket Granting Server (TGS). What is the function of AS and TGS?**
     - **Authentication Server (AS)**: Issues an initial ticket (TGT) after authenticating the user.
     - **Ticket Granting Server (TGS)**: Uses the TGT to grant service tickets, which allow access to other network services.
3. **What is a Server Principal Name (SPN)? How is the name composed / structured?**
     - A unique identifier for a service instance on the network. Usually structured as `service/hostname:port`, indicating the service and the host providing it.
4. **Explain the content and the function of Kerberos Tickets? What is a Ticket Granting Ticket (TGT) and what is a service ticket (ST)? Explain the differences.**
     - **Ticket Granting Ticket (TGT)**: Issued by the AS, used to obtain service tickets from the TGT without re-authenticating.
     - **Service Ticket (ST)**: Allows access to a specific service; issued by the TGT.
     - **Differences**: TGT is for obtaining STs, while STs are for accessing specific services.
5. **Explain the differences between «secret keys» and «session keys».**
     - **Secret Keys**: Long-term keys derived from a user's password, used for initial authentication.
     - **Session Keys**: Temporary, used for the duration of a session to encrypt communication between client and server.
6. **How does the Kerberos Pre-authentication works?**
     - Involves proving the user's identity before a TGT is issued, typically by encrypting a timestamp using the user's secret key (hash of the password).
7. **What is needed to decrypt all messages / tickets in Wireshark?**
     - Secret key and session key
8. **What type of attacks are referred as «Golden Ticket» «Silver Ticket» attack? What can you do with a «Golden Ticket» or «Silver Ticket»?**
      - Golden Ticket Attack: Involves creating a TGT with administrative rights. With this, an attacker can access any service on the network.
      - Silver Ticket Attack: Involves creating a service ticket for specific services. It's more limited than a Golden Ticket but harder to detect.
9. **What has to be done if an attacker gained a «Golden Ticket»?** 
     - Resetting the krbtgt account's password twice (to invalidate old tickets) and resetting passwords for all accounts, as well as investigating the breach, are critical steps to mitigate a Golden Ticket attack.
10. **Describe Kerberos delegation. What does it mean. Where is it used?**
      -  Kerberos delegation allows a service to use the client's credentials to access other services on the client's behalf.
      - Common in scenarios where a middle-tier service needs to access resources on behalf of a user, like a web application accessing a database.
11. **What is the difference between «unconstrained», «constrained» and «resource-based constrained» Delegation.**
      - Unconstrained Delegation: A service can request access to any other service on behalf of the user using the user's TGT.
      - Constrained Delegation: Specific services are pre-defined for delegation. A service can request access only to these specified services on behalf of the user.
      - Resource-Based Constrained Delegation: Services to which delegation is allowed are defined on the target service side, not on the user or delegating service's account.
12. **Can the user prevent delegation?**  
      - Users themselves typically cannot prevent delegation in Kerberos. It's controlled by domain administrators through service configurations and account properties.
13. **Can you restrict delegation. Where does it makes sense to restrict delegation?**
      -  Delegation can be restricted at the domain level by configuring service accounts -> Add users to protected group or flag as sensitive
      - It makes sense to restrict delegation in high-security environments or for services that handle sensitive data to limit the potential for privilege escalation or lateral movement.
14. **What are the security risks? Describe how «unconstrained» delegation could be misused.**  
      - Unconstrained delegation can be misused if an attacker compromises a service account with delegation privileges. An attacker can impersonate users to any service for which the service account holds TGTs
15. **How can you trick users to connect to your service configured for delegation?** 
      - An attacker might set up a service configured for delegation and then use techniques like phishing or DNS spoofing to trick users into connecting to this service, allowing the attacker to impersonate these users.
16. **How could a printer on a DC be attacked?**  
      - Abuse of MS-RPRN: PrinterBug refers to the exploitation of Microsoft's Print System Remote Protocol (MS-RPRN), particularly the Print Spooler service, which is exposed to the network to manage print jobs and related tasks.
      - Forced Connections via RPC Calls: By making Remote Procedure Call (RPC) requests to the Print Spooler service, an attacker can force a target system to establish connections to arbitrary hosts.
      - Authentication Over SMB: The authentication resulting from this forced connection is performed over SMB (Server Message Block) and can use NTLM (NT LAN Manager) or Kerberos protocols​​.
      - If that arbitrary host uses unconstrained delegation the TGT of the DC machine account can be abused for DCSync attack.
17. **What mitigation measurements do you know to secure Kerberos?** 
     - Regularly change and protect the krbtgt account password.
     - Limit and monitor the use of service accounts with delegation rights.
     - Employ strong, unique passwords for all accounts.
     - Keep systems patched and up-to-date.
     - Monitor and audit Kerberos authentication logs for suspicious activity.
18. **How does an attack against «constrained» delegation looks like?**  
      - An attacker would first need to compromise a service account with constrained delegation rights. Then, they could impersonate users but only to the services specified in the constrained delegation setup.
19. **What is meant with «protocol transition»? How does it work?** 
      - **Purpose**: Protocol transition is intended to bridge different authentication protocols to Kerberos. It allows a service to request a Kerberos service ticket on behalf of a user who has authenticated using a non-Kerberos method.
      - **Functioning**: In this process, the delegation service (the service requesting a ticket on behalf of the user) can essentially create the proof of the user's presence itself. This means that the initial authentication of the user (which typically happens through Kerberos) is not actually required for the delegation service to obtain a Kerberos ticket in the user's name.
      - **Implications**: This ability to impersonate users without their direct Kerberos authentication poses significant security considerations. For instance, enabling constrained delegation with protocol transition gives an account additional privileges, marked by the User Account Control (UAC) flag `TrustedToAuthForDelegation`. Accounts with this flag are trusted to perform impersonation of arbitrary users within the context of delegation​​.
20. **What can you do with the permission «Trusted to Auth for Delegation» S4U2Self & S4U2Proxy?**
      - **S4U2Self (Service for User to Self)**: This extension allows a service (which holds the "Trusted to Auth for Delegation" permission) to obtain a service ticket to itself on behalf of any user, even if that user has not previously authenticated to the service. Essentially, it allows the service to impersonate any user in the domain.
      - **S4U2Proxy (Service for User to Proxy)**: Using this extension, the service can then use the service ticket obtained via S4U2Self to request service tickets to other services on behalf of the user. This means the service can act as a proxy, accessing other services as if it were the user.
      - The combination of these extensions with the "Trusted to Auth for Delegation" permission effectively allows a service to impersonate any user in the domain and access resources on their behalf.

### Topic 13: Secure Email

1. **How does the email routing works?**
	- Mails are sent via SMTP, the MX record specifies the mail server responsible for a domain name. By sending a mail, the MTA queries DNS for the MX record for the recipient's domain name (lowest-numbered records are the most preferred).
	- MUA $\rightarrow$ MSA $\rightarrow$ Sender's MTA $\rightarrow$ Receiving MTA $\rightarrow$ (multiple hops) $\rightarrow$ MDA $\leftarrow$ only authenticated MUAs can access emails via POP3 or IMAP.
2. **RFC 8314 introduces Transport Layer Security (TLS) for Email Submission and Access. What security concerns are addressed?**
	- Confidentiality and integrity of email content during transit (no E2E encryption!), protects user credentials from eavesdropping when clients authenticate to email servers, mitigates MITM attacks by authentication email servers to client
3. **Explain what information the «Email envelop» contains (RFC 5321) and what information «Internet Message Format» (RFC 5322) contains?**
	- SMTP envelope: Sender and recipient information used for routing and delivery (MAIL FROM, RCPT TO)
	- Internet Message Format:
		- Mail Header (From, To, Subject, Date, DKIM, ...)
		- Mail Body
4. **What information can be found in the «mail header» which fields are mandatory?**
	- Required: origination date field (Date) and the originator from (From)
	- Common: To, Subject, Message-ID, CC, BCC, Received (trace fields), ...
5. **SMTP originally (RFC821) only allowed 7-bit encoding. What encodings do you know to circumvent this limitation?**
	- MIME supports Base64 and Quoted-Printable encoding
6. **How can you sent signed and encrypted emails (PKCS#7)?**
	- Use MIME type `application/pkcs7-mime` and sign or encrypt mail with certificates (pk infrastructure)
7. **What is the difference between a «Detached Signatures» (application/pkcs7-signature) and a regular PKCS#7 signature (application/pkcs7-mime)?**
	- *Detached Signature*: The signature is stored separately from the original data. This allows recipients to verify the signature without altering the original message format $\rightarrow$ if a mailing list modify email parts, the signature isn't valid anymore.
	- *Regular PKCS#7 Signature*: The signature and the original data are bundled together in a single file. This is more convenient for ensuring both the data and its integrity are preserved together, but it alters the original message format.
8. **Describe how a PKCS#7 message is encrypted for a group of recipients. How is the PKCS#7 encrypted data (pkcs7-envelopedData) structured?**
	- The message is encrypted once using a symmetric key.
	- Each recipient's public key encrypts the symmetric key.
	- The PKCS#7 structure contains the encrypted message, a per-recipient encrypted symmetric key, and encryption algorithm details.
9. **How can you authenticate the origin of an email message (SPF, DKIM, DMARC)?**
	- SPF: erifies the sender's IP address against the domain's published SPF record in DNS.
	- DKIM: Uses a digital signature, linked to the sender's domain, that is verified against a public key in the domain's DNS records.
	- DMARC: Leverages SPF and DKIM authentication results, specifying how receivers should handle failed emails and providing reports on email sources and failures.
10. **What problems tries the Sender Policy Framework (SPF) to address? On what address (RFC5321.MailFrom) is the policy based on?**
	- SPF addresses Email Spoofing (unauthorized senders) and Spam/Phishing (verify sender authenticity). SPF policy is only based on the RFC5321.MailFrom (SMTP envelope) and thus can be bypassed by Spammers.
11. **Describe a typical SPF entry (e.g. from bfh.ch). Where do we find the entry and what information does it contain?**  
	 - The SPF record can be found in DNS as TXT record (`dig bfh.ch TXT`), for an example see [[Email Authentication#Examples|here]]
12. **Describe problem cases respectively scenarios where SPF will fail.**
	- *Email Forwarding*: if an email is forwarded by an intermediate server, the sender's IP may no longer match the SPF record (e.g. Mailing list)
	- RFC5321.MailFrom (SMTP envelope) can be overwritten by a Mailing list or Spamer to generate an SPF pass
	- Many receivers do not act on SPF's policy assertion (misconfiguration, unclear implementation like "softfail")
13. **Which problem addresses the Domain Keys Identified Messages (DKIM) standard?**
	- DKIM addresses the problem of email tampering and sender identity verification. It ensures that an email's content and sender can be authenticated and have not been altered or forged during transit.
14. **How is DKIM designed. What do you need for implementing DKIM?**
	- *Digital Signatures*: the email gateway sign all outgoing emails with a private key
	- *Public Key in DNS*: the public key is published as an DNS TXT record
15. **Describe a typical DKIM entry found in the mail header. What information does it contain?**
	- Version (v=1), Algorithm (rsa-sha256), Domain (d=example.com), Selector (s=selector1, specific public key), Signature Data (b=signature), Signed Headers (`h=from:to:date`)
16. **Where do we find the DKIM key? What types / formats of keys are used?**
	- The key is in the sender's domain DNS record. RSA is mostly used ed25519 is supported too.
17. **Describe the relationships of DKIM key location (domain), RFC5322.From, RFC5321.MailFrom to DKIM.**
	- The signing domain does not have to have any relationship to the domains in the RFC5322.From (Mail Header) or RFC5321.Mail From (SMTP Envelope)
18. **Which steps are involved verifying a DKIM signature? What can go wrong?**
	- more complicated to deploy than SPF
	- does not verify if the signed parts of the message are altered (which happens often, e.g. mailing lists, corporate gateways adding a header, etc.)
	- crypto concerns need to be tracked (key length, hashing algorithms)
19. **Describe the functions of ARC-Authentication-Results (AAR), ARC-Message-Signature (AMS) and ARC-Seal (AS)? Who is adding these mail headers?**
	- ARC headers are added by intermediate email servers to solve altering headers and provide valid signatures
	- *AAR*: checks for SPF, DKIM, DMARC
	- *AMS*: added by the server that performs the ARC signing, signature of entire message except for the ARC-Seal headers
	- *AS*: signature of the previous ARC-Seal headers, validity of the prior ARC entries
20. **What problems is DMARC addressing?**
	- DMARC addresses email spoofing, fraud, and unauthorized domain use by allowing domain owners to specify authorized email sources and policies for handling failed emails. It provides visibility through reporting on email authentication.
21. **Describe a typical DMARC entry (e.g. from ubs.com). Where do we find the entry and what information does it contain?**
	- DMARC entries are published in DNS TXT records
	- Version, Policy (p=reject/quarantine/none), Alignment (adkim=strict/relaxed), Reporting (rua=mailto:dmarc@example.com)
22. **On what address is DMARC based on (RFC5322.From)?**
	- DMARC operates on RFC5322.From address (Mail Header)
23. **What is the alignment to the DKIM and SPF record?**
	- Alignment in DMARC can be strict or relaxed, and it checks whether the domains in DKIM signatures or SPF records match the RFC5322.From domain. Strict alignment requires an exact match, while relaxed alignment allows for subdomain matches.
24. **Where is DMARC policies verification enforced? How can you check the effect of your DMARC policies?**
	- DMARC policies are enforced by email receivers (servers) that validate incoming emails against the policies set by the sending domain. To check the effect of your DMARC policies, send test emails to services like Gmail and configure your DMARC record to receive reports.
25. **What are the options if the DMARC verification fails?**
	- None (monitor), Quarantine (move mails in quarantine or spam folders), Reject (reject email)

### Topic 15: PKCS\#11 (YubiKey)

1. **Describe a typical PKCS\#11 stack for accessing a security token.**  
     - Application with PKCS#11 support
     - PKCS#11 library
     - PC/SC (Personal Computer/Smart Card) communication via APDU (Application Protocol Data Unit)
     - Driver (USB, NFC, Bluetooth)
     - Token with an app installed that supports PKCS#11
2. **Where are APDU (Application Protocol Data Unit) commands used?**
     - APDU (Application Protocol Data Unit) commands are used in smart card technologies. They facilitate communication between a smart card and an external device, like a card reader. These commands are essential in applications such as EMV (Europay, MasterCard, and Visa) chip-based credit cards, SIM cards in mobile phones, identity verification systems, and secure access control.
3. **Which protocol is common between SIM card, smart cards, credit cards, YubiKey etc.?**
     - The ISO/IEC 7816 standard. This standard defines the physical characteristics, communication protocols, and APDU commands for interaction with smart cards
4. **What is the intention of the PKCS\#11 API?**
     - The primary intention of the PKCS#11 API is to provide a standard interface for applications to interact with cryptographic tokens.
5. **How can you extract keys from a smart card or HSM?**
     - This is designed to be difficult or impossible. Some HSMs or smart cards may allow the export of certain keys under specific conditions, often wrapped with another key and subject to stringent security policies
6. **What does attestation stands for?**  
     - Attestation refers to the process where a device or a system demonstrates (or attests to) its identity and integrity. Done via X509 certificates for example. Proof that something was done in specific hardware.
7. **What does the acronym U2F (Universal Second Factor) stands for? What is it based on?**
     - U2F is a standard for two-factor authentication (2FA). It allows users to augment traditional login methods with a physical device, like a USB security key, which provides an additional layer of security. U2F devices communicate with the host using standard protocols such as USB, NFC, or Bluetooth. The U2F standard is based on public-key cryptography. 

### Topic 16: VPN

1. **At which OSI layer can VPN solutions be established? Provide examples.**
	
| Layer | Example |
| ---- | ---- |
| Application Layer | ssh, PGP |
| Transport Layer | TLS (SSL), OpenVPN |
| Network Layer | IPSec, WireGuard |
| Data Link Layer | PPTP, L2TP, IEEE 802.1(X, AE, i) |
| Physical Layer | Quantom Cryptography |

2. **What advantages and disadvantages, or challenges, are associated with a low-level implementation?**
     - **Advantages:**
         1. **Performance Optimization:** Allows fine-tuning for maximum efficiency and speed, crucial for resource-constrained or high-performance systems.
         2. **Hardware Control:** Direct control over hardware resources, enabling precise management and optimization.
         3. **Resource Usage:** Can be more resource-efficient, using less memory and processing power.
     - **Challenges:**
         1. **Complexity:** More complex and time-consuming to develop, requiring deeper understanding of hardware and system architecture.
         2. **Portability:** Often less portable between different hardware platforms, requiring significant modifications for each platform.
         3. **Debugging Difficulty:** Debugging and maintenance can be more challenging due to the proximity to hardware and lack of abstraction.
         4. **Security Risks:** Lower-level code might be more prone to critical security vulnerabilities like buffer overflows.

3. **Explain the authentication process involved in IKEv2 (Internet Key Exchange Protocol Version 2).**
     - **Key Generation**:
	     - A master secret ($SK_d$) is generated along with several other keys ($SK_{ai}, SK_{ei}, SK_{ar}, SK_{er}, SK_{pi}, SK_{pr}$) using a pseudo-random function (prf).
         - The keys $SK_{ai}, SK_{ei}, SK_{ar}, SK_{er}$ are used for integrity protection and encryption of the IKE-Auth message.
         - $SK_{pi}$ and $SK_{pr}$ are pre-shared keys used for authentication
	 - **Authentication**:
	     - **Digital Signature with X509 Certificates**:
             - The initiator signs the first message, appending $N_r$ (nonce from the responder) and prf($SK_{ai}$ , $ID_i$) (a function of the initiator's identity and a key).
             - The responder signs the second message, appending $N_i$ (nonce from the initiator) and prf($SK_{ar}$ , $ID_r$) (a function of the responder's identity and a key).
     - **Pre-shared keys**:
         - HMAC (Hash-based Message Authentication Code) using a negotiated pseudo-random function.
         - The authentication (AUTH) is calculated as `prf(prf(Shared Secret «Key Pad for IKEv2») <InitiatorSignedOctets>).`
4. **What is the purpose of the Authentication Header (AH) and the Encapsulating Security Payload (ESP)? Elucidate the distinctions between these two components.**
     - The Authentication Header (AH) and Encapsulating Security Payload (ESP) are two components of IPsec used for securing internet protocol communications.
	 - **Authentication Header (AH)**: The primary purpose of AH is to provide integrity and authentication of the data. It ensures that the data has not been tampered with during transit and verifies the identity of the sender. However, AH does not provide encryption, so the data remains readable to anyone who intercepts it.
	 - **Encapsulating Security Payload (ESP)**: ESP, on the other hand, provides confidentiality in addition to integrity and authentication. It encrypts the payload data, which means that the content is hidden from unauthorized viewers. ESP can also optionally provide authentication and integrity similar to AH.
	 - **AH-ESP Combination**: When used together, AH provides authentication and integrity checking, while ESP adds encryption for data confidentiality. This combination ensures that the data is not only encrypted but also comes with strong integrity and authentication measures. It offers a higher level of security by combining the strengths of both AH and ESP.
5. **Explain the two IPsec modes: «tunnel mode» and «transport mode».**
     - **Tunnel Mode**: Encrypts both the payload and the header of the original IP packet. It's typically used in network-to-network communications, where the entire original IP packet is encapsulated and a new IP header is added. This mode is suitable for VPNs and gateway-to-gateway communications.
     - **Transport Mode**: Only encrypts the payload of the IP packet, not the header. It's mainly used for end-to-end communications between two devices, where the original IP packet header remains intact. This mode is suitable for direct communication between two hosts.
6. **What MTU (Maximum Transmission Unit) considerations should be taken into account when implementing IPsec?**
     - MTU is usually 1500 bytes IP header and TCP header are usually 20 bytes long so the payload can contain 1460 bytes.
	 - But IPsec adds an Authentication and ESP header (around 50-60 bytes). So the tunneling Interface might be set to 1400 bytes
7. **Which credentials are required to initiate a WireGuard VPN connection?**
	 1. Your Private Key
	 2. Peer's Public Key
	 3. Peer's Endpoint (IP address and port)
	 4. Allowed IPs (IP ranges or subnets)
	 5. Pre-Shared Key (optional)
	 6. Configuration File (optional, but helpful)
8. **What is the fundamental concept behind the key exchange in «Noise Protocol Framework»? What is the RTT of the handshake?**
     - **Handshake Mechanism**: Each session begins with a handshake that only takes 1 round-trip time (1-RTT)​
     - **Basic Concept**: The key exchange employs a triple Diffie-Hellman (DH) mechanism similar to the one used in Signal, with an additional step to enable the 1-RTT handshake​
     - **Key Exchange Process**:
         - **Ephemeral Public Elliptic Curve (EC) Keys**: Both parties send their ephemeral public EC keys ($g^{e_i}$ for the initiator, $g^{e_r}$ for the responder)​
         - **Long Term Static EC Key Pairs**: Each party has a long-term static EC key pair ($s_i , g^{s_i}$ for the initiator, $s_r , g^{s_r}$  for the responder).
         - **Ephemeral EC Key Pairs**: Each party also creates an ephemeral EC key pair ($e_i , g^{e_i}$  for the initiator, $e_r , g^{e_r}$  for the responder).
     - **Derivation of Key Pairs**: Four key pairs are derived from these exchanges: $k_1$ from $g^{e_i s_r}$, $k_2$ from $g^{s_i e_r}$, $k_3$ from $g^{e_i e_r}$, and $k_4$ from $g^{s_i s_r}$
	 - **Symmetric Transport Encryption**:
         - **Key Generation**: The derived keys for symmetric transport encryption are generated using HMAC-based Extract-and-Expand Key Derivation Function (HKDF).
         - **Distinct Keys for Each Direction**: $tk_i$ is derived for one direction, and $tk_r$ for the opposite direction.
         - **Encryption Method**: The transport encryption of network packets uses symmetric ChaCha20 encryption authenticated with Poly1305​
9. **Describe VPN network topologies.**
     - **Point-to-Point**:
         - This is the simplest form of VPN topology.
         - It involves a direct connection between two points (or nodes), typically a client and a server.
         - It's often used for individual remote access to a centralized network.
     -  **Site-to-Site**:
         - Connects entire networks to each other.
         - Commonly used to connect branch offices to a central corporate network.
         - Each site has a VPN gateway, and traffic is routed between these gateways over the VPN.
     -  **Hub-and-Spoke** (Star): 
         - Involves a central 'hub' (usually a main office or data center) and multiple 'spokes' (remote locations or branch offices).
         - All traffic between the spokes usually goes through the hub.
         - Efficient for networks where most communication occurs between the hub and the individual spokes, rather than directly between spokes.
10. **What minimum configurations are needed to set up a point-to-point VPN with WireGuard.**
     -  **Network Interface Configuration**:
	     - On the server, you will create a WireGuard interface, typically named `wg0`. This includes:
             - Private and public keys (generated using `wg genkey | tee privatekey | wg pubkey > publickey`).
             - An IP address for the WireGuard interface (usually from a private range, e.g., `10.0.0.1/24`).
            - Listening port (e.g., `51820`).
     - On the client, you also create a WireGuard interface with:
         - Its own set of private and public keys.
         - An IP address that belongs to the same subnet defined on the server but is a unique address within that subnet (e.g., `10.0.0.2/24`).
     - **Configuration Files**: Both server and client require configuration files (`wg0.conf`), which include:
         - On the server:
             - Its private key.
             - Listening port.
             - Peer (client) public key.
             - Allowed IPs (usually the client's IP, e.g., `10.0.0.2/32`).
         - On the client:
             - Its private key.
             - Server's public key.
             - Server's IP address and port.
             - Allowed IPs (can be `0.0.0.0/0` for routing all traffic through the VPN, or the server's subnet for a more restricted setup).

### Topic 17: Wi-Fi

1. **Under which conditions can you read all Wi-Fi network traffic?**
	- good antenna, being within range of the Wi-Fi
	- Wi-Fi card supporting monitor mode and packet injection.
	- root privileges for tools
	- its useful to set the MAC and IP address statically
2. **Explain the difference between a network card in «promiscuous mode» and «monitor mode».**
	- *Promiscuous Mode*: captures all packets on a connected network, regardless of the intended destination MAC address. You will see only packet if you are connected to a station and only packets inside the same network.
	- *Monitor Mode*: captures all wireless traffic within its range, including packets not addressed to it, allowing analysis of all Wi-Fi communications in the vicinity (including beacons and data form any wireless networks in the area).
3. **Describe the WEP (Wired Equivalent Privacy) encryption. What are the weak points?**
	- WEP uses the RC4 stream cipher for encryption with 64-bit and 128-bit encryption keys (which include a 24-bit IV)
	- Weak Points:
		- *Weak IVs*: only 24-bit
		- *Flawed Integrity*: CRC-32 for checksum for data integrity, which is not cryptographically secure
4. **What kind of authentication does WEP support (Shared Key Authentication, Open System Authentication)?**
	- *Shared Key Authentication*: Pre-shared WEP key, During the authentication process, the access point sends a challenge text to the client, which encrypts it using the WEP key and sends it back. The access point decrypts it to verify if the client has the correct key $\rightarrow$ this method exposes part of the encryption mechanism, this is not secure!
	- *Open System Authentication*: no credentials, any device can request authentication and will be granted access (but with encrypted traffic)
5. **What is needed to crack a WEP key?**
	- sniffing of packets (FMS attack: about 400'000 packets, PTW: 60'000 - 100'000)
6. **Describe a WPA2 authentication with PSK (pre-shared key)?**
	- 4-Way Handshake:
		1. The AP sending a random number (ANonce) to the client
		2. The client responding with its random number (SNonce)
		3. The AP calculating the PTK (Pairwise Transient Key) from these numbers and sending an encrypted message to the client
		4. The client decrypting this message with the PTK, confirming successful authentication
7. **What is the purpose of PBKDF2 (Password-Based Key Derivation Function 2)?**
	- In the context of WPA2, PBKDF2 takes the PSK (a passphrase) and generates a 256-bit key. It incorporates the SSID and the number of iterations (4096 in WPA2) to make brute-force and dictionary attacks more difficult.
8. **Assume you want to analyze an WPA2 communication with Wireshark. What is needed to decrypt the packets of the CAP file (packet capture file)?**
	- To decrypt WPA2 packets in a packet capture file (CAP file) using Wireshark, you need the network's PSK and the SSID.
	- Additionally, capturing the four-way handshake process is essential, as it contains the nonce values used to derive the session keys for encryption.
9. **What Wi-Fi attacks do you know? Describe how they work.**
	- *WPA2-PSK Cracking*: dictionary attack against PSK with SSID and captured handshake (test a password and check until MIC matches)
	- *Rouge DHCP*: allows attackers to set their device as the default router
	- *Fake Webauth*: most users are used seeing a webauth page when connecting to a Wi-Fi
10. **What is «SSID Cloaking»? Does it protect a Wi-Fi access point?**
	- SSID cloaking involves hiding the network name (SSID) from broadcasting in beacon frames, making it less visible to casual scanning.
	- While it can deter casual users, it does not provide significant protection as the SSID can still be discovered by determined attackers using packet sniffers or during the connection process. It is more of an obscurity measure than a robust security feature.

---
links: [[600 SPA MOC|SPA MOC]] - [[themes/000 Index|Index]]