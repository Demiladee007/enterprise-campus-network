# Implementation

## 1. Overview

This document describes the implementation of the enterprise campus network. It outlines the deployment sequence, the role of each network device, and the major configuration tasks performed during implementation.

Detailed device configurations are maintained separately in the `configs/` directory.

---

## 2. Network Devices

The implemented network consists of the following infrastructure:

| Device              | Quantity | Role                                      |
| ------------------- | -------: | ----------------------------------------- |
| Edge Router         |        1 | Internet connectivity, NAT, DHCP          |
| Core Switch         |        2 | High-speed Layer 3 backbone               |
| Distribution Switch |        2 | Inter-VLAN routing and gateway redundancy |
| Access Switch       |        2 | End-device connectivity                   |
| ISP Router          |        2 | Simulated Internet Service Providers      |



## 3. Implementation Sequence

The network was implemented using the following high-level sequence:

1. Configure device hostnames and management settings.
2. Configure Layer 3 point-to-point links.
3. Configure loopback interfaces.
4. Configure OSPF routing.
5. Configure VLANs.
6. Configure Layer 2 trunk links.
7. Configure Switch Virtual Interfaces (SVIs).
8. Configure HSRP gateway redundancy.
9. Configure Layer 3 EtherChannel.
10. Configure DHCP services.
11. Configure NAT.
12. Configure dual ISP failover.
13. Verify end-to-end connectivity.


## 4. Infrastructure Services

### Dynamic Routing

Single-area OSPF (Area 0) provides dynamic routing between Layer 3 devices.

### Gateway Redundancy

HSRP provides resilient default gateway services for all user VLANs.

### Internet Connectivity

The edge router provides Internet connectivity through two independent ISPs using NAT with automatic failover.

### DHCP

The edge router centrally allocates IP addresses for client VLANs.


## 5. Validation

Following implementation, the network was validated to confirm:

* End-to-end connectivity.
* Inter-VLAN routing.
* Dynamic route propagation.
* HSRP operation.
* EtherChannel operation.
* DHCP address allocation.
* Internet connectivity.
* ISP failover.

Detailed validation results are provided in ![verification](../docs/verification.md)
