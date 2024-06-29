tags: #lab

# Lab 1 - Logging, tcpdump, nmap

links: [[609 SPA TOC - Lab|SPA TOC - Lab]] - [[themes/000 Index|Index]]

---

## Exercise  RFC 5424 syslog

**PRI = Facility × 8 + Severity**

1. 19
	* Facility: 2, Severity: 3
	* user-level messages - Error
2. 135
	* Facility: 16, Severity: 7
	* local use 0 - Debug
3. 28
	* Facility: 3, Severity: 4
	* system daemons - Warning
4. 0
	* Facility: 0, Severity: 0
	* kernel messages - Emergency

## Exercise central log server

Ports are open on the mail server:

> - nft list table inet nslab
> - tcp dport 514 ct state new counter packets 0 bytes 0 accept comment "syslog - TCP"
> - udp dport 514 ct state new counter packets 0 bytes 0 accept comment "syslog - UDP"

Config file mail server:  

```
# from-remote.conf  

# Provides UDP syslog reception
module(load="imudp")
input(type="imudp" port="514")

# Provides TCP syslog reception
module(load="imtcp")
input(type="imtcp" port="514")
```

Testing the mail server:

> logger "This is a test message"
> logger -p user.info "This is an informational message"
> tail -f /var/log/syslog

Configuration of the router:  

```
# to-remote.conf

# TCP
*.* @@147.87.86.67:514

# UDP
# *.* @147.87.86.67:514
```

TCP gives error messages if the server is not reachable, while UDP does not.

```
# rules.conf
# Be aware of the rules in the default configuration (rsyslog.conf)

if $programname == 'sshd' then /var/log/sshd.log
& stop

$template RemoteLogs,"/var/log/remote/%HOSTNAME%.log"

if $fromhost-ip != '127.0.0.1' then -?RemoteLogs
& stop

auth,authpriv.* /var/log/auth_log
*.warn /var/log/warn_log
```

```
# Server
module(load="imrelp") # Load RELP input module
input(type="imrelp" port="2514") # Listen for RELP on port 2514

# Client
module(load="omrelp")
*.* action(type="omrelp" target="147.87.86.67" port="2514")
```

## Exercise syslog originator/client for Windows

Going with the "Rsyslog Windows Agent" option:

```
root@mail:/etc/rsyslog.d# tail -f /var/log/remote/client02.log
2024-01-18T10:20:18+01:00 client02 RSyslog Windows Agent: This is a SyslogTest
2024-01-18T10:20:52+01:00 client02 RSyslog Windows Agent: This is a SyslogTest
```

The syslog agent needs to map the Windows event log to the syslog specification.

## Exercise logrotate

```
{
	rotate 4 # Keep 4 rotated files
	size 500k # Rotate when file size is 500k
	weekly # Rotate weekly
	missingok
	notifempty
	compress
	delaycompress
	sharedscripts
	postrotate
	/usr/lib/rsyslog/rsyslog-rotate # reload rsyslog after rotation
	endscript
}
```

## Exercise logwatch

