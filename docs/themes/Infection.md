tags: #malware-analysis #infection
 
# Infection

links: [[801 MAI TOC - Actors & Tools & Attacks|TOC - Actors & Tools & Attacks]] - [[themes/000 Index|Index]]

---
## Intro

This chapter explores the various techniques attackers use to gain initial access to systems and networks. Understanding these methods is crucial for developing effective defenses against cyber attacks. The primary focus areas include infection vectors, exploitation of technical and human vulnerabilities, and specific attack methods such as malware delivery and social engineering.

## Infection Vectors and Vulnerabilities

This section covers the methods and weaknesses that attackers exploit to deliver malware and gain access to systems, focusing on both technical and human vulnerabilities.

### Infection Vectors

Infection vectors refer to the means and techniques used to deliver malware onto a victim's machine or gain access to a victim's network. These vectors exploit both technical and human vulnerabilities to compromise target systems.

- **Definition**: Infection vectors are methods used by attackers to introduce malware into a system or network.
- **Examples**:
	- **Exploiting Unpatched Software**: Attackers take advantage of software vulnerabilities that have not been patched by the user.
	- **Misconfigurations in Network Devices**: Incorrect settings in devices like firewalls and web servers can allow attackers to gain access.

![[entry_vectors.png]]

### Technical Vulnerabilities

Technical vulnerabilities are weaknesses in hardware or software that can be exploited by attackers to gain unauthorized access to systems.

**Types of Technical Vulnerabilities**:

- **Misconfigurations**: Incorrect configurations in firewalls, web servers, and other network devices can create entry points for attackers.
- **Weak Passwords**: Simple or commonly used passwords make it easier for attackers to gain access through brute force attacks.
- **Unpatched Software**: Software that is not updated with the latest security patches remains vulnerable to known exploits.

**Exploitation Process**:

- Attackers identify and exploit these weaknesses to gain initial access to the target system.

**Software Vulnerabilities**:

- **Definition**: Subtle programming errors that can be exploited by processing maliciously crafted input data.
- **Examples**: A malicious PDF that, when opened, executes shellcode to install malware.

**Zero-Day Vulnerabilities**:

- **Definition**: Vulnerabilities that are not publicly known and therefore very difficult to defend against.
- **Market for Zero-Day Exploits**: These vulnerabilities are rare, expensive, and typically used by nation-state actors due to their stealthy nature.

![[0day_lifecycle.png]]

### Human Vulnerabilities

Human vulnerabilities are weaknesses that arise from human behavior, such as being tricked into taking unsafe actions.

**Social Engineering Techniques**:

- **Phishing**: Sending emails that appear to be from legitimate sources to trick users into revealing personal information or clicking on malicious links.
- **Impersonation and Pretexting**: Attackers pose as trusted individuals or create convincing scenarios to deceive victims.

**Examples**:

- **Opening Malicious Attachments**: Users are tricked into opening attachments that contain malware.
- **Sharing Passwords**: Users are deceived into disclosing their passwords to attackers.

 **Exploitation Process**:
 
- Attackers use social engineering techniques to manipulate human behavior and gain initial access to systems.

## Malware Delivery and Initial Access Techniques

This section explores the main methods attackers use to deliver malware and achieve initial access, including email-based, web-based, and physical delivery techniques.

### Email-Based Delivery

Email is one of the most common methods for delivering malware. Attackers use various techniques to deceive users into opening malicious attachments or clicking on harmful links.

- **Phishing Emails**:
	- **Definition**: Emails that appear to be from legitimate sources but contain malicious links or attachments.
	- **Technique**: Attackers often use social engineering tactics to make these emails convincing.
- **Spear Phishing**:
	- **Definition**: A targeted phishing attack aimed at specific individuals or organizations.
	- **Technique**: Attackers gather detailed information about their targets to craft personalized emails that are more likely to deceive.

### Web-Based Delivery

Web-based attacks exploit vulnerabilities in web browsers and plugins to deliver malware.

- **Drive-By Downloads**:
	- **Definition**: Automatic download and installation of malware when a user visits a compromised website.
	- **Technique**: Attackers use exploit kits to take advantage of vulnerabilities in the user's browser or plugins.
- **Watering Hole Attacks**:
	- **Definition**: Attackers compromise websites that are frequently visited by the target group.
	- **Technique**: The compromised website serves malware to visitors, aiming to infect systems of interest.

### Physical Delivery

While less common, physical methods can also be used to deliver malware.

- **Infected USB Sticks**:
	- **Definition**: USB sticks preloaded with malware.
	- **Technique**: Attackers leave these USB sticks in places where potential victims might find them and plug them into their computers.

### Initial Access Techniques

These methods are used by attackers to gain initial access to target systems, often as the first step in a more extensive attack campaign.

- **Social Engineering**: Manipulating individuals into performing actions that compromise security.
- **Exploiting Technical Vulnerabilities**: Taking advantage of software or hardware weaknesses.
- **Physical Access**: Using physical means to gain access to systems, such as infected USB sticks or other devices.

![[initial_access_techniques.png]]
## Case Studies and Examples

This section provides real-world examples of notable attacks and infection techniques to illustrate how attackers operate and highlight the practical implications of these methods.

### Notable Attacks

**Sednit Group (APT28/Fancy Bear) Spear Phishing**:

  - **Incident**: The Sednit group, also known as APT28 or Fancy Bear, has reportedly infiltrated machines operated by targets such as the DNC, the German parliament, and John Podesta, among others.
  - **Technique**: The group used spear phishing emails containing malicious attachments or links to compromise their targets.
  - **Outcome**: These attacks resulted in significant data breaches and political impact.

### Drive-By Download Examples

Drive-by downloads are a common method used by attackers to compromise systems. Understanding how these attacks are executed can help in defending against them.

**Exploit Kits**:

  - **Definition**: Tools used by attackers to automate the exploitation of vulnerabilities in web browsers and plugins.
  - **Example**: Websites infected with exploit kits can automatically download and install malware on a visitor’s computer without any user interaction.
  
**Case Studies**:

  - **Example 1**: Popular news sites were hacked to serve drive-by downloads, infecting thousands of users who visited the compromised sites.
  - **Example 2**: Watering hole attacks targeted specific groups by compromising websites known to be frequented by the targets, serving malware through drive-by downloads.


---
links: [[801 MAI TOC - Actors & Tools & Attacks|TOC - Actors & Tools & Attacks]] - [[themes/000 Index|Index]]