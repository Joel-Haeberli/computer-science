tags: #malware-analysis #actors #attacks
 
# Actors and Attacks

links: [[801 MAI TOC - Actors & Tools & Attacks|TOC - Actors & Tools & Attacks]] - [[themes/000 Index|Index]]

---

## Intro

Malware analysis is a crucial aspect of cybersecurity due to the increasing prevalence of cyber attacks. The digital society and economy have created opportunities for cybercrime and espionage, as most information and tools are now digital. Several factors contribute to the rise in cyber attacks:

- Connectivity allows attackers to operate from anywhere, making attribution difficult and reducing risks for them.
- There is an inherent asymmetry between attackers and defenders; while defenders must secure all systems, attackers need to breach only one.
- Vulnerable systems can be breached given enough time and skills.
- The state of defense is often below the state of the art due to lack of prioritization.

Cybercriminals use malware primarily to earn money. Ransomware attacks targeting companies and organizations are currently the most prevalent form of cybercrime. Other activities include e-banking fraud, identity theft, and credit card fraud. The nature of cybercrime is evolving, with a shift from individual to organizational targets. Everyone is a potential target of cybercrime, emphasizing the need for effective malware analysis and defense mechanisms.

## Actors

The actors involved in cyber attacks range from individual criminals to state-sponsored entities.

### Cybercriminals

  - Cybercriminals are organized and trade goods and services related to their activities. Their sophistication varies greatly from opportunistic small crimes to highly advanced operations.
  - Cybercriminal groups are not limited to specific geographies; significant groups operate from Russia. They remain safe from prosecution as long as they do not attack Russian targets or those of allied countries. Some allegedly cooperate with intelligence agencies.
  - The main business today is multi-extortion ransomware attacks. In the case of triple extortion:
    - Infiltrate network, encrypt data, and ask for ransom to decrypt/restore data.
    - Exfiltrate data, ask for ransom to not leak or sell data.
    - Ask for ransom to not leak data from the victim’s partners or clients.

### State Actors (Espionage)

  - The goal of espionage-type cyber attacks is to gain information, typically for political, military, or economic advantages.
  - Most countries have offensive espionage capabilities. Main actors include the US, China, Russia, Israel, Iran, and North Korea. Attacks by these countries are regularly uncovered, though those by Western governments are less publicized.
  - Various attacker groups exist within the same country, often coinciding with intelligence agencies. For example, Russia has GRU, SVR, and FSB; the US has NSA, CIA, FBI, and others.
  - The sophistication of attacks varies. Advanced attackers choose appropriate techniques based on their goals, sometimes using common tools for low-value targets.

### State Actors (Cyber War)

  - Cyberwarfare involves using digital attacks to cause harm comparable to actual warfare or disrupt vital systems. Targets include water, fuel, communications, transportation, power grids, and military systems.
  - Stuxnet is a notable example, infiltrating and damaging the Iranian nuclear facility in Natanz, destroying over 1000 centrifuges.

### State Actors (Lawful Interception)

  - Law enforcement uses malware to access encrypted communications on suspects' devices, capturing content before encryption or after decryption.
  - This practice is controversial, particularly in non-democratic countries where lawful interception may turn into surveillance. There is a risk of planting false evidence or modifying existing evidence.
  - Law enforcement agencies often buy malware from companies like NSO Group's Pegasus spyware, which is sold to various entities, raising ethical concerns.

### Other Actors

  - Mercenary hackers, or "hackers for hire," collaborate with both cybercriminal and state actors.
  - There are also "unknown" attackers whose identities remain unclear.

### Actors Overview Table

![[actors_overview_table.png]]

## Attacks

Cyber attacks vary in method and scope, from broad, opportunistic attacks to highly targeted and sophisticated operations. Understanding these types of attacks helps in developing appropriate defense mechanisms.

### Types of Attacks

  - **Opportunistic/Non-targeted Attacks**
    - Target a large number of people with general attacks that are not specifically aimed at any one person. Even with a low success rate, the large volume of attacks can result in significant revenue.
    - Example: Sending malicious emails to millions of potential victims. With a success rate of 1/10,000, 10,000 successful infections can yield substantial revenue.
  - **Targeted Attacks (APT)**
    - Focus on high-value targets, requiring detailed knowledge and often high technical sophistication.
    - Known as Advanced Persistent Threats (APT), these attacks may involve sustained efforts to infiltrate and maintain access to specific targets.

### Infection Techniques

Common methods for initial access include malicious email attachments, unpatched VPNs, weak RDP passwords, and web-based attacks.

### Malware and Tools

After gaining initial access, attackers install malware, send commands, and deploy new tools. This includes lateral movement within the network to compromise more machines and gain control over the victim's network.

### Droppers and Downloaders

Droppers and downloaders are typically early-stage malware whose purpose is to deploy the next stage malware.

**Droppers**
    
- Contain the next stage malware within the dropper file itself, often in encrypted form.
- Upon execution, the dropper decrypts and installs the payload on the victim's system.

**Downloaders**

- Fetch the next stage malware from the attackers' command and control (C2) infrastructure.
- Connect to designated download servers to retrieve and install additional malicious payloads.

### Operating Systems Affected

  - All major operating systems (Windows, MacOS, Linux) and smartphones (iOS, Android) are targeted. Attackers choose targets based on their goals and available exploits.
  - Cybercrime mass malware often targets Windows due to its widespread use, but there is also malware for Linux and MacOS, particularly as Linux is a common server OS.
  - Nation-state and targeted attacks are OS agnostic, targeting any platform as needed.

---
links: [[801 MAI TOC - Actors & Tools & Attacks|TOC - Actors & Tools & Attacks]] - [[themes/000 Index|Index]]