VLAN and Trunking Basics



\## Overview



VLANs separate a flat network into smaller logical networks.

This improves security, reduces broadcast traffic, and makes the network easier to manage.



\---



\## Core Concepts



| Term                    | Meaning                        |

| ----------------------- | ------------------------------ |

| VLAN                    | Logical network segment        |

| Access Port             | Carries one VLAN               |

| Trunk Port              | Carries multiple VLANs         |

| 802.1Q                  | VLAN tagging                   |

| Router / Layer 3 Switch | Connects different VLANs       |

| Native VLAN             | Handles untagged trunk traffic |



\---



\## Example VLAN Design



```text

VLAN 10 = Admin

VLAN 20 = Guest

VLAN 30 = CCTV

VLAN 40 = Management

```



\---



\## Basic VLAN Configuration



```bash

conf t

VLAN 10

\#name ADMIN

VLAN 20

\#name GUEST

end

show VLAN brief

```



\---



\## Access Port



Access ports are used for end devices such as PCs, printers, servers, and cameras.



```bash

interface e0/2

\#switchport mode access

\#switchport access VLAN 20

```



\---



\## Trunk Port



Trunk ports are used between switches, routers, Layer 3 switches, or wireless access points.



```bash

interface e0/1

\#switchport trunk encapsulation dot1q

\#switchport mode trunk

```



\---



\## Inter-VLAN Routing



Different VLANs cannot communicate through a Layer 2 switch only.

Use a router, Layer 3 switch, or Router-on-a-Stick.



```bash

interface g0/0.10

\#encapsulation dot1Q 10

\#IP address 10.0.18.1 255.255.255.224

```



\---



\## Security Best Practices



```bash

switchport NONEGOTIATE

VTP mode transparent

switchport trunk native VLAN 99

```



Recommended actions:



\* Disable automatic trunk negotiation

\* Use VTP transparent mode

\* Use a dedicated native VLAN

\* Shutdown unused ports

\* Avoid using VLAN 1 for production users



\---



\## Verification Commands



```bash

show VLAN brief

show interfaces trunk

show IP interface brief

show IP DHCP binding

```



\---



\## Key Takeaways



```text

VLAN   = Separates networks

Access = Carries one VLAN

Trunk  = Carries multiple VLANs

802.1Q = VLAN tag

Router = Connects VLANs

DHCP   = Assigns IP automatically

```



A good network design is segmented, secure, scalable, and easy to troubleshoot.

