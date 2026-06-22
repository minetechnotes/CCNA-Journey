CCNA Journey #5: Cisco Switching Fundamentals



\## Overview



This lab covers the fundamentals of Cisco Layer 2 switching, including MAC address learning, ARP, MAC address table inspection, trunk verification, and device port tracing.



The main troubleshooting workflow is:



```text

IP Address → ARP → MAC Address → Switch Port

````



\---



\## Lab Objectives



\* Configure basic Cisco switch settings

\* Verify interface status, VLAN, speed, and duplex

\* Understand how switches learn MAC addresses

\* Use ARP to map IP addresses to MAC addresses

\* Trace devices using the MAC address table

\* Verify trunk links between switches

\* Document interfaces using descriptions



\---



\## Key Concepts



| Concept           | Description                                                       |

| ----------------- | ----------------------------------------------------------------- |

| Switch            | Connects devices in a LAN and forwards frames using MAC addresses |

| MAC Address       | Physical address of a network device                              |

| ARP               | Maps an IP address to a MAC address                               |

| MAC Address Table | Stores learned MAC addresses and their switch ports               |

| Trunk             | Carries traffic for multiple VLANs between switches               |



\---



\## Basic Configuration



```bash

enable

configure terminal

hostname DS-07-SW1

banner motd #Authorized engineers only.#

enable secret CrC0ffee!

service password-encryption

```



\### Management IP



```bash

interface vlan 1

ip address 192.168.10.11 255.255.255.0

no shutdown

exit

ip default-gateway 192.168.10.1

```



\### Save Configuration



```bash

copy running-config startup-config

```



\---



\## Verification Commands



```bash

show ip interface brief

show interfaces status

show interfaces description

show running-config

show startup-config

```



| Command                       | Purpose                                    |

| ----------------------------- | ------------------------------------------ |

| `show ip interface brief`     | Check interface IP and status              |

| `show interfaces status`      | Check port status, VLAN, speed, and duplex |

| `show interfaces description` | View interface descriptions                |

| `show running-config`         | View active configuration                  |

| `show startup-config`         | View saved configuration                   |



\---



\## ARP and MAC Table Commands



```bash

ping <IP\_ADDRESS>

show arp

show mac address-table

show mac address-table address <MAC\_ADDRESS>

show mac address-table interface <INTERFACE>

clear mac address-table dynamic

```



| Command                                        | Purpose                           |

| ---------------------------------------------- | --------------------------------- |

| `ping <IP\_ADDRESS>`                            | Test connectivity and trigger ARP |

| `show arp`                                     | View IP-to-MAC mappings           |

| `show mac address-table`                       | Display learned MAC addresses     |

| `show mac address-table address <MAC\_ADDRESS>` | Locate a specific device          |

| `clear mac address-table dynamic`              | Clear learned MAC entries         |



\---



\## Trunk and VLAN Verification



```bash

show interfaces trunk

show vlan brief

show cdp neighbors

show cdp neighbors detail

```



| Command                     | Purpose                              |

| --------------------------- | ------------------------------------ |

| `show interfaces trunk`     | Verify trunk ports and allowed VLANs |

| `show vlan brief`           | View VLANs and assigned ports        |

| `show cdp neighbors`        | Discover connected Cisco devices     |

| `show cdp neighbors detail` | View detailed neighbor information   |



\---



\## Device Tracing Workflow



Example target:



```text

PC7 IP Address: 192.168.1.118

```



\### Step 1: Generate Traffic



```bash

ping 192.168.1.118

```



\### Step 2: Find the MAC Address



```bash

show arp

```



Example:



```text

192.168.1.118 → 5254.ab12.cd34

```



\### Step 3: Find the Switch Port



```bash

show mac address-table address 5254.ab12.cd34

```



Example result:



```text

VLAN    MAC Address       Type       Port

10      5254.ab12.cd34    Dynamic    Et0/1

```



Final mapping:



```text

PC7 = Switch6 Et0/1

```



\---



\## Interface Documentation



After identifying a device, add a clear interface description:



```bash

configure terminal

interface fa0/2

description BaristaPOS\_192.168.42.37

end

copy running-config startup-config

```



\---



\## Troubleshooting Checklist



\* Verify the target IP address

\* Ping the device

\* Check the ARP table

\* Find the MAC address

\* Search the MAC address table

\* Identify the switch port

\* Verify VLAN, trunk, speed, and duplex

\* Check for interface errors

\* Add interface descriptions

\* Save the configuration



\---



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



\---



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

