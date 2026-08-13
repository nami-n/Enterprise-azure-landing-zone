# Security Design

## Overview

Security is implemented using a layered approach across the Azure environment.

The design separates workload-level controls from centralized network security services.

## Centralized Network Security

Azure Firewall is deployed in the Connectivity Hub VNet.

The firewall provides centralized inspection and control of network traffic between:

- Azure workloads
- On-premises networks
- Internet destinations
- Other network segments where centralized inspection is required

## Internet Egress

Spoke workloads can use User Defined Routes (UDRs) to send Internet-bound traffic through Azure Firewall.

```text
Spoke VNet
    |
    | 0.0.0.0/0
    |
    v
Azure Firewall
    |
    v
Internet
