NAT & Subnetting

## Overview

Basic summary of **NAT**, **Subnetting**, **VLSM**, and IP planning.

```
NAT        = Private IP → Public IP
Subnetting = Large network → Smaller networks
VLSM       = Different subnet sizes based on need
```

---

## NAT

**NAT** allows private devices to access the internet using a public IP.

| Type | Function |
| --- | --- |
| Static NAT | 1 private IP = 1 public IP |
| Dynamic NAT | Private IPs use a public IP pool |
| PAT / NAT Overload | Many private IPs share 1 public IP using ports |

### Basic PAT Config

```
access-list 1 permit 192.168.1.0 0.0.0.255

interface ethernet0/0
 Ip Nat inside

interface ethernet0/1
 Ip Nat outside

Ip Nat inside source list 1 interface ethernet0/1 overload
```

### Verify

```
show Ip Nat translations
show Ip Nat statistics
```

---

## Subnetting

**Subnetting** splits a large network into smaller networks.

### Benefits

- Saves IP addresses
- Reduces broadcast traffic
- Improves security
- Makes troubleshooting easier
- Supports growth

### Common CIDR

| CIDR | Usable Hosts |
| --- | --- |
| /24 | 254 |
| /26 | 62 |
| /27 | 30 |
| /30 | 2 |

---

## Subnet Rule

```
Mask → Increment → Range → Network & Broadcast
```

Example:

```
IP:        192.168.5.22
Mask:      255.255.255.240
Increment: 16

Network:   192.168.5.16
Hosts:     192.168.5.17 - 192.168.5.30
Broadcast: 192.168.5.31
```

---

## VLSM

**VLSM** uses different subnet sizes in one network.

```
50 hosts → /26
20 hosts → /27
2 hosts  → /30
```

Rule:

```
Start from the largest subnet first.
```

---

## IP Planning

Count all devices, not only users.

```
Laptop, Phone, Printer, CCTV, AP, Server, POS, IoT, Guest WiFi
```

Key mindset:

```
Humans ≠ IP addresses
```

---

## Summary

```
NAT        = Internet access for private IPs
PAT        = Many private IPs share one public IP
Subnetting = Smaller and cleaner networks
VLSM       = Efficient subnet sizing
IP Plan    = Design for devices and growth
```