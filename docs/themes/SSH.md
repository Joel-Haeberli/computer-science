tags: #SPA #ssh
 
# SSH

links: [[614 SPA TOC - Secure Shell|SPA TOC - Secure Shell]] - [[themes/000 Index|Index]]

---

## History

- Created in 1995 (SSH version 1)
- Quickly became a popular replacement for the insecure telnet, witch does not offer server authentication and an encrypted channel.
- After 5 years the number of users grown to 2 million
- Version 2 of the protocol split it into transport, connection and authentication layers

## Protocol Stack

![[SSH-protocol-stack.png]]

## Sequence Diagram

![[SSH-sequence-diagram.png]]

## Transport Layer

- Defined in RFC 4253
- The transport layer provides algorithm negotiation, key exchange and server authentication and sets up a secured connection that provides integrity, confidentiality and optional compression
- For key exchange Diffie-Hellman is used (ensures forward secrecy)
- The server authentication is based on RSA or DSS signatures

![[ssh-transport-layer.png]]

## X509v3 To SSH Public Key

```bash
#Extracting public key
openssl x509 -pubkey -in fsb2.pem -noout >  fsb2.pub

#Convert public key to OpenSSH public key
ssh-keygen -i -m pkcs8 -f fsb2.pub > SSH-pub-key.pub
```

## Initial Server Key Discovery

- When a client connects to the server for the first time it asks to verify the server key:

```bash
ssh -I /usr/local/lib/libykcs11.dylib
user@client01.n025.nslab.ch
The authenticity of host ’client01.n025.nslab.ch (147.87.84.14)’ cannot be established.
ED25519 key fingerprint is SHA256:xXsXRnH95YzncFcUgm4JuSS5epHz+1R+auOgBOLYkbU.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

- This is done to prevent impersonation attack or man-in-the-middle attack

## Authentication Layer

- Defined in RFC 4252
- Provides mechanisms for user authentication:
	- Password based authentication
	- Public key based authentication
	- Keyboard interactive
	- Generic Security Services API (GSSAPI)

## Connection Layer

- Defined in RFC 4254
- It provides:
	- interactive login session
	- remote execution commands
	- Files transfer via scp and sftp
	- Tunneling and forwarding TCP connections
	- Forward X11 connections
- These channels are multiplexed into a single encrypted channel

## SSH Forward/Reverse

```bash
#Forward
ssh -L8080:10.0.0.1:80 user@147.87.242.199

#Reverse
ssh -R8080:localhost:80 user@147.87.242.199
```

![[ssh-forward-reverse.png]]

---
links: [[614 SPA TOC - Secure Shell|SPA TOC - Secure Shell]] - [[themes/000 Index|Index]]