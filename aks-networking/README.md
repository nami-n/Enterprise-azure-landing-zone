# AKS Networking Design

## Overview

Azure Kubernetes Service (AKS) workloads can be integrated into the enterprise hub-and-spoke architecture.

AKS is deployed as a workload in a spoke VNet while centralized network security, DNS, and hybrid connectivity are provided by the Connectivity Hub.

## High-Level Architecture

```text
                    Connectivity Hub
                           |
                    Azure Firewall
                           |
                     Hub VNet
                           |
                    VNet Peering
                           |
                       AKS VNet
                           |
                    AKS Cluster
                 +---------+---------+
                 |                   |
              AKS Nodes           Pods
                 |
        +--------+--------+
        |                 |
    Private Endpoints   Ingress
        |                 |
        v                 v
    Azure PaaS       Application
