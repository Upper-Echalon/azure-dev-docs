---
title: Azure Quotas
description: Check/manage Azure quotas and usage across providers. For deployment planning, capacity validation, region selection.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Quotas

Check/manage Azure quotas and usage across providers. For deployment planning, capacity validation, region selection.

**Skill:** `azure-quotas` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-quotas)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

### Required resources

- **Azure Storage account**—Storage account for blob, file, queue, or table data
- **Azure Cosmos DB account**—Cosmos DB account for NoSQL data

## When to use this skill

Use the **Azure Quotas** skill when you need to:

- Check quotas in Azure
- Work with service limits and current usage
- Request quota increase in Azure
- Work with quota exceeded
- Validate capacity in Azure
- Work with regional availability
- Provisioning limits in Azure
- Work with vCPU limit
- How many vCPUs available in my subscription

## What it provides

The Azure Quotas skill provides GitHub Copilot with specialized knowledge. Check/manage Azure quotas and usage across providers. For deployment planning, capacity validation, region selection.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

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

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
