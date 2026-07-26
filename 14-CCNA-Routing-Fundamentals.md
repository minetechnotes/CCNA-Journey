\# CCNA Routing Fundamentals



> A concise guide covering the essential CCNA routing concepts, from Routing Protocols to First Hop Redundancy Protocol (FHRP).



\---



\## 📚 Table of Contents



\* Categories of Routing Protocols

\* Route Selection

\* Administrative Distance \& Metric

\* Equal Cost Multi-Path (ECMP)

\* Open Shortest Path First (OSPF)

\* OSPF Network Command

\* OSPF Neighbor Adjacency

\* Passive Interface

\* OSPF Areas

\* OSPF Troubleshooting

\* OSPF Scaling

\* First Hop Redundancy Protocol (FHRP)

\* HSRP

\* VRRP

\* GLBP

\* Virtual IP \& Virtual MAC



\---



\# Categories of Routing Protocols



\## Definition



Routing protocols allow routers to exchange routing information automatically and build routing tables.



\## Function



\* Discover network routes automatically.

\* Adapt to topology changes.

\* Reduce manual configuration.



\## Types



| Protocol Type   | Example | Description                                       |

| --------------- | ------- | ------------------------------------------------- |

| Distance Vector | RIP     | Learns routes from neighbors.                     |

| Link-State      | OSPF    | Builds a complete topology map.                   |

| Path Vector     | BGP     | Uses routing policies between Autonomous Systems. |



\### Real-World Example



A company with multiple branch offices uses \*\*OSPF\*\* so every router automatically learns new routes without manual configuration.



\---



\# Route Selection



\## Definition



Route Selection is the process of choosing the best available path to reach a destination.



\## Function



\* Select the optimal route.

\* Improve routing efficiency.

\* Prevent routing conflicts.



\## Selection Order



```text

Longest Prefix Match

\\\&#x20;       ↓

Administrative Distance

\\\&#x20;       ↓

Metric

```



\### Real-World Example



If multiple routes exist, the router installs the most trusted and lowest-cost route into the routing table.



\---



\# Administrative Distance \& Metric



\## Administrative Distance (AD)



Measures the trustworthiness of a routing source.



\*\*Lower AD = Higher Priority\*\*



| Protocol  |  AD |

| --------- | --: |

| Connected |   0 |

| Static    |   1 |

| EIGRP     |  90 |

| OSPF      | 110 |

| RIP       | 120 |



\## Metric



Measures the path cost within the same routing protocol.



| Protocol | Metric           |

| -------- | ---------------- |

| RIP      | Hop Count        |

| OSPF     | Cost             |

| EIGRP    | Composite Metric |



\### Real-World Example



If both RIP and OSPF advertise the same network, the router prefers \*\*OSPF\*\* because its Administrative Distance is lower.



\---



\# Equal Cost Multi-Path (ECMP)



\## Definition



ECMP allows multiple equal-cost routes to be used simultaneously.



\## Function



\* Load balancing

\* Higher bandwidth utilization

\* Better redundancy



\### Real-World Example



Traffic is distributed across two fiber links connecting the same data centers.



\---



\# Open Shortest Path First (OSPF)



\## Definition



OSPF is a Link-State Interior Gateway Protocol (IGP) used in enterprise networks.



\## Function



\* Discover routes dynamically.

\* Calculate the shortest path.

\* React quickly to topology changes.



\### Key Features



\* Link-State

\* SPF (Dijkstra) Algorithm

\* Fast Convergence

\* Scalable

\* Classless Routing



\### Real-World Example



A university uses OSPF to connect multiple campus buildings with automatic route discovery.



\---



\# OSPF Network Command



\## Definition



The \*\*network\*\* command determines which interfaces participate in OSPF.



\## Function



\* Enable OSPF on matching interfaces.

\* Advertise connected networks.



\### Real-World Example



Once configured, neighboring routers automatically exchange routing information.



\---



\# OSPF Neighbor Adjacency



\## Definition



Neighbor Adjacency is the relationship established between OSPF routers.



\## Function



\* Exchange Link-State information.

\* Synchronize LSDB.

\* Build routing tables.



