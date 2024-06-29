tags: #web #network #security-tool #security-protocol   

# SPA TOC - Exam Questions

links: [[600 SPA MOC|SPA MOC]] - [[themes/000 Index|Index]]

---
## Part 1

### Topic 1: Information Security

1. What is meant with Information Security?
2. What are the goals of Information Security?
3. What are older terms for Information Security?
4. Whats an information asset?
5. Who is responsible to protect information assets?
6. What is an ISMS?
7. Do you now Information Security Standards? Which?
8. What are Risks?
9. What are Security Controls?
10. Do you know some important Security Controls? Explain them.
11. What's the job of a Security Professional?
12. Which Security Controls should be implemented immediate if no other controls are in function (e.g., according to the NSA)?
13. What do the acronyms CIA and AAA in connection with Information Security mean?
14. Are you able to explain the meaning of the abbreviated words?
15. What is an "information security incident"?
16. What is the difference between an "information security event" and an "information security incident"?
17. What are the goals of "security incident management"?

### Topic 2: Hacking Basics

1. Recently, there were more and more cyber security attacks against critical infrastructures. What is a critical infrastructure? Provide some examples. What are the targets of such attacks?
2. From where do external attackers (outside attackers, remote attackers) attack networks and computers?
3. Do you know some intrusion techniques? Can you explain these techniques in detail?
4. List known vulnerabilities of systems. Can you explain these vulnerabilities in more details.
5. What authentication methods do you know?
6. List and explain the five stages / phases of an intrusion into a system.
7. Do you know "shortcuts" to the five stages / phases of an intrusion?

### Topic 3: Layered Security

1. Do you know layer specific vulnerabilities (vulnerabilities, which occur on one of the seven layers of the ISO / OSI network reference model)?
2. Can you explain countermeasures?
3. Which vulnerability is the most critical?

### Topic 4: Host and Network Security

1. What are well known computer-based security mechanisms (Host-based security mechanisms)?
2. What are well-known network-based security mechanisms?
3. What are capabilities of network firewalls?
4. What are limitations of network firewalls?
5. Which other terms are used for network layer firewalls?
6. Explain briefly the operation of network layer firewalls.
7. Which protocol header fields are usually evaluated by a packet filter?
8. What is a stateful inspection firewall?
9. What is meant by "deep inspection"?
10. What are the features of a "Next Generation Firewall"?
11. Explain the term "Unified Threat Management UTM"
12. What's the intention of threat protection firewalls? How do they work?
13. What's an advanced persistent threat (APT)?
14. What is an application layer firewall? How does it work?
15. How do proxy servers work, what are non-/transparent proxy servers?
16. What are "Web Application Firewalls" for?
17. Which basic firewall architectures do you know?
18. What are scurity zones?
19. You enable the access to an internal web server through your home router / firewall via port forwarding. Which firewall architecture corresponds to this setup? What dangers does it offer?
21. What are advantages/disadvantages of a IDS/IPS?
22. Explain the term "endpoint security"
23. What's the function of an SIEM?
24. Explain the "Zero Trust" approach to improve network security

### Topic 5: Linux firewall (netfilter / iptables / nftables)

1. Explain the structure of "netfilter (-hooks)"
2. Which are the predefined rule chains of "netfilter" / "iptables"?
3. Can you draw a schema of the rule chains in the filter table? Where do they have an effect?
4. What is the "nat" table of "netfilter" / "iptables" for?
5. Which predefined rule chains belong to the "nat" table?
6. What is the structure of a rule in an "iptables" chain?
7. What happens, if a rule matches/does not match a packet?
8. Which predefined targets are known with "iptables" and what do they do?
9. Do you know some "match/target extensions" and their work?
10. What is the purpose of the match extension "state"/"conntrack" of iptables?
11. What states of connections can be checked by iptables using the match extension "conntrack"?
12. How can packets be marked for further processing?
13. Which kind of processing can be done?
14. Explain presented iptables/nftables rules or rule chains.
15. Why is "nftables" more flexible then "iptables"?
16. What are the main differences between "nftables" and "iptables"?
17. What happens with my "iptables"-rules if "nftables" is deployed?
18. Explain what the presented "nftables" firewall does (e.g., lab sample solutions).

### Topic 6: DNSSEC and DNS privacy

