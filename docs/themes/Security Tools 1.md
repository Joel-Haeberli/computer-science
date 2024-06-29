tags: #SPA #tools 
 
# Security Tools 1

links: [[608 SPA TOC - Security Tools|SPA TOC - Security Tools]] - [[themes/000 Index|Index]]

---

## Syslog

- Invented in 1980's
- Standard specification about forwarding "log messages" in an IP network
- Syslog protocol is Client $\leftrightarrow$ Server 
- Default port: UDP 514

### Syslog Layers

- **syslog content** (message)
	- The management information contained in a syslog messages
- **syslog application**
	- Responsible for generation, interpretation, routing, and storage of syslog messages
- **syslog transport**
	- Responsible for transporting the messages

### Syslog Components

- **Originator** = Client $\rightarrow$ sends the message
- **Relay** = Receives the message $\rightarrow$ processes it $\rightarrow$ forwards it (All according to its configuration)
- **Collector** = Server $\rightarrow$ write the message to the file/DB/... 

### Syslog Header

**PRI** (for Priority) (must):

PRI is a calculated value 

$$PRI=Facility \cdot 8 + Severity$$

Example: MAIL.INFO = $2\cdot8+6$

**PRI - Facility**

| Numerical Code | Facility |
| ---- | ---- |
| 0 | kernel messages |
| 1 | user-level messages |
| 2 | mail system |
| 3 | system daemons |
| 4 | security/authorization messages |
| 5 | messages generated internally by syslog |
| 6 | line printer subsystem |
| 7 | network news subsystem |
| 8 | UUCP subsystem |
| 9 | clock daemon |
| 10 | security/authorization messages |
| 11 | FTP daemon |
| 12 | NTP subsystem |
| 13 | log audit |
| 14 | log alert |
| 15 | clock daemon |
| 16 - 23 | local use 0 - 7 (local0 - local7) |

**PRI - Severity**

| Numerical Code | Severity |
| ---- | ---- |
| 0 | Emergency: system is unusable |
| 1 | Alert: action must be taken immediately |
| 2 | Critical: critical conditions |
| 3 | Error: error conditions |
| 4 | Warning: warning conditions |
| 5 | Notice: normal but significant condition |
| 6 | Informational: informational messages |
| 7 | Debug: debug-level messages |

- **Version** (must): A IANA assigned version number. RFC5424 uses version 1
- **Timestamp** (must): Date followed by uppercase T followed by time and maybe time zone
- **Hostname** (must):
	- FQDN
	- IP Address
	- Hostname
	- NIL Value (NULL)
- **Application name** (should): Name of the application gathering the log message
- **Process ID** (should): Numerical value representing the PID (normally) of the application gathering the log message
- **Message ID** (should): Message type to identify the message

### Syslog MSG/Message

> Anything can be a syslog message

UTF-8 for data and messages text

Syslog message up to 480 Octets must be accepted but 2048 should be accepted

### Syslog implementations

**UNIX/LINUX**

- syslog-ng
- rsyslog
- sysklogd
- systemd (journald)
	- Default journal service of Linux systems (which uses systemd)
	- Replacement for rsyslog
	- Received from variety of sources:
		- Kernel log messages (kmsg)
		- simple system log messages (libvc syslog)
		- structured system log messages (Journal API)
		- standard output and standard error of service units
		- audit records
	- can be queried with journalctl
	- stored in `/var/log/journal`
	- can be sent to remote server using systemd-journal-upload

**Windows**

- NTsyslog
- Kiwi Syslog
- Win Syslog
- Megalog Suite
- Rsyslog Windows Agend

**Frontends**

- LogAnalyzer
- ELK Stack (Elasticsearch Logstash Kibana)
- Logzilla NEO
- Splunk
- Grafana Loki

## TCPDUMP

Command-line packet analyzer

```bash
tcpdump <options> <filter>
```

options:

- `-n` no dns resolution
- `-i` interface to listen on
- `-s` snaplen
- `-w` write out to file
- `-v` verbose
- `-Z` drop privileges to user
- `-D` available network interfaces
- `-e` print link-level header
- `-F` use file as input to filter expression
- `-p` Dont put interface into "promiscuous" mode
- `-r` Read packets from file

- **filter** = pcap filtering language using
- **filter expressions** = consists of one or more primitives
- **primitives** = consists of an id (name or number) and one or more qualifiers. Special primitives = gateway, broadcast, less, greate
- **qualifiers**: one of... 
	- type: qualifiers say what kind the id refers to (host, net, port, portrange)
	- dir(direction): qualifier specify a transfer direction (src, dst, src | dst, src, dst)
	- or proto(protocol): qualifier restrict the match to a protocol (ether, wlan, ip, ip6, arp, rarp, tcp and udp, ...)

## Wireshark

- Network packet/protocol analyzer for Unix/Linux, OS X and Windows
- Based on libpcap/npcap with graphical frontend
- Open-Source
- Licence = GPL

**Use Cases**

- Troubleshoot network problems
- Examine security problems
- Verify network applications
- debug protocol implementations
- Learn network protocol internals

**Features**

- Capture packet data from network interface
- Open pcap files from different sources (tcpdump/WindDump, Wireshark and others)
- Import hex dumps of packet data
- Display packets
- Save packet data
- Export packet data
- Filter packets
- Search packets
- Create statistics

**Capture Sources**

- Ethernet
- 802.11 Wireless LAN
- Bluetooth
- USB interfaces

**Filters**

There are two different types of filters **Capture** filters (during capture time) and **Display** filters (can be used to analyze captured traffic). They use different filter languages.

**TShark**

TShark is the command-line interface of wireshark.

## Nmap

Nmap is a free network security scanner. Allows network-wide ping sweep, port, OS detection scans

Syntax:

```bash
nmap <options> <targets>

Options:
-P0 do not ping
-sT connect scan
-sP ping scan
-v verbose
-O guess OS
-sS syn stealth scan
-sV service version scan
```

**TCP State Machine**:

![[TCP-State-Machine.png]]

## Vulnerability scanner

**Nessus**

- Plugin based
- Client server structured
- network assessment and discovery
- patch, configuration and content auditing

**Greenbone OpenVAS**

- Pendant to Nessus but open-source
- Part of the Greenbone Security manager (GSM)

## Honorable mentions

- THC amap = service scanner with version detection
- netcat = network debugging and exploration tool
- Metasploit = Open-Source platform for developing testing and using exploits
- hping2 = Network tool to send custom TCP/IP packets
- xprobe2 = Operating system fingerprinting tool
- firewalk = Reconnaissance network security tool to test layer 4 services forwarded by firewalls
- scrapy = Interactive packet manipulation tool, packet generator, network scanner, network discovery tool and packet sniffer

[Top 125 Network Security Tools](https://sectools.org/)

---
links: [[608 SPA TOC - Security Tools|SPA TOC - Security Tools]] - [[themes/000 Index|Index]]