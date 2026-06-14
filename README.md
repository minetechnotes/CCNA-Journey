# CCNA-Journey
My personal CCNA learning notes
# Networking Fundamentals

## Introduction

Networking is the foundation of computer communication.
A network allows devices to communicate and share data.

Example:

```text
Laptop → WiFi → Router → Internet → Website
```

---

## What is a Network?

A network is a group of connected devices that can send and receive data.

Simple meaning:

```text
Network = Devices talking to each other
```

---

## Switch

A switch connects devices inside the same local network.

Example:

```text
Laptop → Switch → Printer
```

Key point:

```text
Switch = MAC Address = Local Network
```

---

## Router

A router connects different networks, such as a home network to the internet.

Example:

```text
Laptop → WiFi → Router → Internet
```

Key point:

```text
Router = IP Address = Different Networks
```

---

## Switch vs Router

A switch connects devices in the same network.
A router connects different networks.

Simple memory:

```text
Switch = Local Network
Router = Internet / Different Network
```

---

## TCP/IP Model

TCP/IP is the real networking model used by the internet.

Simple meaning:

```text
TCP/IP = Real internet communication model
```

---

## OSI Model

The OSI Model helps us understand how data moves through a network.

Important layers to remember:

```text
Layer 7 = Application
Layer 4 = TCP / UDP
Layer 3 = IP / Router
Layer 2 = MAC / Switch
Layer 1 = Cable / WiFi
```

---

## Encapsulation

Encapsulation is the process of wrapping data before sending it.

```text
Data → Segment → Packet → Frame → Bits
```

Simple example:

```text
Encapsulation is like putting a message inside an envelope before sending it.
```

---

## De-encapsulation

De-encapsulation is the process of opening the data when it reaches the destination.

```text
Bits → Frame → Packet → Segment → Data
```

Simple example:

```text
De-encapsulation is like opening a package step by step until we can read the message inside.
```

---

## Basic Commands

Check connection:

```bash
ping google.com
```

Check IP address:

```bash
ipconfig
```

Check network path:

```bash
tracert google.com
```

---

## Quick Summary

```text
Network = Devices communicate
Switch = Local network
Router = Different networks
IP Address = Logical address
MAC Address = Physical address
DNS = Domain name to IP address
TCP/IP = Real internet model
OSI = Troubleshooting model
Encapsulation = Wrapping data
De-encapsulation = Opening data
```

---

## Conclusion

Networking is the first step in understanding how computers communicate.

By learning networks, switches, routers, IP addresses, MAC addresses, TCP/IP, OSI Model, encapsulation, and de-encapsulation, we can understand how data moves from one device to another.
