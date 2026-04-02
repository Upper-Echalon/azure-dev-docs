---
title: azure-quotas
description: Check/manage Azure quotas and usage across providers. For deployment planning, capacity validation, region selection.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-quotas

Check/manage Azure quotas and usage across providers. For deployment planning, capacity validation, region selection.

**Skill:** `azure-quotas` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-quotas)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-quotas`** skill when you need to:

- check quotas
- service limits
- current usage
- request quota increase
- quota exceeded
- validate capacity
- regional availability
- provisioning limits
- vCPU limit
- how many vCPUs available in my subscription

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-quotas` skill provides GitHub Copilot with specialized knowledge. Check/manage Azure quotas and usage across providers. For deployment planning, capacity validation, region selection.





## Example prompts

Try these prompts with GitHub Copilot:

- "How do I check my Azure quota limits?"
- "What are the service limits for my Azure subscription?"
- "Check current usage for my compute quota"
- "I need to request a quota increase for VMs in East US"
- "My deployment failed with a quota exceeded error"
- "How do I validate deployment capacity before provisioning?"
- "Help me select a region based on quota availability"
- "Compare quotas across regions for Standard_D4s_v3"
- "What is the provisioning limit for public IP addresses?"
- "Check regional capacity for Container Apps"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
