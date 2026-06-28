VLAN and STP Fundamentals



\## Overview



This document summarizes key CCNA switching concepts used to build a secure, segmented, and loop-free Layer 2 network.



\## Topics



\* VLAN

\* Trunking

\* Inter-VLAN Routing

\* DHCP

\* STP

\* Rapid PVST+

\* MST

\* PortFast

\* BPDU Guard



\---



\## VLAN



A \*\*VLAN\*\* separates one physical network into multiple logical networks.



| VLAN    | Purpose             |

| ------- | ------------------- |

| VLAN 10 | Management          |

| VLAN 20 | Internal Users      |

| VLAN 30 | CCTV / Surveillance |

| VLAN 40 | Guest Access        |

| VLAN 99 | Native / Management |



\### VLAN Workflow



```text

Create VLAN

→ Assign access ports

→ Configure trunk

→ Set native VLAN

→ Configure routing

→ Configure DHCP

→ Verify

```



\### Commands



```bash

show vlan brief

show interfaces trunk

show ip interface brief

show ip dhcp binding

```



\---



\## STP



\*\*STP\*\* prevents Layer 2 loops caused by redundant switch links.



```text

Redundant Link

→ Layer 2 Loop

→ Broadcast Storm

→ Network Down

```



STP blocks backup paths until they are needed.



\### STP Roles



| Role            | Function                     |

| --------------- | ---------------------------- |

| Root Bridge     | Main STP reference switch    |

| Root Port       | Best path to Root Bridge     |

| Designated Port | Forwarding port on a segment |

| Blocking Port   | Backup port to prevent loops |



\### STP Process



```text

Elect Root Bridge

→ Choose Root Port

→ Choose Designated Port

→ Block remaining ports

```



\---



\## Rapid PVST+



\*\*Rapid PVST+\*\* is Cisco’s faster STP mode per VLAN.



```bash

spanning-tree mode rapid-pvst

```



Set Root Bridge priority:



```bash

spanning-tree vlan 10,20,30,40 priority 4096

```



> Lower priority wins.



\---



\## MST



\*\*MST\*\* groups multiple VLANs into fewer STP instances.



| Instance | VLANs       |

| -------- | ----------- |

| MST 1    | VLAN 10, 20 |

| MST 2    | VLAN 30, 40 |



MST region must match:



```text

Region Name

Revision Number

VLAN Mapping

```



\---



\## PortFast



\*\*PortFast\*\* makes access ports go directly to forwarding state.



Use only on end-device ports.



```bash

spanning-tree portfast

```



\---



\## BPDU Guard



\*\*BPDU Guard\*\* protects access ports from rogue switches.



If a PortFast port receives a BPDU, the port is disabled.



```bash

spanning-tree bpduguard enable

```



Global command:



```bash

spanning-tree portfast bpduguard default

```



\---



\## Best Practice Checklist



```text

Enable Rapid PVST+

Set Root Bridge manually

Configure VLANs

Secure trunk ports

Use non-default native VLAN

Enable PortFast on access ports

Enable BPDU Guard on access ports

Shut down unused ports

Verify and save

```



\---



\## Verification Commands



```bash

show spanning-tree

show spanning-tree summary

show spanning-tree vlan 10

show interfaces trunk

show vlan brief

copy running-config startup-config

```



\---



\## Summary



| Technology        | Function               |

| ----------------- | ---------------------- |

| VLAN              | Separates networks     |

| Trunk             | Carries multiple VLANs |

| Router-on-a-Stick | Routes between VLANs   |

| DHCP              | Assigns IP addresses   |

| STP               | Prevents Layer 2 loops |

| Rapid PVST+       | Faster STP convergence |

| MST               | Scales STP             |

| PortFast          | Speeds up access ports |

| BPDU Guard        | Blocks rogue switches  |



\## Workflow



```text

Segment

→ Trunk

→ Route

→ DHCP

→ Protect

→ Verify

→ Save

