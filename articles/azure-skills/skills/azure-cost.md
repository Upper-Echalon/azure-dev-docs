---
title: azure-cost
description: Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste. WHEN: &quot;Azure costs&quot;, &quot;Azure spending&quot;, &quot;Azure bill&quot;, &quot;cost breakdown&quot;, &quot;cost by service&quot;, &quot;cost by resource&quot;, &quot;how much am I spending&quot;, &quot;show my bill&quot;, &quot;monthly cost summary&quot;, &quot;cost trends&quot;, &quot;top cost drivers&quot;, &quot;actual cost&quot;, &quot;amortized cost&quot;, &quot;forecast spending&quot;, &quot;projected costs&quot;, &quot;estimate bill&quot;, &quot;future costs&quot;, &quot;budget forecast&quot;, &quot;end of month costs&quot;, &quot;how much will I spend&quot;, &quot;optimize costs&quot;, &quot;reduce spending&quot;, &quot;find cost savings&quot;, &quot;orphaned resources&quot;, &quot;rightsize VMs&quot;, &quot;cost analysis&quot;, &quot;reduce waste&quot;, &quot;unused resources&quot;, &quot;optimize Redis costs&quot;, &quot;cost by tag&quot;, &quot;cost by resource group&quot;, &quot;AKS cost analysis add-on&quot;, &quot;namespace cost&quot;, &quot;cost spike&quot;, &quot;anomaly&quot;, &quot;budget alert&quot;, &quot;AKS cost visibility&quot;. DO NOT.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-cost

Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste. WHEN: &quot;Azure costs&quot;, &quot;Azure spending&quot;, &quot;Azure bill&quot;, &quot;cost breakdown&quot;, &quot;cost by service&quot;, &quot;cost by resource&quot;, &quot;how much am I spending&quot;, &quot;show my bill&quot;, &quot;monthly cost summary&quot;, &quot;cost trends&quot;, &quot;top cost drivers&quot;, &quot;actual cost&quot;, &quot;amortized cost&quot;, &quot;forecast spending&quot;, &quot;projected costs&quot;, &quot;estimate bill&quot;, &quot;future costs&quot;, &quot;budget forecast&quot;, &quot;end of month costs&quot;, &quot;how much will I spend&quot;, &quot;optimize costs&quot;, &quot;reduce spending&quot;, &quot;find cost savings&quot;, &quot;orphaned resources&quot;, &quot;rightsize VMs&quot;, &quot;cost analysis&quot;, &quot;reduce waste&quot;, &quot;unused resources&quot;, &quot;optimize Redis costs&quot;, &quot;cost by tag&quot;, &quot;cost by resource group&quot;, &quot;Azure Kubernetes Service (AKS) cost analysis add-on&quot;, &quot;namespace cost&quot;, &quot;cost spike&quot;, &quot;anomaly&quot;, &quot;budget alert&quot;, &quot;AKS cost visibility&quot;. don't.

**Skill:** `azure-cost` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-cost)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-cost`** skill when you need to:

- Deploying resources
- Provisioning infrastructure
- Work with diagnostics and security audits
- Or estimating costs for new resources not yet deployed
- Work with Azure costs, Azure spending, Azure bill, and cost breakdown
- Work with cost by service and cost by resource
- How much am I spending
- Work with show my bill, monthly cost summary, cost trends, and top cost drivers
- Work with actual cost, amortized cost, forecast spending, and projected costs
- Work with estimate bill, future costs, budget forecast, and end of month costs
- How much will I spend
- Optimize costs
- Work with reduce spending
- Find cost savings
- Work with orphaned resources, rightsize VMs, cost analysis, and reduce waste
- Work with unused resources
- Optimize Redis costs
- Work with cost by tag, cost by resource group, AKS cost analysis add-on, and namespace cost
- Work with cost spike, anomaly, budget alert, and AKS cost visibility

### When NOT to use this skill

Don't use this skill for:

- Deploying resources
- Provisioning infrastructure
- Work with diagnostics and security audits
- Or estimating costs for new resources not yet deployed

## What it provides

The `azure-cost` skill provides GitHub Copilot with specialized knowledge. Unified Azure cost management: query historical costs, forecast future spending, and optimize to reduce waste. WHEN: &quot;Azure costs&quot;, &quot;Azure spending&quot;, &quot;Azure bill&quot;, &quot;cost breakdown&quot;, &quot;cost by service&quot;, &quot;cost by resource&quot;, &quot;how much am I spending&quot;, &quot;show my bill&quot;, &quot;monthly cost summary&quot;, &quot;cost trends&quot;, &quot;top cost drivers&quot;, &quot;actual cost&quot;, &quot;amortized cost&quot;, &quot;forecast spending&quot;, &quot;projected costs&quot;, &quot;estimate bill&quot;, &quot;future costs&quot;, &quot;budget forecast&quot;, &quot;end of month costs&quot;, &quot;how much will I spend&quot;, &quot;optimize costs&quot;, &quot;reduce spending&quot;, &quot;find cost savings&quot;, &quot;orphaned resources&quot;, &quot;rightsize VMs&quot;, &quot;cost analysis&quot;, &quot;reduce waste&quot;, &quot;unused resources&quot;, &quot;optimize Redis costs&quot;, &quot;cost by tag&quot;, &quot;cost by resource group&quot;, &quot;AKS cost analysis add-on&quot;, &quot;namespace cost&quot;, &quot;cost spike&quot;, &quot;anomaly&quot;, &quot;budget alert&quot;, &quot;AKS cost visibility&quot;. don't.

### Related tools

| Tool | Command | Purpose |
|------|---------|---------|
| `azure__documentation` | `Search Azure documentation` | `query` (Required): search terms |
| `azure__extension_cli_generate` | `Generate Azure CLI commands` | `intent` (Required): task description, `cli-type` (Required): `&quot;az&quot;` |
| `azure__get_azure_bestpractices` | `Get Azure best practices` | `intent` (Required): optimization context |
| `azure__extension_azqr` | `Run Azure Quick Review compliance scan` | `subscription` (Required): subscription ID, `resource-group` (Optional): resource group name |
| `azure__aks` | `Azure Kubernetes Service operations` | varies by sub-command |





## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
