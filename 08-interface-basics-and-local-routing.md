Interface Basics and Local Routing



\## Overview



This lab covers basic Cisco switch and router interface configuration, interface verification, and static routing between two networks.



The main goal is to understand how to check interface status, identify common interface issues, and verify network connectivity.



\## Objectives



\* Verify switch and router interfaces

\* Configure interface descriptions

\* Understand speed and duplex

\* Check interface counters

\* Configure router IP addresses

\* Add static routes

\* Verify end-to-end connectivity



\## Key Concepts



\### Switch Interfaces



Switch interfaces connect devices inside a LAN, such as PCs, printers, access points, phones, and cameras.



Useful commands:



```cisco

show ip interface brief

show interfaces status

show interfaces description

```



Example:



```cisco

interface FastEthernet0/1

&#x20;description Front\_Register\_PC

```



Descriptions make ports easier to identify and troubleshoot.



\### Speed, Duplex, and Counters



Speed defines link capacity, such as `100 Mbps` or `1 Gbps`.



Duplex defines how data is sent and received:



```text

Half-duplex = one direction at a time

Full-duplex = send and receive at the same time

```



Common interface issues:



```text

CRC errors

Input errors

Output errors

Collisions

Late collisions

Interface resets

```



Useful command:



```cisco

show interface Ethernet0/0

```



A healthy interface should be `up/up`, full-duplex, and have low or zero errors.



\## Management IP



A Layer 2 switch needs a management IP for remote access.



```cisco

interface vlan 1

&#x20;ip address 192.168.0.2 255.255.255.0

&#x20;no shutdown



ip default-gateway 192.168.0.1

```



\## Local Routing Lab



Network topology:



```text

Coffee LAN  : 192.168.42.0/24

Fallout LAN : 192.168.84.0/24

WAN Link    : 10.8.0.0/30

```



Router addressing:



```text

Cafe-RT1 E0/0    : 192.168.42.1/24

Cafe-RT1 E0/1    : 10.8.0.1/30



Fallout-RT1 E0/0 : 192.168.84.1/24

Fallout-RT1 E0/1 : 10.8.0.2/30

```



\## Static Routes



On Cafe-RT1:



```cisco

ip route 192.168.84.0 255.255.255.0 10.8.0.2

```



On Fallout-RT1:



```cisco

ip route 192.168.42.0 255.255.255.0 10.8.0.1

```



Static routes allow each router to reach the remote LAN.



\## Verification Commands



```cisco

show ip interface brief

show interfaces description

show interface Ethernet0/0

show ip route

show ip route static

show arp

ping

write memory

```



\## Key Takeaways



\* Switch interfaces connect devices inside a LAN.

\* Router interfaces connect different networks.

\* Interface descriptions improve troubleshooting.

\* Speed and duplex must match.

\* Interface counters help detect physical or configuration issues.

\* Static routes enable communication between remote networks.



\## Final Note



```text

Do not guess. Check the interface first.

```



Clean interface configuration and proper verification are the foundation of stable networking.

