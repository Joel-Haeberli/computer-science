tags: #netfilter #nftables

# nftables utility

links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]

---

##  Tables

- see available [[nftables#Tables|kind of families]]

```bash
nft list tables              # list all tables
nft list tables arp|ip|...   # list tables per family
nft list table ip myfilter   # list the content of a specific table

nft add table ip myfilter    # adding an IPv4 table named "myfilter"

nft delete table ip myfilter # delete tyle, table must be empty!

nft flush table ip myfilter  # flush the rules, clear all rules
```

## Chains

Possible chain types: `filter`, `route`, `nat`

### Base chain

- [[nftables#Base chain|base chain]]
- [[netfilter#Netfilter Hooks|Netfilter hooks]]

```bash
# add new base chain "myinput" to existing IPv4 table "myfilter"
# "myinput" is hooked to the netfilter "input hook"
nft add chain ip myfilter myinput { type filter hook input priority 0 ; }

# add new base chain with a default accept policy
nft add chain ip foo myoutput { type filter hook output priority 0 ; \
	policy accept; }
```

**Hook priority value**

![[nftables-priorities.png]]

### Regular or non-base chain

- [[nftables#Regular or non-base chain|regular or non-base chain]]

```bash
# add regular chain "myinput" to existing IPv4 table "myfilter"
nft add chain ip myfilter myinput

# delete an empty chain
nft delete chain ip myfilter myinput

# flush a chain (clear all rules)
nft flush chain myfilter myinput
```
## Rules

To add new rules, the table and the chain must be specified

```bash
# list rules and chains of a table
nft list table myfilter
nft -n list ... # no hostname resolution
nft -nn list ... # no hostname and service name resolution

# add new rules to the table "myfilter" and the chain "myoutput"
nft add rule myfilter myoutput ip daddr 8.8.8.8 counter
nft add rule myfilter myoutput tcp dport ssh counter
```

### Rule management

- to add, insert and remove rules at a given position the rule handle is required:
	- `add`: after the referenced rule
	- `insert`: at the place of the referenced rule
	- `delete`: the referenced rule
- use `flush` to empty a chain or a table

```bash
# print out the rule handles
nft -a list ...

# examples
nft add rule myfilter myoutput position 8 ip daddr 127.0.0.8 drop
nft insert rule myfilter myoutput position 9 ip daddr 127.0.0.1 drop
nft delete rule myfilter myoutput handle 5

# insert a rule at the first position of a chain
nft insert rule myfilter myoutput ip daddr 192.168.1.1 counter

# flush all rules of a chain
nft flush chain myfilter myoutput

# flush all rules of all chains of a table
nft flush table myfilter
```

### Expressions

nftables provides the following built-in operations:

- `ne`, `!=`: not equal
- `lt`, `<`: less than
- `gt`, `>`: greater than
- `le`, `<=`: less or equal than
- `ge`, `>=`: greater or equal than

```bash
nft add rule myfilter myinput tcp dport != 22
nft add rule myfilter myinput tcp dport >= 1024
```

### Selectors

- supported selectors for packet matching:
	- meta information: incoming/outgoing interface name/index/type, packet length, ...
	- header fields: layer 2 up to layer 4
	- connection tracking: conntrack
	- routing information
	- rate limiting matchings: per packet/byte or burst

### Actions

- Possible actions on packets:
	- **accepting and dropping** packets
	- **rejecting** traffic
	- **jumping to chain**
	- **counters**
	- **logging** traffic
	- performing **NAT**
	- setting packet/connection tracking meta information
	- mangling packet headers
	- duplicating packets
	- load balancing
	- queueing to userspace

Unlike iptables **multiple actions** may be performed in one single rule

## Advanced data structures

There are advanced data structures for **performance packet classification** (e.g. intervals, quotas, limits, timeout policies, ...)

## Backup & Restore
### Save Ruleset

- a ruleset is essentially **a collection of all the rules, chains and tables** that have been configured in nftables
- the first line in the backup file has to be a flush command (see example below)

```bash
nft list ruleset             # list completet ruleset
nft list ruleset arp|ip|...  # list ruleset per address family
nft flush ruleset            # flush the complete ruleset
nft flush ruleset arp|ip|... # flush ruleset per address family

echo "nft flush ruleset" > backup.nft  # add a flush to the ruleset entry
nft list ruleset >> backup.nft         # append the ruleset to save/restore
nft -f backup.nft                      # restore the ruleset from file
nft -j list [| json_pp] > ruleset.json # export in json format
```

### Save specific tables

- to (atomically) replace a rule set a `flush table myfilter` line must be added at the beginning of the file `myfilter-table`

```bash
# backup
echo "nft flush table myfilter" > myfilter-table
nft list table myfilter >> myfilter-table # add rules of table to file

# restore: atomically update rule set from a file
nft -f myfilter-table
```

## Examples

### IPv4 table examples

- the `ipv4-filter` and `ipv4-nat` of the nftables distribution provides an iptables-like filtering/nat structure

![[nftables-ipv4-filter-example.png]]

![[nftables-ipv4-nat-example.png]]
### Host firewall

**IPv4**

![[nftables-example-ip.png]]

**IPv6**

![[nftables-example-ip6.png]]

**inet**

![[nftables-example-inet.png]]

---
links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]