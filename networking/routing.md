# Routing Design

## Overview

The routing architecture controls how traffic moves between Azure workload VNets, the centralized Connectivity Hub, on-premises networks, and the Internet.

The design uses a combination of:

- System routes
- VNet peering
- User Defined Routes (UDRs)
- VPN/ExpressRoute route propagation
- Azure Firewall
- BGP for dynamic hybrid route exchange

---

## 1. Spoke-to-Hub Connectivity

Dev, Test, and Prod VNets are connected to the Hub VNet through VNet peering.

```text
              Hub VNet
                  |
       +----------+----------+
       |          |          |
      Dev        Test       Prod
