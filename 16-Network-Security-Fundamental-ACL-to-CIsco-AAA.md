\# Network Security Fundamentals (ACL to Cisco AAA)



> A concise reference covering \*\*Cisco Access Control Lists (ACLs)\*\*, \*\*Cybersecurity Fundamentals\*\*, and \*\*Cisco AAA (Authentication, Authorization, and Accounting)\*\* for \*\*CCNA 200-301\*\* preparation.



\---



\## 📚 Overview



This document summarizes the essential security concepts required to secure enterprise networks. It covers traffic filtering with ACLs, cybersecurity fundamentals, common attack vectors, identity protection, and centralized network access control using Cisco AAA.



\---



\# 1. Access Control Lists (ACL)



\## What is an ACL?



An \*\*Access Control List (ACL)\*\* is a set of rules that controls network traffic by permitting or denying packets based on predefined criteria.



\### Benefits



\- Control network access

\- Reduce attack surface

\- Protect critical resources

\- Enforce security policies



\---



\## Standard ACL



Filters traffic using only the \*\*source IP address\*\*.



\### Characteristics



\- Matches source IP only

\- Simple and lightweight

\- Lower precision

\- Place \*\*near the destination\*\*



\### Best Use Cases



\- Restrict host or subnet access

\- Basic traffic filtering

\- VTY access control



\---



\## Extended ACL



Filters traffic using multiple criteria.



\### Matches



\- Source IP

\- Destination IP

\- Protocol

\- Port Number



\### Characteristics



\- Highly granular

\- Supports application filtering

\- Place \*\*near the source\*\*



\### Common Services



| Service | Port |

|---------|-----:|

| HTTP | TCP 80 |

| HTTPS | TCP 443 |

| SSH | TCP 22 |

| FTP | TCP 21 |

| Telnet | TCP 23 |

| DNS | UDP 53 |



\---



\## ACL Processing Rules



\- Top-down processing

\- First match wins

\- Implicit deny at the end

\- ACLs work only after being applied

\- Use sequence numbers for easier management



\---



\## ACL Deployment Workflow



```text

Plan

&#x20;  ↓

Create ACL

&#x20;  ↓

Apply to Interface

&#x20;  ↓

Verify

&#x20;  ↓

Monitor

```



\---



\## ACL Best Practices



\- Plan before configuring

\- Place Standard ACL near the destination

\- Place Extended ACL near the source

\- Order rules from most specific to most general

\- Verify functionality after deployment

\- Monitor ACL hit counters



\---



\# 2. Cybersecurity Fundamentals



\## Why Security Matters



Network security protects:



\- Business operations

\- Network infrastructure

\- User identities

\- Sensitive information

\- Service availability



Security is everyone's responsibility—not only the security team.



\---



\## CIA Triad



\### Confidentiality



Protect data from unauthorized access.



\### Integrity



Ensure information remains accurate and unmodified.



\### Availability



Keep systems and services continuously accessible.



\---



\## Security Concepts



\### Vulnerability



A weakness within a system.



Examples:



\- Weak passwords

\- Misconfigurations

\- Outdated software



\### Threat



Anything capable of exploiting a vulnerability.



Examples:



\- Hackers

\- Malware

\- Insider attacks



\### Exploit



The method used to attack a vulnerability.



Examples:



\- SQL Injection

\- Brute Force

\- Rogue DHCP



\### Risk



The potential impact when a threat exploits a vulnerability.



\---



\## Common Network Threats



\### Denial of Service (DoS)



Overloads services to make them unavailable.



\### Spoofing



Pretends to be a trusted device or user.



\### Man-in-the-Middle (MITM)



Intercepts or modifies network traffic.



\### Reflection \& Amplification



Uses third-party servers to increase attack volume.



\### Reconnaissance



Collects information before launching an attack.



Examples:



\- Port scanning

\- Banner grabbing

\- WHOIS lookup



\### Malware



Malicious software designed to compromise systems.



Types include:



\- Virus

\- Worm

\- Trojan

\- Ransomware

\- Backdoor



\---



\# 3. Identity \& Password Security



Modern attacks often target \*\*identities instead of systems\*\*.



\## Password Attacks



\- Password guessing

\- Password theft

\- Hash cracking



\### Common Techniques



\- Dictionary Attack

