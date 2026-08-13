# Networking Design

## Network Architecture

The solution uses a hub-and-spoke network topology.

A centralized Hub VNet is deployed in a dedicated Connectivity subscription. Development, Test, and Production workloads are deployed in separate spoke VNets.

## Virtual Networks

| Network | Address Space | Purpose |
|---|---|---|
| Hub VNet | 10.0.0.0/16 | Central connectivity and security |
| Dev VNet | 10.10.0.0/16 | Development workloads |
| Test VNet | 10.20.0.0/16 | Test workloads |
| Prod VNet | 10.30.0.0/16 | Production workloads |

## Hub VNet Subnets

The Hub VNet contains dedicated subnets for shared network services.

| Subnet | Purpose |
|---|---|
| AzureFirewallSubnet | Azure Firewall |
| GatewaySubnet | VPN/ExpressRoute Gateway |
| AzureBastionSubnet | Azure Bastion |
| DNS Resolver subnet | Azure DNS Private Resolver |

## Spoke Connectivity

Each spoke VNet is peered with the Hub VNet.

```text
                 Hub VNet
                10.0.0.0/16
                     |
       +-------------+-------------+
       |             |             |
       |             |             |
    Dev VNet      Test VNet      Prod VNet
  10.10.0.0/16  10.20.0.0/16  10.30.0.0/16
