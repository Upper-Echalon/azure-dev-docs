---
title: Azure Resource Lookup
description: List, find, and show Azure resources across subscriptions or resource groups. Handles prompts like &quot;list websites&quot;, &quot;list virtual machines&quot;, &quot;list my VMs&quot;, &quot;show storage accounts&quot;, &quot;find container apps&quot;, and &quot;what resources do I have&quot;.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Resource Lookup

List, find, and show Azure resources across subscriptions or resource groups. Handles prompts like &quot;list websites&quot;, &quot;list virtual machines&quot;, &quot;list my VMs&quot;, &quot;show storage accounts&quot;, &quot;find container apps&quot;, and &quot;what resources do I have&quot;.

**Skill:** `azure-resource-lookup` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-resource-lookup)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

### Required resources

- **Azure Key Vault** — Key vault for secrets and certificate management
- **Azure Storage account** — Storage account for blob, file, queue, or table data
- **Azure Kubernetes Service cluster** — Azure Kubernetes Service (AKS) cluster for container orchestration
- **Azure Cosmos DB account** — Cosmos DB account for NoSQL data

## When to use this skill

Use the **Azure Resource Lookup** skill when you need to:

- Work with resource inventory
- Find resources by tag
- Work with tag analysis
- Orphaned resource discovery (not for cost analysis)
- Work with unattached disks, count resources by type, and cross-subscription lookup
- And Azure Resource Graph queries

## What it provides

The Azure Resource Lookup skill provides GitHub Copilot with specialized knowledge. List, find, and show Azure resources across subscriptions or resource groups. Handles prompts like &quot;list websites&quot;, &quot;list virtual machines&quot;, &quot;list my VMs&quot;, &quot;show storage accounts&quot;, &quot;find container apps&quot;, and &quot;what resources do I have&quot;.

### Related tools

| Tool | Command | Purpose |
|------|---------|---------|
| `extension_cli_generate` | `Generate `az graph query` commands` | Primary tool &#8212; generate ARG queries from user intent |
| `mcp_azure_mcp_subscription_list` | `List available subscriptions` | Discover subscription scope before querying |
| `mcp_azure_mcp_group_list` | `List resource groups` | Narrow query scope |



## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "List the websites in my subscription"
- "Show me the websites in my resource group"
- "List all virtual machines in my subscription"
- "Show me all VMs in resource group 'my-rg'"
- "List my Azure storage accounts"
- "List all my Azure Container Registries"
- "List the container apps in my subscription"
- "Show me the container apps in my resource group"
- "What resources do I have across all my subscriptions?"
- "Show me all my Azure resources"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
