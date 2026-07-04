STP and EtherChannel Fundamentals



\## Overview



This document summarizes the basic concepts of \*\*Spanning Tree Protocol (STP)\*\* and \*\*EtherChannel\*\* in Layer 2 networks.



\* \*\*STP\*\* prevents Layer 2 loops.

\* \*\*EtherChannel\*\* combines multiple physical links into one logical link.

\* \*\*LACP\*\* is the recommended standard protocol for EtherChannel.



\---



\## Spanning Tree Protocol



STP is used to keep a switched network loop-free.



When multiple redundant links exist, STP blocks some paths to prevent broadcast storms and MAC address table instability.



\### Key Points



\* Prevents Layer 2 loops

\* Elects a Root Bridge

\* Chooses the best path to the Root Bridge

\* Blocks redundant links

\* Keeps backup paths ready



\### Common STP Port Roles



| Role                  | Description                   |

| --------------------- | ----------------------------- |

| Root Port             | Best path to the Root Bridge  |

| Designated Port       | Forwarding port for a segment |

| Alternate Port        | Backup path                   |

| Blocking / Discarding | Prevents loops                |



\---



\## Rapid PVST+



Rapid PVST+ is a faster STP version that runs per VLAN.



```bash

spanning-tree mode rapid-pvst

show spanning-tree summary

show spanning-tree vlan 1

```



\---



\## PortFast and BPDU Guard



PortFast is used on access ports connected to end devices.



BPDU Guard protects access ports from unauthorized switches.



```bash

spanning-tree portfast

spanning-tree bpduguard enable

```



> Do not use PortFast on trunk links between switches.



\---



\## EtherChannel



EtherChannel bundles multiple physical links into one logical interface called a \*\*Port-channel\*\*.



```text

Ethernet0/1 + Ethernet0/2 = Port-channel1

```



\### Benefits



\* Better bandwidth usage

\* Link redundancy

\* Fewer blocked links

\* Cleaner STP topology

\* Higher availability



\---



\## LACP



LACP is the standard protocol used to build EtherChannel.



\### LACP Modes



| Mode    | Description                         |

| ------- | ----------------------------------- |

| Active  | Actively tries to form EtherChannel |

| Passive | Waits for negotiation               |



\### Working Combinations



```text

active + active = works

active + passive = works

passive + passive = fails

```



Recommended mode:



```text

active + active

```



\---



\## Basic EtherChannel Configuration



Before creating EtherChannel, member ports must use matching settings such as speed, duplex, trunk mode, native VLAN, and allowed VLANs.



```bash

configure terminal



interface range Ethernet0/1-2



```text

switchport trunk encapsulation dot1q

switchport mode trunk

switchport trunk allowed vlan all

channel-group 1 mode active



interface Port-channel1



```text

switchport mode trunk

switchport trunk allowed vlan all



end

write memory

```



\---



\## Verification Commands



```bash

show etherchannel summary

show interface trunk

show spanning-tree vlan 1

show etherchannel load-balance

```



Healthy EtherChannel output:



```text

Po1(SU)

Et0/1(P)

Et0/2(P)

```



| Symbol | Meaning              |

| ------ | -------------------- |

| Po1    | Port-channel 1       |

| S      | Layer 2 EtherChannel |

| U      | In use               |

| P      | Port is bundled      |



\---



\## Load Balancing



EtherChannel uses a hashing algorithm to decide which physical link carries each traffic flow.



One flow usually uses one physical link, but multiple flows can be distributed across multiple links.



```bash

port-channel load-balance src-dst-mac

show etherchannel load-balance

```



\---



\## Deployment Checklist



\* Verify interface configuration

\* Confirm trunk and VLAN consistency

\* Configure LACP on both switches

\* Configure the Port-channel interface

\* Verify EtherChannel status

\* Confirm STP sees the Port-channel

\* Tune load balancing if needed

\* Save the configuration



\---



\## Key Takeaways



```text

STP = prevents Layer 2 loops

Rapid PVST+ = faster STP convergence

PortFast = fast access port activation

BPDU Guard = protects access ports

EtherChannel = bundles physical links

LACP = standard EtherChannel protocol

Port-channel = logical bundled interface

```



STP protects the network from loops, while EtherChannel improves bandwidth and redundancy.



Together, they create a more stable and resilient Layer 2 network.

