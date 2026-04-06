---
title: Azure skill for resource visualizer
description: Analyze Azure resource groups and generate detailed Mermaid architecture diagrams showing the relationships between individual resources.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for resource visualizer

Analyze Azure resource groups and generate detailed Mermaid architecture diagrams showing the relationships between individual resources.

**Skill:** `azure-resource-visualizer` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-resource-visualizer)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

### Required resources

- **Azure Key Vault**—Key vault for secrets and certificate management

## When to use this skill

Use this skill when you need to:

- Create architecture diagram in Azure
- Visualize Azure resources
- Work with generate Mermaid diagram
- Analyze resource group in Azure
- Work with diagram my resources, architecture visualization, resource topology, and map Azure infrastructure

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Analyze Azure resource groups and generate detailed Mermaid architecture diagrams showing the relationships between individual resources.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Create an architecture diagram for my Azure resource group"
- "Generate a Mermaid diagram of my resource group"
- "Visualize my Azure resources"
- "Visualize the architecture of my Azure resources"
- "Architecture visualization for my Azure infrastructure"
- "Show me the relationships between my Azure resources"
- "Show resource relationships"
- "How are my Azure resources connected?"
- "Analyze my resource group"
- "Analyze resource group architecture"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
