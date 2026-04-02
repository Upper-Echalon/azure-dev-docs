---
title: azure-diagnostics
description: Debug Azure production issues on Azure using AppLens, Azure Monitor, resource health, and safe triage.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-diagnostics

Debug Azure production issues on Azure using AppLens, Azure Monitor, resource health, and safe triage.

**Skill:** `azure-diagnostics` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-diagnostics)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-diagnostics`** skill when you need to:

- debug production issues
- troubleshoot container apps
- troubleshoot functions
- troubleshoot Azure Kubernetes Service (AKS)
- kubectl can't connect
- kube-system/CoreDNS failures
- pod pending
- crashloop
- node not ready
- upgrade failures
- analyze logs
- insights
- image pull failures
- cold start issues
- health probe failures
- resource health
- root cause of errors

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-diagnostics` skill provides GitHub Copilot with specialized knowledge. Debug Azure production issues on Azure using AppLens, Azure Monitor, resource health, and safe triage.





## Example prompts

Try these prompts with GitHub Copilot:

- "Debug my Azure Container App"
- "Troubleshoot production issues in my container app"
- "Diagnose errors in my Azure service"
- "Help me troubleshoot container apps on Azure"
- "Analyze logs with KQL for my app"
- "How do I analyze application logs?"
- "View application logs for my container"
- "Fix image pull failures in Container Apps"
- "My container app has image pull errors"
- "Resolve cold start issues"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
