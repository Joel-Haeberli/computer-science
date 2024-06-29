tags: #auth 

# Kerberos Delegation

links: [[620 SPA TOC - Kerberos|SPA TOC - Kerberos]] - [[themes/000 Index|Index]]

---

## Kerberos Delegation

- Delegation is a standard built-in mechanism of kerberos
- Allows a service to act on behalf of a user when talking to other services $\rightarrow$ "user impersonation"
- Delegation is transparent
	- Users can't control whether delegation will occur or not
	- Users can't detect whether delegation happened or not
	- Delegation happens at the discretion of the service

![[kerberos-10.png]]

### Unconstrained delegation

- When accessing a service with unconstrained delegation a copy of the users TGT is sent together with the ST

![[kerberos-12.png]]

- A copy of the TGT with a new session key (pink key in [[Kerberos Introduction#Complete process in detail|Introduction]]) needs to be used instead of the actual user TGT because of security principles (separation, service can't have the same ticket as the user)
- Service can now impersonate users against any service

![[kerberos-11.png]]

- Configured on the domain object (delegating service user or machine)
- **Risks**
	- "Unconstrained" $\rightarrow$ insecure by definition
	- Unconstrained services are high-value targets for attackers
	- Impact depends on the permissions of the delegated account
	- Attacker can abuse delegated TGTs when he has control over the local admin, the target machine or the service user account
	- Attackers can either target cached TGTs or convince users / machines to connect to the service and then steal their TGT copies
	- ARP poisoning, DNS poisoning, PrinterBug etc. can be used to make a victim send the copy of the TGT to the attacker instead of the intended service
	- Best case scenario: Don't use unconstrained delegation

![[kerberos-13.png]]

- **DCSync attack**: Once the attacker has obtained domain admin-level access through the PrinterBug exploit, they can then execute a DCSync attack. This involves using tools like Mimikatz to impersonate a Domain Controller and request user credential data from a legitimate Domain Controller. The attacker get sensitive information like hashed user credentials back.

### Constrained Delegation

- Services can impersonate users against specific services (target restrictions)
- Two types of constrained delegation
	- Exclusive Kerberos authentication
	- Transition from different protocol (e.g. NTLM) to kerberos

![[kerberos-14.png]]

- Configured on the domain object (delegating service user or machine)

#### Kerberos Only

- Microsoft added a protocol extension called **S4U2Proxy**, used for constrained delegation
- S4U2Proxy replaces the TGT forwarding mechanism of unconstrained delegation
- The service can obtain a service ticket on behalf of a user for another service
- S4U2Proxy
	- Delegation should only happen, if the user is present (if the user has effectively connected to the delegation service) $\rightarrow$ "proof" of a user's presence
	- This proof comes in the form of a regular ST
	- ST needs to be flagged FORWARDABLE (default for regular ST unless the user is in the Protected Users group or flagged as sensitive)

![[kerberos-15.png]]

- **Risks**
	- Similar to unconstrained delegation but attacker can only impersonate the victim on configured services (services that the compromised service is allowed to delegate)
	- Requirements
		- Attacker mus have control over the account enabled for constrained delegation
		- A user must actively connect to the target account with kerberos authentication

![[kerberos-16.png]]

#### Protocol Transition

- Initial user authentication can take any form
	- NTLM
	- Username & Password Login on a website
	- Federated authentication via an IDP (e.g. SAML / OpenID Connect)
- Problem: Delegating service can't invoke S4U2Proxy because there is no Kerberos ST
- Solution: S4U2Self
	- Allows a service to get a ST on behalf of a user to itself (ST represents the user's presence)
	- This ST can then be used to invoke S4U2Proxy
- Problem: User authentication is not required
	- The delegating service can impersonate users "out of thin air"

![[kerberos-17.png]]

- S4U2Self does not require specific permission $\rightarrow$ anyone can request an ST from some user to itself
- The ticket is only tagged as FORWARDABLE (usable for S4U2Proxy) if:
	- The requesting account is configured for constrained delegation with protocol transition (TrustedToAuthForDelegation UAC flag is set)
	- The target is not flagged as sensitive
	- The target is not in the Protected Users Group
- The resulting S4U2Self ST contains the users authorization data (PAC)
	- This allows authorization decisions to be performed without pre-authentication
- **Risks**
	- Delegation service can impersonate any user without user interaction against any allowed service
	- Requirements
		- Attacker must have control over the account configured for constrained delegation
		- Attacker must know the SPN of the account they want to impersonate

![[kerberos-18.png]]

### Resource-based Constrained Delegation (RBCD)

- Services decides which services can impersonate users (reverse of constrained delegation)

![[kerberos-20.png]]

- Configured on the domain object (delegating service user or machine)
- Computer accounts can configure RBCD for delegating services on themselves with *msDS-AllowedToActOnBehalfOfOtherIdentity* attribute
- Delegating services still use S4U2Self & S4U2Proxy but different validation rules and checks are performed by KDC

![[kerberos-21.png]]

- **Risks**
	- Similar risks as constrained delegation
	- Delegating service can still impersonate any user without user interaction
	- Requirements
		- Attacker must have control over the account configured for RBCD delegation
		- Attacker must know the SPN of the account they want to impersonate

### Substituting Services

- In a ST the information about the target service is not encrypted
- The encrypted part does not contain any information about the target service
- Windows decides which ticket to use for authentication based on "meta-data" within the ticket
- **Implication**
	- An attacker can substitute any valid service on the same target
	- If a target device hosts a HTTP and a MSSQL service and the attacker only has an ST for HTTP then he can simply change HTTP to MSSQL which results in a valid ticket for MSSQL
***Not sure if this is correct, confusing slides***
![[kerberos-19.png]]

### Restrictions

- **Sensitive Users**
	- Accounts can be flagged as **sensitive**
	- Sensitive accounts can't be delegated
	- This setting is off by default
- **Protected Users Group**
	- Built-in group in AD (only for users, not services / machines)
	- Designed to restrict credential exposure
	- Prevents caching of plain text credentials
	- Prevents NTLM authentication
	- Disables weak ciphers (DES / RC4)
	- Prevents delegation
	- Restricts life-time of authentication material
	- Group is empty by default

### Recommendations

- Make use of Protected Users Group for high privileged accounts (delegation is deactivated for accounts in this group)
- Delegating services need to be protected as strongly as the DC
- Reduce permissions available to account (least privilege principle)
- Disable print spoolers + similar triggers on all systems where possible
- Implement monitoring measures for high value accounts and systems with delegation rights
- Use most restrictive delegation option
	- unconstrained > "protocol transition" constrained > "kerberos only" constrained > resource-based constrained

---
links: [[620 SPA TOC - Kerberos|SPA TOC - Kerberos]] - [[themes/000 Index|Index]]