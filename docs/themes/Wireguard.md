tags: #SPA #VPN 
 
# WireGuard

links: [[616 SPA TOC - VPN|SPA TOC - VPN]] - [[themes/000 Index|Index]]

---

>Can I just once again state my love for WireGuard and hope it gets merged soon? Maybe the code isn’t perfect, but I’ve skimmed it, and compared to the horrors that are OpenVPN and IPSec, it’s a work of art.
>-- Linus Torvalds

## General

- WireGuard requires only around 4000 lines of code!!!
- Encapsulates IP packets within UDP
- Multi platform support for all current desktop and mobile OS (Windows, macOS, Linux, Android, IOS)
- Operates with a fixed suite of cryptographic primitives:
	- Symmetric encryption: [[Authenticated Encryption#ChaCha20-Poly1305|ChaCha20-Poly1305]] using RFC7539 [[Authenticated Encryption#Authenticated encryption with associated data|AEAD]] construction
	- [[Cryptographic Hash Functions#BLAKE|BLAKE2]] for (keyed) hashing
	- ECDH with Curve25519
	- Key derivation with [[Key Derivation Function (KDF)#KDF using HMAC (HKDF)|HKDF]]
- Interoperable with other VPNs such as [[IPsec]] and PPTP
- Easy setup

## Configuration

**Typical Server configuration**

```
[Interface]
PrivateKey = yAhhud43+fdXX... dfUH7fjH=
ListenPort = 51820

[Peer]
PublicKey = HkduHU3Ooeioa33...Jbdd32=
AllowedIPs = 10.192.122.4/32, 10.192.34.1/24

[Peer]
PublicKey = Dkjfhsd7dsjfhds...jhdu63=
AllowedIPs = 10.192.122.5/32, 192.168.0.0.16
```

**Typical client configuration**

```
[Interface]
PrivateKey = gI6Edfui3...iZxIhp3Gfdhui3
ListenPort = 21841

[Peer]
PublicKey = HiHDhidid...6dsiegg7
Endpoint = 192.95.5.69:41414
AllowedIPs = 0.0.0.0/0
```

## Setup example

```bash
#Setup virtual Wiregurard interface
ip link add dev wg0 type wireguard
wg genkey >pkey
wg set wg0 private-key ./pkey

#Add IP address and start up interface
ip addr add dev wg0 192.168.1.200/24
ip link set wg0 up

#Add peer
wg set wg0 peer
D3MFdfihF873dfjasKJDLKdakjldja/384ADhjiudd= allowed-ips 192.168.1.0/24 endpoint 192.168.68.185:55779
```

## Routing

![[vpn-wireguard-routing.png]]

## Noise Key Exchange

Each session begins with a handshake based on the Noise framework. This handshake takes only 1-RTT (Round Trip Time):

![[vpn-wireguard-noise-key-exchange.png]]

Definitions (Below in the Basic idea section you will find the missing keys and where they come from):

![[vpn-wireguard-noise-key-exchange-definitions.png]]

### Basic Idea

Triple DH like the Signal Protocol + one for the 1-RTT

![[vpn-wireguard-key-exchange-basic.png]]

**Initiator**

- Long term static EC key pair ($s_i$ , $g^{s_i}$)
- Ephemeral EC key pair ($e_i$ , $g^{e_i}$)
- 4 derived key pairs
	- k1 $\leftarrow$ $g^{e_i s_r}$
	- k2 $\leftarrow$ $g^{s_i e_r}$
	- k3 $\leftarrow$ $g^{e_i e_r}$
	- k4 $\leftarrow$ $g^{s_i s_r}$
	- The keys for this symmetric transport encryption are generated using HMAC-based Extract-and-Expand Key Derivation Function (HKDF)
		- $tk_i$ ← HKDF(C9 , 0x01)
		- $tk_r$← HKDF(C9 , $tk_i$ ||0x02)

The initiator sends to the responder:

- His ephemeral public key $g^{e_i}$
- AEAD encrypted data with a key derived from $g^{e_i s_r}$
	- This transport encryption is done using ChaCha20 as symmetric encryption authenticated by Poly1305
	- AEAD.Enc($tk_i$ , counter$_i$ , encapsulated packet)
- A increasing counter authenticated-encrypted using a key derived from $g^{s_i s_r}$

**Responder**

- Long term static EC key pair ($s_r$ , $g^{s_r}$)
- Ephemeral EC key pair ($e_r$ , $g^{e_r}$)
- 4 derived key pairs
	- k1 $\leftarrow$ $g^{e_i s_r}$
	- k2 $\leftarrow$ $g^{s_i e_r}$
	- k3 $\leftarrow$ $g^{e_i e_r}$
	- k4 $\leftarrow$ $g^{s_i s_r}$
	- The keys for this symmetric transport encryption are generated using HMAC-based Extract-and-Expand Key Derivation Function (HKDF)

The responder sends back to the initiator:

- His ephemeral public key $g^{e_r}$
- Empty buffer, authenticated-encrypted using a key derived from $g^{e_i e_r}$ and $g^{s_i e_r}$

### Key rotation

The symmetric session keys are constantly rotated:

![[vpn-wireguard-key-rotation.png]]

## Containerization

WireGuard integrates into the network namespace infrastructure so Namespacing tricks can be used:

- Assign only the WireGuard interface to a container
- Let DHCP touch only physical interfaces
- Let your web browser see WireGuard interfaces
- Nice alternative to routing table hacks

![[vpn-wireguard-containerization.png]]

## WireGuard/VPN Topologies

### Point to Point

Direct connection or connection via Internet

![[vpn-point-to-point.png]]

### Site to Site

![[vpn-site-to-site.png]]
### Dynamic Multipoint - Hub and Spoke

Two endpoints are connected through a third host (also known as Star Topology)

![[vpn-hub-spoke.png]]

---
links: [[616 SPA TOC - VPN|SPA TOC - VPN]] - [[themes/000 Index|Index]]