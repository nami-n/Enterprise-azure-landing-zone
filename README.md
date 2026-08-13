# Enterprise Azure Landing Zone & Hub-Spoke Architecture

## Overview

This project demonstrates the design of an enterprise Azure Landing Zone using a hub-and-spoke network architecture.

The architecture is designed for an organization that requires secure connectivity between on-premises infrastructure and Azure workloads while maintaining strong separation between development, test, and production environments.

## Objectives

- Design a scalable Azure Landing Zone
- Separate workload environments using dedicated subscriptions
- Centralize network connectivity and security
- Provide secure hybrid connectivity to on-premises infrastructure
- Control internet-bound traffic through centralized security
- Provide private connectivity to Azure PaaS services
- Implement centralized DNS architecture
- Establish a foundation for future AKS and cloud workloads

## High-Level Architecture

The proposed architecture consists of a centralized connectivity hub and multiple workload spokes.

```text
                    On-Premises
                         |
                  VPN / ExpressRoute
                         |
                 Connectivity Hub
                         |
          +--------------+--------------+
          |              |              |
       Dev VNet       Test VNet      Prod VNet
          |              |              |
       Workloads      Workloads      Workloads
                                         |
                                  Private Endpoints
                                         |
                                  Azure PaaS Services
