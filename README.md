# Home Network Security Basics

Basic notes about router, switch, VLAN, Wi-Fi segmentation, and firewall rules.

## Core Concepts

```text
Router = connects network to internet
Switch = connects local devices
WAN    = internet input
LAN    = internal network
VLAN   = separated virtual network
```

## Network Segmentation

Separate devices by purpose:

```text
Personal = laptop and phone
Work     = work laptop
IoT      = CCTV and smart devices
Guest    = visitor devices
Lab      = cybersecurity practice
```

## Basic Firewall Rules

```text
Personal → Internet = Allow
IoT → Personal      = Block
Guest → LAN         = Block
Lab → Personal      = Block
```

## Wi-Fi Security

```text
Use WPA2/WPA3
Disable WPS
Use strong passwords
Enable guest isolation
Update router firmware
```

## Key Point

```text
Do not put all devices in one network.
```

Good network segmentation helps make the network safer and easier to manage.