\- Brute Force Attack

\- Reconnaissance



\---



\## Multi-Factor Authentication (MFA)



Strengthens authentication by combining multiple factors.



\### Factors



\- Something you know

\- Something you have

\- Something you are



\---



\## Password Manager



Recommended for:



\- Strong passwords

\- Unique passwords

\- Secure credential storage



\---



\# 4. Social Engineering



Social engineering manipulates people instead of systems.



\## Common Attacks



| Attack | Description |

|---------|-------------|

| Spear Phishing | Targeted email attack |

| Whaling | Executive-focused phishing |

| Smishing | SMS phishing |

| Vishing | Voice phishing |

| Tailgating | Unauthorized physical entry |



\---



\## Security Best Practices



\- Use passwords with at least 15 characters

\- Never reuse passwords

\- Enable MFA

\- Use a password manager

\- Keep software updated

\- Verify suspicious emails, calls, and messages

\- Promote security awareness

\- Protect physical access to devices



\---



\# 5. Cisco AAA



AAA centralizes network access management.



\---



\## Authentication



\*\*Who are you?\*\*



Verifies user identity before granting access.



\---



\## Authorization



\*\*What are you allowed to do?\*\*



Determines user permissions after authentication.



\---



\## Accounting



\*\*What did you do?\*\*



Records user activities for logging, auditing, and compliance.



\---



\## AAA Workflow



```text

Authentication

&#x20;       ↓

Authorization

&#x20;       ↓

Accounting

```



\---



\# 6. AAA Protocols



\## RADIUS



Best suited for:



\- User authentication

\- Wireless networks

\- VPN access

\- Enterprise authentication



\### Characteristics



\- Open standard

\- UDP

\- Combines authentication and authorization



\---



\## TACACS+



Designed primarily for device administration.



\### Characteristics



\- Cisco protocol

\- TCP

\- Encrypts the entire payload

\- Ideal for router and switch management



\---



\# 7. Network Access Security



\## IEEE 802.1X



Provides port-based network access control before allowing devices onto the network.



\---



\## Extensible Authentication Protocol (EAP)



Authentication framework used with 802.1X.



Commonly deployed in:



\- WPA2 Enterprise

\- WPA3 Enterprise



\---



\# 8. Access Layer Security



\## Port Security



Limits which devices can connect to a switch port.



\---



\## DHCP Snooping



Blocks unauthorized DHCP servers.



Benefits:



\- Prevents Rogue DHCP

\- Validates DHCP messages



\---



\## Dynamic ARP Inspection (DAI)



Prevents ARP spoofing attacks by validating ARP packets.



\---



\# Security Workflow



```text

Identify Assets

&#x20;       ↓

Identify Threats

&#x20;       ↓

Identify Vulnerabilities

&#x20;       ↓

Choose Security Controls

&#x20;       ↓

Deploy

&#x20;       ↓

Monitor

&#x20;       ↓

Improve

```



\---



\# Key Takeaways



\- ACLs enforce network traffic policies.

\- Standard ACLs filter by source IP and should be placed near the destination.

\- Extended ACLs filter by source, destination, protocol, and port, and should be placed near the source.

\- Cybersecurity begins with understanding risks, not memorizing commands.

\- Strong identity protection relies on unique passwords, MFA, and user awareness.

\- AAA centralizes authentication, authorization, and accounting.

\- RADIUS secures user authentication, while TACACS+ manages network devices.

\- Switch security features such as Port Security, DHCP Snooping, and Dynamic ARP Inspection protect the access layer.

\- Effective security is a continuous cycle of planning, deployment, monitoring, and improvement.



\---



\## CCNA Exam Checklist



\- Standard ACL

\- Extended ACL

\- ACL Placement

\- First Match Wins

\- Implicit Deny

\- CIA Triad

\- Vulnerability, Threat, Exploit

\- Password Security

\- MFA

\- Social Engineering

\- AAA

\- RADIUS

\- TACACS+

\- 802.1X

\- EAP

\- Port Security

\- DHCP Snooping

\- Dynamic ARP Inspection



\---



\*\*Author:\*\* \*CCNA Study Notes\*  

\*\*Certification:\*\* Cisco CCNA 200-301  

\*\*Topic:\*\* Network Security Fundamentals (Skill 18–19)

