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

- Estimate costs for deploying resources to Azure.
- Analyze costs of provisioning infrastructure.
- Analyze diagnostics, security audits, and Azure spending patterns.
- Review your Azure bill, costs broken down by service, and costs per resource.
- Compare monthly cost summaries, identify cost trends, and pinpoint top cost drivers.
- Calculate amortized costs, forecast spending, and estimate your monthly bill.
- Plan future costs and set budget forecasts.
- Identify and implement cost optimization strategies.
- Find opportunities to reduce cloud spending.
- Discover cost-saving recommendations tailored to your infrastructure.

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
