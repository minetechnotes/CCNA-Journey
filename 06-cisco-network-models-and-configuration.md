CCNA Network Basics



\## Overview



This documentation summarizes basic CCNA concepts, including network models, network design, Cisco IOS, base configuration, and configuration management.



The goal is to understand how networks work and how Cisco devices are configured in real environments.



\---



\## 1. Network Models



Network models help engineers understand how data moves across a network.



\### OSI Model



```text

7\. Application

6\. Presentation

5\. Session

4\. Transport

3\. Network

2\. Data Link

1\. Physical

````



Common troubleshooting examples:



```text

Layer 1 = Cable or physical issue

Layer 2 = Switch, MAC address, or VLAN issue

Layer 3 = IP address or routing issue

Layer 4 = TCP, UDP, or port issue

```



\### TCP/IP Model



```text

4\. Application

3\. Transport

2\. Internet

1\. Link

```



```text

OSI    = troubleshooting reference

TCP/IP = real-world communication model

```



\---



\## 2. Encapsulation



Encapsulation is the process of wrapping data before it is sent across the network.



```text

Data → TCP/UDP Header → IP Header → Ethernet Header → Bits

```



Decapsulation is the process of opening that data on the receiving device.



\---



\## 3. Network Design



A network should be designed properly, not randomly connected.



Common design models:



```text

SOHO Network

Two-Tier Architecture

Three-Tier Architecture

Spine and Leaf

```



\### Three-Tier Architecture



```text

Access Layer       = Connects end devices

Distribution Layer = Manages routing and policies

Core Layer         = High-speed backbone

```



Good design improves scalability, redundancy, management, and troubleshooting.



\---



\## 4. Network Roles



```text

Network Architect     = Designs the network

Network Engineer      = Builds and configures the network

Network Administrator = Maintains and monitors the network

```



In small environments, one person may handle all roles.



\---



\## 5. Console Connection



A new Cisco device usually has no IP address or remote access.



Initial configuration is done using a console connection.



```text

Laptop → Console Cable → Console Port → Cisco CLI

```



The console port is used for administration, not normal network traffic.



\---



\## 6. Cisco IOS Basics



Cisco IOS is the operating system used on Cisco routers and switches.



Common IOS modes:



```text

Switch>              User EXEC Mode

Switch#              Privileged EXEC Mode

Switch(config)#      Global Configuration Mode

Switch(config-if)#   Interface Configuration Mode

```



Useful commands:



```bash

enable

configure terminal

exit

end

```



Useful shortcuts:



```text

?      Show available commands

Tab    Auto-complete command

↑      Command history

```



\---



\## 7. Cisco Boot Process



Cisco device boot sequence:



```text

Power On

→ POST

→ Bootstrap

→ Load IOS from Flash

→ Load startup-config from NVRAM

→ CLI Ready

```



Memory types:



```text

ROM    = Bootstrap

Flash  = IOS image

RAM    = Running-config

NVRAM  = Startup-config

```



\---



\## 8. Cisco Base Configuration



Base configuration prepares a Cisco device for secure basic operation.



Common tasks:



Set hostname

Set enable secret

Encrypt passwords

Configure console access

Configure VTY access

Set login banner

Save configuration



Example configuration:



```bash

enable

configure terminal

hostname Cafe-01-SW1

enable secret C1sc0R0cks!

service password-encryption

banner motd #Authorized Access Only#



line console 0

password ConsolePass123

login



line vty 0 4

password RemotePass123

login



end

copy running-config startup-config

```



\---



\## 9. Running-Config vs Startup-Config



```text

running-config = Active configuration stored in RAM

startup-config = Saved configuration stored in NVRAM

```



Check configuration:



```bash

show running-config

show startup-config

```



Save configuration:



```bash

copy running-config startup-config

```



Unsaved changes will be lost after reload.



\---



\## 10. Reset Cisco Configuration



Reset saved configuration:



```bash

write erase

reload

```



Or:



```bash

erase startup-config

reload

```



After reset, the device returns to the default prompt:



```text

Switch>

```



\---



\## Key Commands



```bash

enable

configure terminal

hostname

show running-config

show startup-config

show ip interface brief

copy running-config startup-config

write erase

erase startup-config

reload

```



\---



\## Summary



This documentation covers the foundation of practical networking:



```text

Understand network models

Design networks properly

Access Cisco IOS

Configure Cisco devices

Save and reset configurations

Troubleshoot with confidence

```



These skills are essential for networking, cybersecurity, and IT infrastructure.

