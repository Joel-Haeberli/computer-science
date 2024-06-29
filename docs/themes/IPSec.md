tags: #SPA #VPN 
 
# IPSec

links: [[616 SPA TOC - VPN|SPA TOC - VPN]] - [[themes/000 Index|Index]]

---

Open standard since 1995 (was sponsored by NSA befron from 1986 to 1991). With the current definition (RFC4301 from 2005). It supports 2 modes of operation Transport and Tunnel.

## Authentication Header (AH)

Provides data integrity, data origin authentication and anti-reply services but not confidentiality. Followed the IPv4 datagram with the AH (in red)

![[vpn-ipsec-ah-datagram.png]]

### Transport vs. Tunnel Mode

**Transport Mode**

- Keeps the IP header
- Authenticates payload but keeps routing information in the header
- Used for host-to-host communication

**Tunnel Mode**

- Authenticates the whole IP packet
- Generates a new header
- Used for VPNs

![[vpn-ipsec-ah-modes.png]]

In the middle the original packet. At top the transport mode packet and at the bottom the tunnel mode packet.

## Encapsulating Security Payload (ESP): 

Provides confidentiality, data integrity, data origin authentication and anti-reply services and limited traffic-flow confidentiality

### Header

![[vpn-ipsec-esp-header.png]]

### Transport vs Tunnel mode

![[vpn-ipsec-esp-modes.png]]

## Security Association (SA): 

Internet Security and Key Management Protocol (ISAKMP), framework for authentication and key exchange (the actual authentication is based on the "Internet Key Exchange Protocol Version 2" see below)

![[vpn-ipsec-rfcs.png]]

### IPv6

IPsec was developed with IPv6 in mind and was originally required to be supported by all standard-compliant implementations of IPv6, now it is only a recommendation.

- All IPv6 SHOULD support IPsec
- IPsec requires the implementation of manual and automatic key management
- The automated key management protocol at the moment is IKEv2

## Internet Key Exchange Protocol Version 2 (IKEv2)

- Certificate based authentication with X509 certificates
- Pre-Shared Keying (PSK)
- Extensible Authentication Protocol Methods (ESP, RFC3748) operations (Legacy Authentication mechanisms)

![[vpn-IKEv2.png]]

**Key Generation**

![[vpn-ipsec-ikev2-key-generation.png]]

**Authentication**

![[vpn-ipsec-ikev2-authentication.png]]

## Ciphers

**Symmetric encryption algorithms**

- Triple DES-CBC
- AES-CBC and AES-CTR
- AES-GCM and ChaCha20-Poly1305

**Authentication algorithms**

- RSA
- ECDSA
- PSK
- EdDSA

**Key exchange algorithms**

- Diffie-Hellman
- ECDH

**Hashing for integrity protection and authenticity**

- HMAC-SHA1/SHA2

## MTU

MSS (Maximum Segment Size) and MTU (Maximum Transmission Unit) are measurements of packet size. MTU = largest data packet a network device will accept. MSS = maximum payload without header.

- Packets that exceeds a networks MTU may be fragmented
- Packets that exceed the MSS are dropped
- For networks that use IPsec, either MSS and MTU have to be adjusted so the packets will not be fragmented
	- MTU is uesually 1500 bytes
	- IP header and TCP header are usually 20 bytes long so the payload can contain 1460 bytes
	- But IPsec adds an AH, an ESP header and associated trailers (around 50-60 bytes or more)
	- Tunneling interface MTU might be set to 1400 bytes

---
links: [[616 SPA TOC - VPN|SPA TOC - VPN]] - [[themes/000 Index|Index]]