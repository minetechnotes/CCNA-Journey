NAT \& Subnetting



\## Overview



Basic summary of \*\*NAT\*\*, \*\*Subnetting\*\*, \*\*VLSM\*\*, and IP planning.



```text

NAT        = Private IP → Public IP

Subnetting = Large network → Smaller networks

VLSM       = Different subnet sizes based on need

```



\---



\## NAT



\*\*NAT\*\* allows private devices to access the internet using a public IP.



| Type               | Function                                       |

| ------------------ | ---------------------------------------------- |

| Static NAT         | 1 private IP = 1 public IP                     |

| Dynamic NAT        | Private IPs use a public IP pool               |

| PAT / NAT Overload | Many private IPs share 1 public IP using ports |



\### Basic PAT Config



```cisco

access-list 1 permit 192.168.1.0 0.0.0.255



interface ethernet0/0

&#x20;ip nat inside



interface ethernet0/1

&#x20;ip nat outside



ip nat inside source list 1 interface ethernet0/1 overload

```



\### Verify



```cisco

show ip nat translations

show ip nat statistics

```



\---



\## Subnetting



\*\*Subnetting\*\* splits a large network into smaller networks.



\### Benefits



\* Saves IP addresses

\* Reduces broadcast traffic

\* Improves security

\* Makes troubleshooting easier

\* Supports growth



\### Common CIDR



| CIDR | Usable Hosts |

| ---- | -----------: |

| /24  |          254 |

| /26  |           62 |

| /27  |           30 |

| /30  |            2 |



\---



\## Subnet Rule



```text

Mask → Increment → Range → Network \& Broadcast

```



Example:



```text

IP:        192.168.5.22

Mask:      255.255.255.240

Increment: 16



Network:   192.168.5.16

Hosts:     192.168.5.17 - 192.168.5.30

Broadcast: 192.168.5.31

```



\---



\## VLSM



\*\*VLSM\*\* uses different subnet sizes in one network.



```text

50 hosts → /26

20 hosts → /27

2 hosts  → /30

```



Rule:



```text

Start from the largest subnet first.

```



\---



\## IP Planning



Count all devices, not only users.



```text

Laptop, Phone, Printer, CCTV, AP, Server, POS, IoT, Guest WiFi

```



Key mindset:



```text

Humans ≠ IP addresses

```



\---



\## Summary



```text

NAT        = Internet access for private IPs

PAT        = Many private IPs share one public IP

Subnetting = Smaller and cleaner networks

VLSM       = Efficient subnet sizing

IP Plan    = Design for devices and growth

```

