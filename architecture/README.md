# Architecture

This section documents the enterprise Azure Landing Zone and hub-and-spoke architecture.

## Architecture Objectives

The architecture is designed to provide:

- Centralized connectivity
- Environment isolation
- Centralized network security
- Controlled internet egress
- Hybrid connectivity
- Private access to Azure PaaS services
- Centralized DNS
- Scalability for future Azure subscriptions

## High-Level Design

The environment uses a centralized connectivity hub with separate workload spokes for development, test, and production.

The Connectivity subscription owns shared network infrastructure, while workload subscriptions remain separated from the shared platform.

## Key Design Components

### Connectivity Hub

The hub provides centralized:

- Network connectivity
- Azure Firewall
- VPN/ExpressRoute connectivity
- DNS services
- Shared network services

### Spoke VNets

Separate VNets are used for:

- Development
- Test
- Production

The spokes connect to the central hub through VNet peering.

### Traffic Inspection

Internet-bound and selected inter-VNet traffic can be routed through Azure Firewall using User Defined Routes.

### Private PaaS Connectivity

Private Endpoints provide private connectivity from workloads to Azure PaaS services.

Private DNS is used to resolve the private endpoint addresses.

## Design Principle

Shared connectivity infrastructure is separated from workload subscriptions to provide:

- Clear ownership
- Separation of duties
- Centralized security
- Reduced blast radius
- Scalability
