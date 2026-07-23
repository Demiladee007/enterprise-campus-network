# Network Design

## 1. Design Goals

The network is designed to provide a scalable, resilient, and maintainable enterprise campus infrastructure for a manufacturing subsidiary with approximately 250 employees.

The design objectives are to:

* Support reliable connectivity for users, manufacturing equipment, servers, printers, surveillance systems, and management devices.
* Provide high availability through redundant network paths and gateway redundancy.
* Deliver resilient Internet connectivity using dual Internet Service Providers (ISPs).
* Simplify network growth through a modular three-tier architecture.
* Support future expansion, including integration with the parent company's headquarters and additional enterprise services.


## 2. Network Architecture

The network follows the Cisco three-tier campus architecture consisting of the Core, Distribution, and Access layers. This hierarchical approach separates network responsibilities, improves scalability, simplifies troubleshooting, and provides multiple opportunities for redundancy.

### Edge Layer

A single edge router provides connectivity to two independent Internet Service Providers (ISPs). The edge router performs Network Address Translation (NAT), hosts DHCP services for client networks, and provides Internet access with automatic ISP failover.

### Core Layer

The core layer consists of two Layer 3 switches connected using a Layer 3 EtherChannel. The core provides fast and resilient transport between the edge router and the distribution layer while participating in OSPF Area 0.

### Distribution Layer

The distribution layer consists of two Layer 3 switches connected redundantly to both core switches. Switch Virtual Interfaces (SVIs) provide inter-VLAN routing, while HSRP provides a resilient default gateway for end devices.

### Access Layer

The access layer connects end devices including office users, manufacturing equipment, surveillance cameras, printers, and servers. VLAN segmentation is implemented to logically separate network traffic, while PVST+ provides loop prevention across Layer 2 switching paths.




## 3. Logical Topology

The logical topology follows a hierarchical enterprise campus design.

* Dual ISP connectivity
* Single edge router
* Dual core switches
* Dual distribution switches
* Redundant uplinks
* Layer 3 EtherChannel
* HSRP gateway redundancy
* Layer 2 access layer

*A logical topology diagram is provided in the repository.*

---

## 4. IP Addressing Plan

The network uses the private IPv4 address block 10.0.0.0/8.

User VLANs follow the addressing convention:

> **10.<Site>.<VLAN>.0/24**

This approach provides predictable addressing while allowing future expansion to additional sites without requiring network redesign.

Infrastructure links use /30 networks to conserve address space, while all infrastructure devices are assigned /32 loopback interfaces for stable router identification and management.

---

## 5. VLAN Design

The network is segmented into functional VLANs to improve security, simplify administration, and reduce broadcast domains.

Current VLANs include:

* Office Users
* Surveillance Cameras
* Servers
* Manufacturing Equipment
* Printers
* Network Management

Each VLAN is assigned a dedicated subnet and an SVI on the distribution layer. HSRP virtual IP addresses provide the default gateway for end devices.

---

## 6. Routing Design

Dynamic routing is provided using single-area OSPF (Area 0).

OSPF was selected because it provides automatic route learning, rapid convergence, and scalability compared to static routing. Infrastructure loopback interfaces provide stable router identifiers.

The edge router originates the default route, allowing internal devices to reach external networks through the available ISP connection.

---

## 7. High Availability

High availability is incorporated throughout the network.

### Gateway Redundancy

HSRP provides resilient default gateway services for all VLANs. End devices use the HSRP virtual IP as their default gateway, allowing gateway availability to be maintained if a distribution switch fails.

### Core Redundancy

The core switches are interconnected using a Layer 3 EtherChannel, providing increased bandwidth and resilience against individual link failures.

### Internet Redundancy

The edge router maintains connectivity to two independent Internet Service Providers. NAT failover ensures Internet connectivity is maintained when the primary ISP becomes unavailable.

---

## 8. Design Decisions

The following design decisions were made during implementation:

* A three-tier architecture was selected to provide scalability and simplify future expansion.
* OSPF was selected to simplify route management and support future network growth.
* Functional VLANs were used to logically separate user devices, manufacturing equipment, servers, surveillance systems, printers, and management traffic.
* DHCP services were centralized on the edge router to simplify address management.
* /30 point-to-point networks were used on routed links to efficiently utilize IPv4 address space.
* /32 loopback interfaces provide stable router identifiers and management addresses.
* Dual ISP connectivity improves Internet availability during provider outages.

---

## 9. Current Limitations

The current implementation focuses on the wired enterprise campus infrastructure.

Wireless networking, headquarters integration, firewall services, VPN connectivity, network monitoring, IPv6, and automation are outside the scope of Version 1 and will be introduced as the project evolves.

---

## 10. Future Enhancements

Future project phases may include:

* Headquarters integration
* Cisco ASA firewall deployment
* Site-to-site VPN connectivity
* IPv6 implementation
* Enterprise wireless infrastructure
* Network monitoring and logging
* Infrastructure automation
* Additional branch offices
