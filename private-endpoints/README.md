# Private Endpoint Design

## Overview

Azure Private Endpoints provide private connectivity from Azure VNets to supported Azure PaaS services.

The design avoids unnecessary exposure of PaaS services through public endpoints.

## Example Architecture

The Production environment uses Azure SQL as an example PaaS service.

```text
Prod Application
       |
       | Private IP
       v
Private Endpoint
       |
       v
Azure SQL Database
