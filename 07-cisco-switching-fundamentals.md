Cisco Switching Fundamentals



\## Overview



This lab covers basic Cisco Layer 2 switching, including MAC address learning, ARP, MAC address table inspection, trunk verification, and device port tracing.



Main workflow:



```text

IP Address → ARP → MAC Address → Switch Port

```



\## Objectives



\* Understand how switches forward traffic

\* Verify switch interfaces and VLANs

\* Use ARP to map IP addresses to MAC addresses

\* Use the MAC address table to locate devices

\* Verify trunk links between switches

\* Document switch ports with clear descriptions



\## Key Concepts



\*\*Switch\*\*

Forwards traffic inside a LAN using MAC addresses.



\*\*MAC Address\*\*

A physical address used to identify a network device.



\*\*ARP\*\*

Maps an IP address to a MAC address.



\*\*MAC Address Table\*\*

Shows which MAC address is connected to which switch port.



\*\*Trunk\*\*

Carries traffic for multiple VLANs between switches.



\## Basic Configuration



```bash

enable

configure terminal

hostname DS-07-SW1

banner motd #Authorized engineers only.#

enable secret CrC0ffee!

service password-encryption

```



\## Management IP



```bash

interface vlan 1

ip address 192.168.10.11 255.255.255.0

no shutdown

exit

ip default-gateway 192.168.10.1

copy running-config startup-config

```



\## Essential Commands



```bash

show ip interface brief

show interfaces status

show interfaces description

show interfaces trunk

show vlan brief

show cdp neighbors

show arp

show mac address-table

show mac address-table address <MAC\_ADDRESS>

show interfaces <INTERFACE>

copy running-config startup-config

```



\## Device Tracing Workflow



Example target:



```text

PC7 IP Address: 192.168.1.118

```



Generate traffic:



```bash

ping 192.168.1.118

```



Find the MAC address:



```bash

show arp

```



Find the switch port:



```bash

show mac address-table address <MAC\_ADDRESS>

```



Example result:



```text

PC7 = Switch6 Et0/1

```



\## Interface Documentation



After locating a device, add a clear interface description.



```bash

configure terminal

interface fa0/2

description BaristaPOS\_192.168.42.37

end

copy running-config startup-config

```



\## Key Takeaways



\* Switches forward traffic using MAC addresses.

\* ARP maps IP addresses to MAC addresses.

\* The MAC address table helps locate devices.

\* Trunk and VLAN verification are important for Layer 2 troubleshooting.

\* Clear interface descriptions make network documentation easier.

