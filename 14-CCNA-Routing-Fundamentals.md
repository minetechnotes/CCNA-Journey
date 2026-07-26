\# 14-Routing-Protocols-OSPF-and-FHRP-Fundamentals



> A concise guide to CCNA Routing Fundamentals, covering Routing Protocols, OSPF, and First Hop Redundancy Protocol (FHRP).



\---



\# 📚 Topics



\- Categories of Routing Protocols

\- Route Selection

\- Administrative Distance

\- Metric

\- Equal Cost Multi-Path (ECMP)

\- OSPF

\- OSPF Network Command

\- OSPF Neighbor Adjacency

\- Passive Interface

\- OSPF Areas

\- OSPF Troubleshooting

\- OSPF Scaling

\- First Hop Redundancy Protocol (FHRP)

\- HSRP

\- VRRP

\- GLBP

\- Virtual IP \& Virtual MAC



\---



\# 1. Categories of Routing Protocols



\### Definition

Routing protocols allow routers to automatically exchange routing information and build routing tables.



\### Function

\- Discover routes automatically.

\- Adapt to network changes.

\- Reduce manual configuration.



\### Real-World Example

A company with multiple branch offices uses \*\*OSPF\*\* so all routers automatically learn new routes when a new branch is added.



\---



\# 2. Route Selection



\### Definition

Route Selection is the process a router uses to choose the best available path to a destination.



\### Function

\- Select the most efficient route.

\- Improve network performance.

\- Prevent routing conflicts.



\### Decision Process



```

Longest Prefix Match

&#x20;       ↓

Administrative Distance

&#x20;       ↓

Metric

```



\### Real-World Example

If two routes exist to the same destination, the router automatically chooses the most trusted and lowest-cost route.



\---



\# 3. Administrative Distance (AD)



\### Definition

Administrative Distance measures how trustworthy a routing source is.



\### Function

\- Compare different routing protocols.

\- Select the preferred routing source.



\### Common Values



| Route Source | AD |

|-------------|---:|

| Connected | 0 |

| Static | 1 |

| EIGRP | 90 |

| OSPF | 110 |

| RIP | 120 |



\### Real-World Example

If both OSPF and RIP advertise the same network, the router chooses OSPF because it has a lower AD.



\---



\# 4. Metric



\### Definition

A Metric measures the cost of reaching a destination within the same routing protocol.



\### Function

\- Select the best path.

\- Optimize routing decisions.



\### Examples



| Protocol | Metric |

|----------|--------|

| RIP | Hop Count |

| OSPF | Cost |

| EIGRP | Composite Metric |



\### Real-World Example

OSPF chooses the path with the lowest total cost instead of the fewest hops.



\---



\# 5. Equal Cost Multi-Path (ECMP)



\### Definition

ECMP allows multiple equal-cost routes to be used simultaneously.



\### Function

\- Load balancing.

\- Increase bandwidth.

\- Improve redundancy.



\### Real-World Example

Traffic is distributed across two fiber links connecting the same office.



\---



\# 6. Open Shortest Path First (OSPF)



\### Definition

OSPF is a Link-State Interior Gateway Protocol (IGP) designed for enterprise networks.



\### Function

\- Discover routes automatically.

\- Calculate the shortest path.

\- React quickly to network changes.



\### Key Features

\- Link-State Protocol

\- SPF (Dijkstra) Algorithm

\- Fast Convergence

\- Scalable

\- Classless



\### Real-World Example

A university connects multiple buildings using OSPF for automatic routing.



\---



\# 7. OSPF Network Command



\### Definition

The \*\*network\*\* command determines which interfaces participate in OSPF.



\### Function

\- Enable OSPF.

\- Advertise connected networks.



\### Real-World Example

After configuring the network command, routers automatically exchange routing information.



\---



\# 8. OSPF Neighbor Adjacency



\### Definition

Neighbor Adjacency is the relationship between OSPF routers used to exchange Link-State information.



\### Function

\- Build neighbor relationships.

\- Synchronize the LSDB.

\- Exchange routing information.



\### Neighbor States



