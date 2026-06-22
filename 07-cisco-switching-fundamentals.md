Cisco Switching Fundamentals



\## Overview



This lab covers Cisco Layer 2 switching fundamentals, including MAC address learning, ARP, MAC address table inspection, trunk verification, and device port tracing.



Main workflow:



```text

IP Address → ARP → MAC Address → Switch Port

```



\## Objectives



\* Configure basic Cisco switch settings

\* Verify interface status, VLAN, speed, and duplex

\* Understand how switches learn MAC addresses

\* Use ARP to map IP addresses to MAC addresses

\* Trace devices using the MAC address table

\* Verify trunk links between switches

\* Document interfaces with descriptions



\## Key Concepts



\*\*Switch\*\*

Connects devices in a LAN and forwards frames using MAC addresses.



\*\*MAC Address\*\*

A physical address assigned to a network device.



\*\*ARP\*\*

Maps an IP address to a MAC address.



\*\*MAC Address Table\*\*

Stores learned MAC addresses and the switch ports where they are located.



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



\## Management IP Configuration



```bash

interface vlan 1

ip address 192.168.10.11 255.255.255.0

no shutdown

exit

ip default-gateway 192.168.10.1

```



\## Save Configuration



```bash

copy running-config startup-config

```



or



```bash

wr

```



\## Verification Commands



```bash

show ip interface brief

show interfaces status

show interfaces description

show running-config

show startup-config

```



Command purpose:



\* `show ip interface brief` checks interface IP address and status

\* `show interfaces status` checks port status, VLAN, speed, and duplex

\* `show interfaces description` shows interface descriptions

\* `show running-config` shows the active configuration

\* `show startup-config` shows the saved configuration



\## ARP and MAC Table Commands



```bash

ping <IP\_ADDRESS>

show arp

show mac address-table

show mac address-table address <MAC\_ADDRESS>

show mac address-table interface <INTERFACE>

clear mac address-table dynamic

```



Command purpose:



\* `ping <IP\_ADDRESS>` tests connectivity and triggers ARP

\* `show arp` displays IP-to-MAC mappings

\* `show mac address-table` displays learned MAC addresses

\* `show mac address-table address <MAC\_ADDRESS>` locates a specific device

\* `show mac address-table interface <INTERFACE>` shows MAC addresses learned on one interface

\* `clear mac address-table dynamic` clears dynamically learned MAC entries



\## Trunk and VLAN Verification



```bash

show interfaces trunk

show vlan brief

show cdp neighbors

show cdp neighbors detail

```



Command purpose:



\* `show interfaces trunk` verifies trunk ports and allowed VLANs

\* `show vlan brief` shows VLANs and assigned ports

\* `show cdp neighbors` discovers directly connected Cisco devices

\* `show cdp neighbors detail` shows detailed neighbor information



\## Device Tracing Workflow



Example target:



```text

PC7 IP Address: 192.168.1.118

```



Step 1: Generate traffic.



```bash

ping 192.168.1.118

```



Step 2: Find the MAC address.



```bash

show arp

```



Example result:



```text

192.168.1.118 → 5254.ab12.cd34

```



Step 3: Find the switch port.



```bash

show mac address-table address 5254.ab12.cd34

```



Example result:



```text

VLAN    MAC Address       Type       Port

10      5254.ab12.cd34    Dynamic    Et0/1

```



Final result:



```text

PC7 = Switch6 Et0/1

```



\## Interface Documentation



After identifying the device, add a clear interface description.



```bash

configure terminal

interface fa0/2

description BaristaPOS\_192.168.42.37

end

copy running-config startup-config

```



\## Troubleshooting Checklist



\* Verify the target IP address

\* Ping the device

\* Check the ARP table

\* Identify the MAC address

\* Search the MAC address table

\* Find the switch port

\* Verify VLAN, trunk, speed, and duplex

\* Check interface errors

\* Add interface descriptions

\* Save the configuration



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



\## Key Takeaways



\* Switches forward frames using MAC addresses.

\* ARP maps IP addresses to MAC addresses.

\* The MAC address table maps MAC addresses to switch ports.

\* Device tracing follows this workflow:



```text

IP → ARP → MAC → Switch Port

```



\* Interface descriptions improve network documentation.

\* VLAN, trunk, and interface verification are essential for Layer 2 troubleshooting.

