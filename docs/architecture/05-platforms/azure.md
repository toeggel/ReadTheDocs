---
tags:
  - WIP
  - Azure
---

```mermaid
graph TB
    subgraph subscription
	    rg1[resource group 1]
	    rg2[resource group 2]
	    rg3[resource group 3]
    end

```

## Subscription

A subscription can have multiple resource groups 

## Resource Group

Contain things that share a common lifecycle. They are created together, they run together, they get provisioned together. We can apply policies, RBAC, budget on resource group level

- App
- Workload 
- VM
- Storage account
- DB
- ...

Resource group cannot contain another resource group (no nesting)