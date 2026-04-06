---
title: Azure skill for cost optimization
description: Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for cost optimization

Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste.

**Skill:** `azure-cost` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-cost)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

### Required resources

- **Azure Kubernetes Service cluster**—Azure Kubernetes Service (AKS) cluster for container orchestration

## When to use this skill

Use this skill when you need to:

- Deploying resources in Azure
- Provisioning infrastructure in Azure
- Work with diagnostics, security audits, Azure costs, and Azure spending
- Work with Azure bill, cost breakdown, cost by service, and cost by resource
- Work with monthly cost summary, cost trends, top cost drivers, and actual cost
- Work with amortized cost, forecast spending, projected costs, and estimate bill
- Work with future costs, budget forecast, and end of month costs
- Optimize costs in Azure
- Work with reduce spending
- Find cost savings in Azure

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste.

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
