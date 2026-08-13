# Traffic Flows

This document describes the expected traffic paths through the enterprise Azure network.

The traffic flows demonstrate how routing, Azure Firewall, VNet peering, private endpoints, and hybrid connectivity work together.

---

## 1. Dev Workload to Internet

Internet-bound traffic from the Dev VNet is centrally inspected by Azure Firewall.

```text
Dev Workload
     |
     | Destination: Internet
     |
     v
UDR: 0.0.0.0/0
     |
     v
Azure Firewall
     |
     | SNAT / Security Inspection
     |
     v
Internet