\### Neighbor States



```text

Down

\\\&#x20;↓

Init

\\\&#x20;↓

Two-Way

\\\&#x20;↓

ExStart

\\\&#x20;↓

Exchange

\\\&#x20;↓

Loading

\\\&#x20;↓

Full

```



\### Real-World Example



Two branch routers automatically become neighbors after matching OSPF settings.



\---



\# Passive Interface



\## Definition



A Passive Interface advertises its network without sending Hello packets.



\## Function



\* Improve security.

\* Reduce unnecessary OSPF traffic.

\* Prevent unwanted neighbors.



\### Real-World Example



User LAN interfaces advertise routes but never form OSPF neighbor relationships with PCs.



\---



\# OSPF Areas



\## Definition



Areas divide a large OSPF network into smaller logical sections.



\## Function



\* Improve scalability.

\* Reduce LSDB size.

\* Decrease routing overhead.



\### Real-World Example



A global enterprise separates headquarters and regional offices into different OSPF areas.



\---



\# OSPF Troubleshooting



\## Common Commands



```bash

show ip ospf neighbor

show ip ospf interface

show ip ospf database

show ip route ospf

show ip protocols

```



\## Common Issues



\* Area mismatch

\* Timer mismatch

\* Authentication mismatch

\* Network type mismatch

\* Duplicate Router ID



\---



\# Scaling OSPF



\## Features



\* Multi-Area OSPF

\* Route Summarization

\* Default Route Advertisement

\* ASBR (Route Redistribution)



\### Real-World Example



A large enterprise summarizes hundreds of branch routes into one summary route to reduce routing overhead.



\---



\# First Hop Redundancy Protocol (FHRP)



\## Definition



FHRP provides gateway redundancy by allowing multiple routers to share a single virtual gateway.



\## Function



\* Eliminate the default gateway as a single point of failure.

\* Provide automatic failover.

\* Improve network availability.



\### Real-World Example



If the primary gateway fails in a hospital, users remain connected because the backup router immediately takes over.



\---



\# HSRP



\## Definition



Cisco proprietary First Hop Redundancy Protocol.



\## Function



\* Active / Standby gateway redundancy.

\* Automatic failover.



\### Real-World Example



Two Cisco routers protect the Internet gateway of a corporate network.



\---



\# VRRP



\## Definition



Open-standard First Hop Redundancy Protocol.



\## Function



\* Multi-vendor gateway redundancy.

\* Master / Backup operation.



\### Real-World Example



Cisco and Juniper routers share the same virtual gateway.



\---



\# GLBP



\## Definition



Cisco protocol that combines redundancy with load balancing.



\## Function



\* Gateway redundancy.

\* Traffic load balancing.

\* Higher bandwidth utilization.



\### Real-World Example



Multiple gateway routers actively forward traffic in a university campus network.



\---



\# Virtual IP \& Virtual MAC



\## Definition



A shared IP address and MAC address used by multiple gateway routers.



\## Function



\* Keep the default gateway consistent.

\* Minimize failover interruption.



\### Real-World Example



Users continue browsing the Internet without changing gateway settings after the primary router fails.



\---



\# Summary



| Technology              | Primary Purpose                        |

| ----------------------- | -------------------------------------- |

| Routing Protocols       | Exchange routing information           |

| Route Selection         | Choose the best path                   |

| Administrative Distance | Select the most trusted route          |

| Metric                  | Select the lowest-cost path            |

| ECMP                    | Load balancing across equal-cost paths |

| OSPF                    | Dynamic enterprise routing             |

| FHRP                    | Gateway redundancy                     |

| HSRP                    | Cisco redundancy                       |

| VRRP                    | Open-standard redundancy               |

| GLBP                    | Redundancy with load balancing         |



\---



\## Key Takeaways



\* Dynamic routing automates route discovery.

\* OSPF is the most common enterprise Link-State routing protocol.

\* Administrative Distance selects the routing source, while Metrics select the best path.

\* ECMP enables efficient traffic distribution.

\* FHRP ensures continuous gateway availability through automatic failover.

\* HSRP, VRRP, and GLBP improve network resilience and high availability.

