Dynamic Routing, Route Selection, and Static NAT



\## Overview



This lab covers how Cisco routers learn routes, choose the best path, and translate private IP addresses to public IP addresses using Static NAT.



\## Topics



\* EIGRP Dynamic Routing

\* Routing Table

\* Route Selection

\* Static NAT

\* NAT Verification



\---



\## EIGRP Dynamic Routing



EIGRP allows routers to learn routes automatically.



```cisco

router eigrp 1

network 192.168.1.0 0.0.0.255

network 192.168.2.0 0.0.0.3

```



Verify EIGRP:



```cisco

show ip eigrp neighbors

show ip route eigrp

```



EIGRP routes appear with code `D`.



\---



\## Routing Table



Routers use the routing table to decide where packets should go.



```cisco

show ip route

```



Common route codes:



| Code | Meaning        |

| ---- | -------------- |

| `C`  | Connected      |

| `L`  | Local          |

| `S`  | Static         |

| `S\*` | Default Static |

| `D`  | EIGRP          |



\---



\## Route Selection



Routers choose the best route using this order:



```text

1\. Most specific route

2\. Lowest Administrative Distance

3\. Lowest metric

```



Common Administrative Distance values:



| Route Type |  AD |

| ---------- | --: |

| Connected  |   0 |

| Static     |   1 |

| EIGRP      |  90 |

| OSPF       | 110 |



Static routes are preferred over EIGRP because static routes have lower AD.



\---



\## Static NAT



Static NAT maps one private IP address to one public IP address.



Example:



```text

192.168.1.50 <--> 216.0.5.20

192.168.1.51 <--> 216.0.5.21

```



Static NAT is commonly used for internal servers that must be reachable from outside the network.



\---



\## Static NAT Configuration



Create NAT mappings:



```cisco

conf t

ip nat inside source static 192.168.1.50 216.0.5.20

ip nat inside source static 192.168.1.51 216.0.5.21

end

```



Set LAN interface as inside:



```cisco

interface ethernet0/0

ip nat inside

```



Set ISP interface as outside:



```cisco

interface ethernet0/1

ip nat outside

```



Verify NAT:



```cisco

show ip nat translations

```



\---



\## Important Commands



| Command                       | Function                  |

| ----------------------------- | ------------------------- |

| `show ip route`               | Check routing table       |

| `show ip eigrp neighbors`     | Check EIGRP neighbors     |

| `show ip route eigrp`         | Check EIGRP routes        |

| `ip nat inside source static` | Create Static NAT mapping |

| `ip nat inside`               | Mark inside interface     |

| `ip nat outside`              | Mark outside interface    |

| `show ip nat translations`    | Verify NAT table          |



\---



\## Key Takeaways



\* EIGRP learns routes automatically.

\* The routing table decides the best path.

\* Static routes are preferred over EIGRP because AD is lower.

\* Static NAT maps one private IP to one public IP.

\* NAT requires correct inside and outside interface configuration.



\## Summary



Routing decides where packets go.



NAT changes how IP addresses appear.



Together, routing and NAT allow private networks to communicate with external networks.



