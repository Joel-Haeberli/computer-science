tags: #netfilter #iptables

# iptables

links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]

---

## Overview

- iptables provides a **generic table structure** for the **definition of rule sets and rule chains**
- each table contains **built-in rule chains**
- each table may also contain **user-defined chains**

## Generic tables

- `filter` for the filtering of packets
- `nat` for the altering of addresses in packet headers
- `mangle` for a specialized manipulation of packets
- `raw` for an exceptional dealing with raw packets

## Predefined chains

- `INPUT`: packets for local processes ([[netfilter#Netfilter Hooks|netfilter]] hook # 2)
- `OUTPUT`: packets from local processes ([[netfilter#Netfilter Hooks|netfilter]] hook # 4)
- `FORWARD`: forwarded packets ([[netfilter#Netfilter Hooks|netfilter]] hook # 3)
- `PREROUTING`: incoming packets before routing ([[netfilter#Netfilter Hooks|netfilter]] hook # 1)
- `POSTROUTING`: outgoing packets after routing ([[netfilter#Netfilter Hooks|netfilter]] hook # 5)

## Architecture

See all tables: [[iptables table architecture]]

![[iptables-architecture.png]]

## Firewall rules

- A firewall rule specifies:
	- one or multiple **criteria/matches for a traversing packet**
	- one **action/target**
- if the packet does not match the criteria's, the next rule in the chain is examined
- If it does match, then the next rule or action is specified by the value of the target

### Targets

- `ACCEPT`: packet is let through (no further processing of the following rules)
- `DROP`: packet is dropped (no further processing of the following rules)
- `QUEUE`: packet is passed to the user space
- `RETURN`: means stop traversing this chain and resume at the next rule in the previous/calling chain
- call of a user-defined chain
- iptables can use **extended target modules** (e.g. `AUDIT`, `DNAT`, `CT`, ...)

![[iptables-user-chain-return.png]]

## Default policy

- every built-in chain has a default policy
- user-defined chains cannot have a default policy

![[iptables-default-policy.png]]

## Administration of chains and rules

- the utility `iptables`is used
- see [[iptables utility]]

---
links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]