---
title: Azure skill for diagnostics
description: Debug Azure production issues on Azure using AppLens, Azure Monitor, resource health, and safe triage.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for diagnostics

Debug Azure production issues on Azure using AppLens, Azure Monitor, resource health, and safe triage.

**Skill:** `azure-diagnostics` | [Source code](https://github.com/microsoft/azure-skills/tree/main/skills/azure-diagnostics)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`
- **Azure Kubernetes Service cluster**—Azure Kubernetes Service (AKS) cluster for container orchestration

## When to use this skill

Use this skill when you need to:

- Debug production issues in Azure
- Troubleshoot container apps in Azure
- Troubleshoot functions in Azure
- Troubleshoot AKS in Azure
- Work with kubectl can't connect, kube-system/CoreDNS failures, pod pending, and crashloop
- Work with node not ready
- Upgrade failures in Azure
- Analyze logs in Azure
- Work with insights, image pull failures, cold start issues, and health probe failures
- Work with resource health and root cause of errors

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Debug Azure production issues on Azure using AppLens, Azure Monitor, resource health, and safe triage.

## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

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

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
