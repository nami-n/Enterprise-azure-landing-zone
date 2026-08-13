# Azure Firewall Design

## Overview

Azure Firewall is deployed in the centralized Connectivity Hub VNet to provide centralized network traffic inspection and policy enforcement.

The firewall provides a common security control point for workload traffic that requires centralized inspection.

## Architecture

```text
                    Connectivity Hub
                           |
                    Azure Firewall
                           |
              +------------+------------+
              |            |            |
            Dev          Test         Prod
            VNet         VNet         VNet
