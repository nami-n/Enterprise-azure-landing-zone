# IP Addressing Design

## Overview

The IP addressing strategy uses non-overlapping private address spaces for the Hub and workload VNets.

The design reserves sufficient address space for future growth while maintaining clear network boundaries between environments.

## VNet Address Spaces

| VNet | Address Space | Purpose |
|---|---|---|
| Hub VNet | 10.0.0.0/16 | Shared connectivity and security |
| Dev VNet | 10.10.0.0/16 | Development workloads |
| Test VNet | 10.20.0.0/16 | Test workloads |
| Prod VNet | 10.30.0.0/16 | Production workloads |

The address spaces do not overlap.

## Hub Subnet Design

The Hub VNet is divided into dedicated subnets for shared network services.

| Subnet | Address Range | Purpose |
|---|---|---|
| AzureFirewallSubnet | 10.0.0.0/26 | Azure Firewall |
| GatewaySubnet | 10.0.1.0/27 | VPN/ExpressRoute Gateway |
| AzureBastionSubnet | 10.0.2.0/26 | Azure Bastion |
| DNS Resolver | 10.0.3.0/28 | DNS Private Resolver |

Subnet sizes should be reviewed against the requirements of each Azure service and expected future growth.

## Dev Subnet Design

The Dev VNet can be segmented according to workload requirements.

Example:

| Subnet | Address Range | Purpose |
|---|---|---|
| Application | 10.10.1.0/24 | Application workloads |
| Data | 10.10.2.0/24 | Data workloads |
| PrivateEndpoints | 10.10.3.0/24 | Private Endpoints |

## Test Subnet Design

| Subnet | Address Range | Purpose |
|---|---|---|
| Application | 10.20.1.0/24 | Application workloads |
| Data | 10.20.2.0/24 | Data workloads |
| PrivateEndpoints | 10.20.3.0/24 | Private Endpoints |

## Prod Subnet Design

| Subnet | Address Range | Purpose |
|---|---|---|
| Application | 10.30.1.0/24 | Application workloads |
| Data | 10.30.2.0/24 | Data workloads |
| PrivateEndpoints | 10.30.3.0/24 | Private Endpoints |

## Addressing Considerations

The following factors were considered when designing the address space:

### 1. Non-overlapping Networks

VNet address spaces must not overlap with each other or with connected on-premises networks.

Overlapping address spaces can cause routing ambiguity and prevent reliable communication across VPN, ExpressRoute, and peering connections.

### 2. Future Growth

Address spaces are intentionally larger than the initial workload requirements.

This allows additional subnets and workloads to be added without redesigning the entire network.

### 3. Hybrid Connectivity

The Azure address space must be coordinated with the organization's on-premises IP addressing strategy.

For this design, the on-premises network is assumed to use a separate address range.

Example:

```text
On-Premises: 10.100.0.0/16
Azure Hub:   10.0.0.0/16
Azure Dev:   10.10.0.0/16
Azure Test:  10.20.0.0/16
Azure Prod:  10.30.0.0/16