1. Why is DNSSEC used? What problem does it solve?
2. What is the purpose and function of a validating resolver?
3. What are the new DNSSEC Resource Records? What are they for?
4. What is the purpose of the RRSIG/DNSKEY/NSEC/DS RR? Explain how they work.
5. What is a Resource Record Set (RRSet) and where is it used?
6. What problem is caused by the NSEC RR? How can it be solved?
7. What is the purpose of the Zone Signing Key ZSK?
8. What is the purpose of the Key Signing Key KSK?
9. How are DNS entries validated on a validating resolver?
10. How does the Chain of Trust for DNSSEC work?
11. What response does a client receive if the resolver used cannot validate a response?
12. What is the purpose of the AD or the CD flag in the DNS protocol header?
13. Explain use cases for DNSSEC such as SSHFP or DANE?
14. Do you know methods to improve the confidentiality and privacy of DNS communication?
15. Explain mechanisms/protocols that ensure the confidentiality of DNS transactions.
16. How can DoT be implemented on a DNS resolver (which does not support it natively)? 

### Topic 7: DNS RPZ

1. What is a Response Policy Zone (RPZ) and how does it work?
2. What do you use RPZs for?
3. How do you get valuable RPZ information?
4. What responses can a resolving name server respond to a client out of a RPZ?
5. How can you block/redirect access to "badhost.baddom.com" using RPZ?

### Topic 8: Tools

1. Why is a centralized logging important? How can it be done?
2. What is a syslog facility and a syslog severity?
3. Which tools can you use to capture traffic?
4. How do vulnerability scanners work? Can they find every vulnerable system?
5. What is nmap for? What is a stealth scan?
6. What is "netflow" or "IPFIX"? How does it work and why is it an important mean to rise host and network security?
7. Explain an ARP MITM attack. What are countermeasures?
8. What is the purpose of "arpwatch"?
9. Why and when is SNMP dangerous?
10. How do you capture packets of a DNS request / response on Interface "eth0" using "tcpdump"?

### Topic 9: Lab Exercises

1. How can a centralized syslog be implemented?
2. Explain how you tested arp spoofing, did it work?
3. What does a specific "iptables" or "nftables" firewall rule do (see also the provided sample solutions)?
4. How do you redirect traffic to a filtering proxy using "iptables" or "nftables"?
5. Which criteria did you use for your filtering proxy?
6. Which means do you know to explore networks?
7. Which vulnerability scanner was used in the lab exercises?
8. What data of your router can you analyze using "nfsen"?
9. What is "softflowd" and how can it be used to export flow data?
10. Explain how "softflowd" and "nfcap/nfsen" interact.
11. Which security distributions where used in the lab? Explain their main focus.

## Part 2

### Topic 10: TLS

1. Name 5 protocols based on TLS.
2. What is meant with «Opportunistic TLS»? What is meant with «implicit TLS»? What kind of risks / attacks do you know?
3. What does «HTTP Strict Transport Security» (HSTS) stands for? How is it supposed to work? Describe the OSI layer in general and where the TLS communication takes place.
4. TLS is composed of the handshake protocol and the record protocol. Describe what happens on each layer?
5. What information do we find in a «Client Hello» message?
6. What information contains the CipherSuite such as TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 (128-bit AES encryption with SHA-256 message authentication and ephemeral ECDH key exchange signed with an RSA certificate)?
7. How does a TLS mutual authentication works? Which additional handshake messages are exchanged?
8. How does a TLS resume session looks like. What are the prerequisites? What is a anonymous TLS session such as TLS_ECDH_anon?
9. What does the term Forward Secrecy stands for. What has to be done to get perfect forward secrecy (PFS)?
10. What do you have to do respectively think off to implement a TLS reverse proxy for a company?
11. What is a bit flipping attack? Which ciphers are vulnerable?
12. What information do you need to inspect and decipher all TLS packets e.g. with wireshark (TLS private key corresponding to the server certificate, pre-master key, master key)?
13. What information is exchanged with Diffie-Hellman key exchange in a TLS session? Describe which information is used for a JA3 fingerprint?  
14. How is the master secret derived for the pre-master secret?  
15. Describe how a HMAC function works.
16. What is meant with «Authenticated Encryption» (AE)?  
17. What is the difference between AE and AEAD (Authenticated Encryption Associated Data)?
18. Describe a «Padding Oracle Attack».  
19. Describe a «Padding Oracle On DOwngradeD Legacy Encryption» (POODLE) attack. 
20. Describe the changes between TLS 1.2 and TLS 1.3 in respect of:
	* Key exchange  
	* Cipher suites  
	* Round trip time 
	* Authenticated Encryption 
	* Authentication / Signature

### Topic 11: Certificates and PKI

