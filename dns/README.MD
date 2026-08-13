# DNS Design

## Overview

The DNS architecture provides name resolution for Azure workloads, Private Endpoints, and on-premises resources.

The design supports both Azure-native DNS resolution and hybrid DNS resolution between Azure and the on-premises environment.

## Azure Private DNS

Azure Private DNS Zones are used to resolve Private Endpoint addresses.

Examples include:

- privatelink.database.windows.net
- privatelink.blob.core.windows.net

Private DNS zones are linked to the VNets that require resolution.

## Private Endpoint Name Resolution

When an application accesses an Azure PaaS service using its normal service FQDN, DNS resolution returns the private IP address associated with the Private Endpoint.

Example:

```text
Application
     |
     | DNS query
     v
Private DNS Zone
     |
     | Private IP
     v
Private Endpoint
     |
     v
Azure PaaS Service
