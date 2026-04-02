---
title: azure-resource-lookup
description: List, find, and show Azure resources across subscriptions or resource groups. Handles prompts like &quot;list websites&quot;, &quot;list virtual machines&quot;, &quot;list my VMs&quot;, &quot;show storage accounts&quot;, &quot;find container apps&quot;, and &quot;what resources do I have&quot;.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-resource-lookup

List, find, and show Azure resources across subscriptions or resource groups. Handles prompts like &quot;list websites&quot;, &quot;list virtual machines&quot;, &quot;list my VMs&quot;, &quot;show storage accounts&quot;, &quot;find container apps&quot;, and &quot;what resources do I have&quot;.

**Skill:** `azure-resource-lookup` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-resource-lookup)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-resource-lookup`** skill when you need to:

- Work with resource inventory
- Find resources by tag
- Work with tag analysis
- Orphaned resource discovery (not for cost analysis)
- Work with unattached disks, count resources by type, and cross-subscription lookup
- And Azure Resource Graph queries

### When NOT to use this skill

Don't use this skill for:

- Work with deploying/changing resources (use `azure-deploy`), cost optimization (use `azure-cost`), and or non-Azure clouds

## What it provides

The `azure-resource-lookup` skill provides GitHub Copilot with specialized knowledge. List, find, and show Azure resources across subscriptions or resource groups. Handles prompts like &quot;list websites&quot;, &quot;list virtual machines&quot;, &quot;list my VMs&quot;, &quot;show storage accounts&quot;, &quot;find container apps&quot;, and &quot;what resources do I have&quot;.

### Related tools

| Tool | Command | Purpose |
|------|---------|---------|
| `extension_cli_generate` | `Generate `az graph query` commands` | Primary tool &#8212; generate ARG queries from user intent |
| `mcp_azure_mcp_subscription_list` | `List available subscriptions` | Discover subscription scope before querying |
| `mcp_azure_mcp_group_list` | `List resource groups` | Narrow query scope |





## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
