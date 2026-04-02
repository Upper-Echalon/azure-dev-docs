---
title: Azure Cost Optimization
description: Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Cost Optimization

Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste.

**Skill:** `azure-cost` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-cost)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

### Required resources

- **Azure Kubernetes Service cluster** — Azure Kubernetes Service (AKS) cluster for container orchestration

## When to use this skill

Use the **Azure Cost Optimization** skill when you need to:

- Deploying resources in Azure
- Provisioning infrastructure in Azure
- Work with diagnostics and security audits
- Or estimating costs for new resources not yet deployed
- Work with Azure costs, Azure spending, Azure bill, and cost breakdown
- Work with cost by service and cost by resource
- How much am I spending
- Work with show my bill, monthly cost summary, cost trends, and top cost drivers
- Work with actual cost, amortized cost, forecast spending, and projected costs
- Work with estimate bill, future costs, budget forecast, and end of month costs
- How much will I spend
- Optimize costs in Azure
- Work with reduce spending
- Find cost savings in Azure
- Work with orphaned resources, rightsize VMs, cost analysis, and reduce waste
- Work with unused resources
- Optimize Redis costs in Azure
- Work with cost by tag, cost by resource group, AKS cost analysis add-on, and namespace cost
- Work with cost spike, anomaly, budget alert, and AKS cost visibility

## What it provides

The Azure Cost Optimization skill provides GitHub Copilot with specialized knowledge. Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste.

### Related tools

| Tool | Command | Purpose |
|------|---------|---------|
| `azure__documentation` | `Search Azure documentation` | `query` (Required): search terms |
| `azure__extension_cli_generate` | `Generate Azure CLI commands` | `intent` (Required): task description, `cli-type` (Required): `"az"` |
| `azure__get_azure_bestpractices` | `Get Azure best practices` | `intent` (Required): optimization context |
| `azure__extension_azqr` | `Run Azure Quick Review compliance scan` | `subscription` (Required): subscription ID, `resource-group` (Optional): resource group name |
| `azure__aks` | `Azure Kubernetes Service operations` | varies by sub-command |





## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
