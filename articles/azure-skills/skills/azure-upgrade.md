---
title: azure-upgrade
description: Assess and upgrade Azure workloads between plans, tiers, or SKUs within Azure. Generates assessment reports and automates upgrade steps.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-upgrade

Assess and upgrade Azure workloads between plans, tiers, or SKUs within Azure. Generates assessment reports and automates upgrade steps.

**Skill:** `azure-upgrade` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-upgrade)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-upgrade`** skill when you need to:

- upgrade Consumption to Flex Consumption
- upgrade Azure Functions plan
- migrate hosting plan
- upgrade Functions Sku
- move to Flex Consumption
- upgrade Azure service tier
- change hosting plan
- upgrade function app plan
- migrate App Service to Container Apps

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-upgrade` skill provides GitHub Copilot with specialized knowledge. Assess and upgrade Azure workloads between plans, tiers, or SKUs within Azure. Generates assessment reports and automates upgrade steps.





## Example prompts

Try these prompts with GitHub Copilot:

- "Upgrade my function app from Consumption to Flex Consumption"
- "Move my function app to a better plan"
- "Is my function app ready for Flex Consumption?"
- "Automate the steps to upgrade my Functions plan"
- "Upgrade my Azure Functions SKU"
- "Change my function app hosting plan"
- "Migrate my Azure Functions from Consumption to Flex Consumption"
- "Assess my function app for upgrade readiness"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
