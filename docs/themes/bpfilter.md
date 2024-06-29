tags: #bpfilter
# bpfilter

links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]

---

## eBPF

- **Extended Berkeley Packet Filter** is a Linux kernel technology that allows running custom programs inside the kernel in a sandboxed environment without changing kernel source code or loading kernel modules
- Use cases: Security, Networking, Tracing and Profiling, Observability & Monitoring (Kubernetes)
- **Security**: eBPF can see and intercept all system calls and filter them, has also a packet and socket-level view for network-level filtering or process context tracing
- **Networking**: eBPF enables to implement protocol parsers or any kind of forwarding logic without leaving the packet processing context of the Linux kernel

![[ebpf-overview.png]]
## bpfilter

- uses **eBPF**
- filtering capabilities are implemented as an interpreter program for the BPF virtual machine
- the BPF program can be attached to points in the network packet path like:
	- the eXpress Data Path **(XDP)** layer, where they are **run from the network-interface drivers**
- the BPF virtual machine can run in user space or in kernel space

## Measurements

- Some PoC applications show performance improvements of up to 3 to 6 times over [[iptables]] or [[nftables]].

![[bpfilter-measurement.png]]

---
links: [[606 SPA TOC - Linux Firewall|SPA TOC - Linux Firewall]] - [[themes/000 Index|Index]]