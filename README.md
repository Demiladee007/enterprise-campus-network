# Enterprise Campus Network

A simulated enterprise campus network for a manufacturing subsidiary, designed to demonstrate practical enterprise networking skills through realistic architecture, redundancy, routing, and documentation.



## Project Overview

This project implements a scalable three-tier enterprise campus network supporting approximately 250 employees across a manufacturing plant and multiple office areas. The network is designed using enterprise best practices and focuses on high availability, resiliency, and future scalability.

The implementation simulates a production environment consisting of dual ISP connectivity, redundant core and distribution layers, dynamic routing, gateway redundancy, and segmented network services.



## Features

* Three-tier enterprise campus architecture
* Single-area OSPF routing
* Layer 3 EtherChannel
* HSRP gateway redundancy
* Dual ISP connectivity
* NAT with ISP failover
* DHCP services
* VLAN segmentation
* PVST+
* Loopback interfaces on infrastructure devices
* Structured IP addressing
* Comprehensive project documentation


## Technologies

* Cisco IOS
* EVE-NG
* OSPF
* HSRP
* EtherChannel
* VLANs
* NAT
* DHCP
* Git
* GitHub
* draw.io



## Network Topology

![Logical topology diagram](../enterprise-campus-network/topology/topology.drawio)



## Repository Structure


docs/
├── project-overview.md
├── network-design.md
├── implementation.md
├── verification.md
└── future-enhancements.md

configs/
diagrams/
images/
topology/
verification/



## Documentation

Detailed documentation is available in the `docs` directory.

* Project Overview
* Network Design
* Implementation
* Verification
* Future Enhancements



## Current Version

**Version:** 1.0

Current implementation focuses on the enterprise campus infrastructure. Future versions will introduce additional enterprise technologies including headquarters integration, firewall deployment, VPN connectivity, network monitoring, and automation.

