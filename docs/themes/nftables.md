tags: #nftables

# nftables

links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]

---

## Overview

- nftables replace the existing iptables framework
- provides a new packet filtering framework, new utility `nft`, a compatibility layer for ip/ip6tables (**allows to run iptables/ip6tables over the nftables infrastructure**)
- build upon the [[netfilter]] infrastructure:
	- the existing [[netfilter#Netfilter Hooks|hooks]]
	- the [[Connection Tracking Subsystem]]
	- the userspace queueing component
	- the logging subsystem

### Main features

- pseudo-state machine in kernel-space
- **fast lookups**
- reduces the amount of code in kernel space
- **unified interface** `nft`
- nftables is **still under development** (v1.0.0 was releases in 2021)

## Main differences between iptables/nftables

- new **cleaner syntax**
- tables and chains are **fully configurable**
- **no distinction between matches and targets** anymore
- several actions in **one single rule** can be specified (e.g. `log drop`)
- no built-in counter per chain and rules $\rightarrow$ counters can be enabled (per rule) on demand
- generic set infrastructure (e.g. `{ssh, http, https}`)
- new protocols are supported without kernel upgrades

## Tables

- the **table** objects are **containers for chains, sets, and stateful objects**
- there are **no predefined tables** anymore (e.g. `filter`, `raw`, ...)
- different kind of table families:
	- `ip`: IPv4
	- `ip6`: IPv6
	- `inet`: IPv4 & IPv6
	- `arp`: ARP
	- `bridge`: Bridge address family (bridge device)
	- `netdev`: Netdev address family (ingress or egress)

## Chains

- chains are used to **store rules** and are highly configurable
- possible **chain types** are:
	- `filter`: filter packets, supported by all table families
	- `route`: reroute packages, supported by `ip` and `ip6` family
	- `nat`: perform NAT, supported by `ip`, `ip6` and `inet` family
- for every chain type, following **chain kind** exist: **base chains** and **regular or non-base chains**

### Base chain

- base chains are registered into the [[netfilter#Netfilter Hooks|Netfilter Hooks]]
- a default policy of `accept` or `drop` can be specified for each chain
- the **priority value** can be used to **order the chains** or to put them before or after some Netfilter internal operations

### Regular or non-base chain

- are **not attached to any hook**
- not see any traffic at first
- is very useful to **arrange rule-sets** in a tree of chains by using the `jump` or `goto` action
- works like a user defined chain of iptables

## Limitations of netfilter/ iptables/ nftables

- modern technologies like container virtualization environments require **highly dynamic changes and very fast processing** of firewall rulesets
- the packet filtering framework (netfilter/iptables/nftables) **slows down when large rules sets are used** because of sequential processing of the rules
- if large rule sets are changed very often, the installation duration of the rule sets delays the processing
- for this reason, a new filtering framework [[bpfilter]] is in development

---
links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]