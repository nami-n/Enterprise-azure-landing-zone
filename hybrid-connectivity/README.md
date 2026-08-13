# Hybrid Connectivity Design

## Overview

The organization has an on-premises datacenter in Toronto that requires secure connectivity to Azure workloads.

The Azure Connectivity Hub provides the centralized entry point for hybrid connectivity.

The design can support both site-to-site VPN and ExpressRoute depending on connectivity, performance, and business requirements.

## High-Level Connectivity

```text
                    On-Premises
                 Toronto Datacenter
                         |
                +--------+--------+
                |                 |
             VPN/            ExpressRoute
          Internet               |
                |                 |
                +--------+--------+
                         |
                  Connectivity Hub
                         |
                 Azure Hub VNet
                         |
              +----------+----------+
              |          |          |
             Dev        Test       Prod
             VNet       VNet       VNet