1. How can you choose a public RSA key?
2. In which areas are asymmetric keys used?
3. How scales the key distribution process for (a) symmetric keys and (b) for asymmetric keys?
4. Describe the 3 types of trust model: (a) Direct trust, (b) Web of Trust and (c) Hierarchical trust.
5. Describe the 3 types of certificates: (a) Root certificate, (b) Intermediate certificate, (c) End-entity certificate.
6. What information contains a X509v3 certificate?
7. What is the difference between a certificate fingerprint and TBS certificate fingerprint?
8. Provide some samples of trusted root certificates and where they are used.
9. How are X509v3 certificates encoded?
10. Provide an example of a «critical certificate extension». How should «critical certificate extension» be dealt with?
11. Issuers and subjects are represented as «Distinguished Names». What is a «Distinguished Name» (DN)?
12. What is the certificate extension subjectAltName used for?
13. What is defined in PKCS#1, PKCS#7, PKCS#10, PKCS#11, PKCS#12?
14. What is the life cycle of a X509 certificate?
15. What protocols do you know to check the status of a certificate (CRL-DP, OSCP)? Describe them.
16. What is a Extended Validation SSL (EV SSL) certificate?
17. What problems are addressed with the «Certificate Transparency» (CT) standard?
18. How does CT works? Where is it implemented? Who is enforcing checks?
19. Which components and processes are required for a PKI?
20. How to you generate a «Certificate Signing Request» (PKCS#10)? What attributes are checked by the RA?
21. What are «Advanced Digital Signature» (AdES) and «Qualified Electronic Signatures» (QES). Who can issue such certificates in Switzerland?

### Topic 12: Identification Authentication Authorization

1. What is Identification, Authentication and Authorization?
2. What factors are distinguished for authentication? What is required for 2FA / MFA?
3. What is meant in the PSD2 regulation with «strong authentication with linking»?
4. What hat to be met to get a high «Level of Assurance» (LoA)?
5. What can go wrong with shared secrets? How should you store credentials used for password based authentication?
6. Describe «online» and «offline» attacks against passwords.  
7. How do you calculate the Entropy of a password?  
8. How is the password transferred with «HTTP Basic Authentication»?  
9. How does the OATH standard HOTP (HMAC-based One Time Password) works?  
10. How does the OATH standard TOTP (Time-based One Time Password) works?  
11. What is a Challenge-Response-Protocol and why do we need it?  
12. FIDO2 consists of the standards WebAuthn and CTAP. Describe the function of the two standards.
13. What is meant with attestation?
14. What information / LoA do we get with a FIDO2 registration with a YubiKey? 
15. What does the Relying Party (RP) need for verifying the attestation?
16. What communication protocols are supported by CTAP? What options are displayed when resisting on a FIDO2 page with an Android device?
17. What is needed to access resources over OAuth from a «Resource Server»?
18. What is a «bearer token»?
19. Describe the trust relations between the 4 parties: resource holder, client, authentication server and resource server.
20. What kind of CSRF attack would be possible if the client would not check the session state? 
21. How can a resource holder revoke his consent?
22. Outline how you can use «OpenID Connect» as authentication layer. What is the benefit. How are the trust relations?
23. Outline how you can leverage OAuth as Identity Provider interface. 
24. On what security mechanism is OAuth relying on?

### Topic 12.5: Kerberos

1. How does Kerberos works? Why does Kerberos need shared secrets? What are these shared secrets?
2. The Key Distribution Center (KDC) is composed of the Authentication Server (AS) and the Ticket Granting Server (TGT). What is the function of AS and TGT?
3. What is a Server Principal Name (SPN)? How is the name composed / structured?
4. Explain the content and the function of Kerberos Tickets? What is a Ticket Granting Ticket (TGT) and what is a service ticket (ST)? Explain the differences.
5. Explain the differences between «secret keys» and «session keys».
6. How does the Kerberos Pre-authentication works?
7. What is needed to decrypt all messages / tickets in Wireshark?
8. What type of attacks are referred as «Golden Ticket» «Silver Ticket» attack? What can you do with a «Golden Ticket» or «Silver Ticket»?
9. What has to be done if an attacker gained a «Golden Ticket»? 
10. Describe Kerberos delegation. What does it mean. Where is it used?
11. What is the difference between «unconstrained», «constrained» and «resource-based constrained» Delegation.
12. Can the user prevent delegation?  
13. Can you restrict delegation. Where does it makes sense to restrict delegation?  
14. What are the security risks? Describe how «unconstrained» delegation could be misused.  
15. How can you trick users to connect to your service configured for delegation? 
16. How could a printer on a DC could be attacked?  
17. What mitigation measurements do you know to secure Kerberos? 
18. How does an attack against «constrained» delegation looks like?  
19. What is meant with «protocol transition»? How does it work?  
20. What can you do with the permission «Trusted to Auth for Delegation» S4U2Self & S4U2Proxy?

### Topic 13: Secure Email

1. How does the email routing works?  
2. RFC 8314 introduces Transport Layer Security (TLS) for Email Submission and Access. What security concerns are addressed?  
3. Explain what information the «Email envelop» contains (RFC 5321) and what information «Internet Message Format» (RFC 5322) contains?  
4. What information can be found in the «mail header» which fields are mandatory?  
5. SMTP originally (RFC821) only allowed 7-bit encoding. What encodings do you know to circumvent this limitation?  
6. How can you sent signed and encrypted emails (PKCS#7)?  
7. What is the difference between a «Detached Signatures» (application/pkcs7-signature) and a regular PKCS#7 signature (application/pkcs7-mime)?  
8. Describe how a PKCS#7 message is encrypted for a group of recipients. How is the PKCS#7 encrypted data (pkcs7-envelopedData) structured?  
9. How can you authenticate the origin of an email message (SPF, DKIM, DMARC)?  
10. What problems tries the Sender Policy Framework (SPF) to address? On what address (RFC5321.MailFrom) is the policy based on?  
11. Describe a typical SPF entry (e.g. from bfh.ch). Where do we find the entry and what information does it contain?  
12. Describe problem cases respectively scenarios where SPF will fail.
13. Which problem addresses the Domain Keys Identified Messages (DKIM) standard?  
14. How is DKIM designed. What do you need for implementing DKIM?  
15. Describe a typical DKIM entry found in the mail header. What information does it contain? 
16. Where do we find the DKIM key? What types / formats of keys are used?
17. Describe the relationships of DKIM key location (domain), RFC5322.From, RFC5321.MailFrom to DKIM.
18. Which steps are involved verifying a DKIM signature? What can go wrong?
19. Describe the functions of ARC-Authentication-Results (AAR), ARC-Message-Signature (AMS) and ARC-Seal (AS)? Who is adding these mail headers?
20. What problems is DMARC addressing?
21. Describe a typical DMARC entry (e.g. from ubs.com). Where do we find the entry and what information does it contain?
22. On what address is DMARC based on (RFC5322.From)? 
23. What is the alignment to the DKIM and SPF record?
24. Where is DMARC policies verification enforced? How can you check the effect of your DMARC policies?
25. What are the options if the DMARC verification fails?

### Topic 15: PKCS\#11 (YubiKey)

1. Describe a typical PKCS\#11 stack for accessing a security token.  
2. Where are APDU (Application Protocol Data Unit) commands used?  
3. Which protocol is common between SIM card, smart cards, credit cards, YubiKey etc.?
4. What is the intention of the PKCS\#11 API?  
5. How can you extract keys from a smart card or HSM?  
6. What does attestation stands for?  
7. What does the acronym U2F (Universal Second Factor) stands for? What is it based on?

### Topic 16: VPN

1. At which OSI layer can VPN solutions be established? Provide examples.
2. What advantages and disadvantages, or challenges, are associated with a low-level implementation?
3. Explain the authentication process involved in IKEv2 (Internet Key Exchange Protocol Version 2).
4. What is the purpose of the Authentication Header (AH) and the Encapsulating Security Payload (ESP)? Elucidate the distinctions between these two components.
5. Explain the two IPsec modes: «tunnel mode» and «transport mode».
6. What MTU (Maximum Transmission Unit) considerations should be taken into account when implementing IPsec?
7. Which credentials are required to initiate a WireGuard VPN connection?
8. What is the fundamental concept behind the key exchange in «Noise Protocol Framework»? What is the RTT of the handshake?
9. Describe VPN network topologies.  
10. What minimum configurations are needed to set up a point-to-point VPN with WireGuard.

### Topic 17: Wi-Fi

1. Under which conditions can you read all Wi-Fi network traffic?
2. Explain the difference between a network card in «promiscuous mode» and «monitor mode».
3. Describe the WEP (Wired Equivalent Privacy) encryption. What are the weak points?
4. What kind of authentication does WEP support (Shared Key Authentication, Open System Authentication)?
5. What is needed to crack a WEP key?
6. Describe a WPA2 authentication with PSK (pre-shared key)?
7. What is the purpose of PBKDF2 (Password-Based Key Derivation Function 2)?
8. Assume you want to analyze an WPA2 communication with Wireshark. What is needed to decrypt the packets of the CAP file (packet capture file)?
9. What Wi-Fi attacks do you know? Describe how they work. 
10. What is «SSID Cloaking»? Does it protect a Wi-Fi access point?

---
links: [[600 SPA MOC|SPA MOC]] - [[themes/000 Index|Index]]