```

Down

&#x20;↓

Init

&#x20;↓

Two-Way

&#x20;↓

ExStart

&#x20;↓

Exchange

&#x20;↓

Loading

&#x20;↓

Full

```



\### Real-World Example

Two branch routers automatically become OSPF neighbors over a WAN connection.



\---



\# 9. Passive Interface



\### Definition

A Passive Interface advertises a network without sending OSPF Hello packets.



\### Function

\- Improve security.

\- Reduce unnecessary traffic.

\- Prevent unwanted neighbors.



\### Real-World Example

LAN interfaces connected to PCs advertise routes but never form OSPF neighbors with end devices.



\---



\# 10. OSPF Areas



\### Definition

An OSPF Area divides a large network into smaller logical sections.



\### Function

\- Improve scalability.

\- Reduce routing overhead.

\- Minimize LSDB size.



\### Real-World Example

A multinational company separates headquarters and branch offices into different OSPF areas.



\---



\# 11. OSPF Troubleshooting



\### Definition

Troubleshooting verifies OSPF operation and identifies routing issues.



\### Function

\- Detect configuration problems.

\- Verify neighbor relationships.

\- Restore connectivity.



\### Common Commands



```bash

show ip ospf neighbor

show ip ospf interface

show ip ospf database

show ip route ospf

show ip protocols

```



\### Real-World Example

A network engineer checks OSPF neighbors after a WAN outage.



\---



\# 12. Scaling OSPF



\### Definition

Scaling techniques improve OSPF performance in large networks.



\### Function

\- Reduce routing overhead.

\- Improve performance.

\- Simplify routing tables.



\### Features

\- Multi-Area OSPF

\- Route Summarization

\- Default Route

\- ASBR Redistribution



\### Real-World Example

Hundreds of branch routes are summarized into one route to reduce routing updates.



\---



\# 13. First Hop Redundancy Protocol (FHRP)



\### Definition

FHRP provides gateway redundancy by allowing multiple routers to share one virtual gateway.



\### Function

\- Eliminate gateway failure.

\- Automatic failover.

\- Increase network availability.



\### Real-World Example

If the primary gateway in a hospital fails, the backup gateway immediately takes over.



\---



\# 14. HSRP



\### Definition

Cisco proprietary gateway redundancy protocol.



\### Function

\- Active/Standby operation.

\- Automatic failover.



\### Real-World Example

Two Cisco routers protect a company's Internet gateway.



\---



\# 15. VRRP



\### Definition

Open-standard gateway redundancy protocol.



\### Function

\- Multi-vendor redundancy.

\- Master/Backup operation.



\### Real-World Example

Cisco and Juniper routers share the same virtual gateway.



\---



\# 16. GLBP



\### Definition

Cisco gateway redundancy protocol with load balancing.



\### Function

\- Gateway redundancy.

\- Load balancing.

\- Higher bandwidth utilization.



\### Real-World Example

Multiple gateway routers actively forward traffic in a university campus network.



\---



\# 17. Virtual IP \& Virtual MAC



\### Definition

A Virtual IP and Virtual MAC represent a shared gateway identity.



\### Function

\- Maintain the same default gateway.

\- Reduce failover interruption.



\### Real-World Example

Users continue browsing the Internet without changing gateway settings after the primary router fails.



\---



\# 📌 Summary



| Technology | Purpose |

|------------|---------|

| Routing Protocols | Exchange routing information |

| Route Selection | Choose the best path |

| Administrative Distance | Select the most trusted route |

| Metric | Select the lowest-cost path |

| ECMP | Load balancing |

| OSPF | Dynamic enterprise routing |

| FHRP | Gateway redundancy |

| HSRP | Cisco redundancy |

| VRRP | Multi-vendor redundancy |

| GLBP | Redundancy + Load Balancing |



\---



\# 🎯 Key Takeaways



\- Dynamic routing automatically learns and updates routes.

\- OSPF is the most common enterprise Link-State routing protocol.

\- Administrative Distance selects the routing source, while Metric selects the best path.

\- ECMP improves bandwidth utilization by using multiple equal-cost paths.

\- FHRP prevents gateway failures by providing automatic failover.

\- HSRP, VRRP, and GLBP increase network availability and reliability.

