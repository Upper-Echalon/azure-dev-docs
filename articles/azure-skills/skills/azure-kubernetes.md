---
title: azure-kubernetes
description: Plan, create, and configure production-ready Azure Kubernetes Service (AKS) clusters. Covers Day-0 checklist, SKU selection (Automatic vs Standard), networking options (private API server, Azure CNI Overlay, egress configuration), security, and operations (autoscaling, upgrade strategy, cost analysis).
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-kubernetes

Plan, create, and configure production-ready Azure Kubernetes Service (Azure Kubernetes Service (AKS)) clusters. Covers Day-0 checklist, SKU selection (Automatic vs Standard), networking options (private API server, Azure CNI Overlay, egress configuration), security, and operations (autoscaling, upgrade strategy, cost analysis).

**Skill:** `azure-kubernetes` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-kubernetes)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-kubernetes`** skill when you need to:

- Create AKS environment
- Provision AKS environment
- Enable AKS observability
- Design AKS networking
- Choose AKS Sku
- Secure AKS


## What it provides

The `azure-kubernetes` skill provides GitHub Copilot with specialized knowledge. Plan, create, and configure production-ready Azure Kubernetes Service (AKS) clusters. Covers Day-0 checklist, SKU selection (Automatic vs Standard), networking options (private API server, Azure CNI Overlay, egress configuration), security, and operations (autoscaling, upgrade strategy, cost analysis).

### Related tools

| Tool | Command | Purpose |
|------|---------|---------|
| `mcp_azure_mcp_aks` | `AKS Model Context Protocol (MCP) entry point used to discover the exact AKS-specific tools exposed by the client` | Discover the callable AKS tool first, then use that tool's parameters |





## Related content

- [Azure MCP Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