[Arch Wiki](https://wiki.archlinux.org/title/Logwatch)
  
```
logwatch --detail High

root@mail:/usr/share/logwatch/default.conf/services# cat syslog-manual.conf
Title = "Just Testing"
LogFile = syslog

root@mail:/usr/share/logwatch/scripts/services# cat syslog-manual
#!/bin/bash
cat

logwatch --service syslog-manual --detail High
```

## Exercise LogAnalyzer

```bash
apt-get install apache2 php php-cli
curl https://download.adiscon.com/loganalyzer/loganalyzer-4.1.13.tar.gz --output log.tar.gz
tar -xvzf log.tar.gz
systemctl enable apache2.service
systemctl start apache2.service
mv loganalyzer-4.1.13/src /var/www/html/log
mv loganalyzer-4.1.13/contrib/* /var/www/html/log
cd /var/www/html/log
bash configure.sh
usermod -a -G adm www-data
systemctl restart apache2
```

Access the web interface at `http://147.87.86.67/log`

## Exercise systemd-journald

See here: [centralize logs with journald](https://www.digitalocean.com/community/tutorial-collections/how-to-centralize-logs-with-journald)

- install package `systemd-journal-remote` on client and server
- create necessary firewall rules on hosts
- create certificates on client and server (e.g. with certbot)
- *server*: configure journal-remote system daemon to use correct certificates
- *client*: create user for daemon with rights to the certificates, configure journal-remote system daemon with 

## Exercise tcpdump

```
tcpdump -i ens192 -w dhcp.pcap port 67 or port 68
tcpdump -i ens192 -w dns.pcap port 53
tcpdump -i ens192 -w ssh.pcap port 22
tcpdump -i ens192 -w traceroute.pcap icmp
tcpdump -i ens192 -w traceroute2.pcap icmp or udp
tcpdump -i ens192 -w tcptraceroute.pcap tcp
```

## Exercise password sniffing

Won't work with `sftp` because it's encrypted.

```
# Mail

apt install vsftpd
vim /etc/vsftpd.conf (Set listen=YES, listen_ipv6=NO)
systemctl restart vsftpd
adduser ftpuser # 12345

# Update nftables:
tcp dport 21 ct state new counter packets 0 bytes 0 accept comment "FTP"

chain OUTPUT {
      tcp sport 20 ct state established,related counter packets 0 bytes 0 accept comment "FTP Active Mode"
}

systemctl restart nftables
sudo tcpdump -i ens192 'port 21' -A

# Password visible as --> "PASS 12345"

# Router

apt install ftp
ftp 147.87.86.67
# Username: ftpuser
# Password: 12345
```

## Exercise nmap

```bash
nmap -sn 147.87.80.0/21
# Nmap done: 2048 IP addresses (119 hosts up) scanned in 17.41 seconds

nmap -sn 147.87.80.0/24
# Nmap done: 256 IP addresses (31 hosts up) scanned in 1.78 seconds

nmap -sn 147.87.86.64/28
# Nmap done: 16 IP addresses (5 hosts up) scanned in 1.27 seconds

nmap -O -v # OS detection and uptime guess. MAC address sometimes gives away if it's a VM or not.

nmap -sS --open # TCP SYN scan
nmap -sT --open # TCP connect scan
nmap -sU --open --top-ports=100 # UDP scan
```

More commands: [https://www.stationx.net/nmap-cheat-sheet/](https://www.stationx.net/nmap-cheat-sheet/)

## Exercise nmap and IPv6

```bash
nmap -6 -sn
nmap -6 -p 1-1000 -A 2001:620:500:ffad::30
```

The vast address space of IPv6 introduces challenges that require a more targeted and selective approach to scanning, as opposed to the blanket scanning often seen in IPv4.

* **ZMap** is another open-source network scanner that can be used for IPv6 scanning. It's known for its speed and efficiency in scanning large IPv6 address spaces.
* **Masscan** is a high-speed scanner that can be used for both IPv4 and IPv6 scanning. It's particularly useful for scanning large networks quickly.
* **Scapy** is a Python-based packet manipulation tool that can be used for crafting custom IPv6 packets and scanning networks. It provides a lot of flexibility for network exploration.

## Exercise Greenbone OpenVAS

```bash
systemctl enable --now gsad.service
systemctl enable --now gvmd.service
systemctl enable --now ospd-openvas.service
greenbone-feed-sync
gvm-start

# https://localhost:9392

runuser -u _gvm -- gvmd --get-get-scanners
runuser -u _gvm -- gvmd --get-get-users --verbose
runuser -u _gvm -- gvmd --get-modify-scanner 08b69003-5fc2-4037-a479-93b440211c73 --value b7d2b4a1-588e-4237-af7e-4d68c14b1b24

# Somehow the scan configs are not there: (go to /feedstatus. Still updating)
# But yeah I leave it at that... you could make some scans then.
```

---
links: [[609 SPA TOC - Lab|SPA TOC - Lab]] - [[themes/000 Index|Index]]