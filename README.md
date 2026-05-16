# Windows Networking Lab

## Overview

This project simulates a small multi
-subnet Windows network environment using Hyper-V and Windows Server technologies.

The lab focuses on:

- TCP/IP networking fundamentals
- DHCP configuration
- DNS configuration
- Routing between subnets using RRAS
- Cross-subnet communication
- Windows networking administration

The environment was built to strengthen practical networking skills commonly required for IT Support and Junior System Administrator roles.

---

# Technologies Used

- Windows Server 2022
- Hyper-V
- Routing and Remote Access (RRAS)
- DHCP
- DNS
- Windows 10
- TCP/IP Networking

---

# Network Architecture

Two isolated internal networks were created in Hyper-V:

- LAN-SALES → 192.168.10.0/24
- LAN-IT → 192.168.20.0/24

FS01 acts as the router between both networks.

| Machine | Role | IP Address |
|---|---|---|
| DC01 | DNS + DHCP Server | 192.168.10.10 |
| FS01 NIC1 | Router Interface (SALES) | 192.168.10.1 |
| FS01 NIC2 | Router Interface (IT) | 192.168.20.1 |
| WIN10-01 | SALES Client | DHCP |
| WIN10-02 | IT Client | 192.168.20.20 |

---

# Architecture Diagram

![Architecture](Networking.drawio.png)

---

# Hyper-V Environment

The lab environment was deployed using Hyper-V virtual machines.

- DC01
- FS01
- WIN10-01
- WIN10-02

![Hyper-V Topology](01-hyperv-topology.png)

---

# Network Adapter Configuration

FS01 contains two network adapters to route traffic between both subnets.

- SALES Network → 192.168.10.1
- IT Network → 192.168.20.1

![FS01 NIC Configuration](02-fs01-nics.png)

---

# DC01 Network Configuration

DC01 is configured as the DHCP and DNS server for the SALES subnet.

![DC01 IP Configuration](03-dc01-ipconfig.png)

---

# DHCP Configuration

DC01 provides DHCP services for the SALES subnet.

DHCP scope:
- Network: 192.168.10.0/24
- Gateway: 192.168.10.1
- DNS Server: 192.168.10.10

![DHCP Scope](06-dhcp-scope.png)

WIN10-01 successfully receives an IP address from DHCP.

![WIN10-01 DHCP Lease](04-win10-01-dhcp.png)

---

# DNS Configuration

DNS records were configured on DC01 for devices in the environment.

Configured records:
- DC01
- FS01
- WIN10-01
- WIN10-02

![DNS Records](05-dns-records.png)

---

# Routing Configuration

FS01 was configured with Routing and Remote Access Service (RRAS) to enable communication between the SALES and IT subnets.

![RRAS Configuration](07-routing-enabled.png)

---

# Cross-Subnet Connectivity Testing

Connectivity between subnets was verified using:

- ping
- tracert

WIN10-02 successfully communicates with devices in the SALES subnet.

## Ping Test

![Cross-Subnet Ping](08-cross-subnet-ping.png)

## Tracert Test

![Tracert](09-tracert.png)

---

# Skills Demonstrated

- Windows networking fundamentals
- TCP/IP configuration
- DHCP administration
- DNS configuration
- RRAS routing
- Subnetting and gateway configuration
- Multi-subnet communication
- Network connectivity testing

---

# Purpose of the Lab

This lab was created to practice Windows networking and routing concepts in a virtualized environment using Hyper-V.