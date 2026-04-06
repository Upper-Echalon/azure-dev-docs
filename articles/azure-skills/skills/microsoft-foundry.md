---
title: Azure skill for Microsoft Foundry
description: Deploy, evaluate, and manage Foundry agents end-to-end: Docker build, acr push, hosted/prompt agent create, container start, batch eval, prompt optimization, prompt optimizer workflows, agent.yaml, dataset curation from traces.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for Microsoft Foundry

Deploy, evaluate, and manage Foundry agents end-to-end: Docker build, acr push, hosted/prompt agent create, container start, batch eval, prompt optimization, prompt optimizer workflows, agent.yaml, dataset curation from traces.

**Skill:** `microsoft-foundry` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/microsoft-foundry)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **PowerShell** (v7.4+)—Install: `winget install Microsoft.PowerShell`
- **Bash**

## When to use this skill

Use this skill when you need to:

- Deploy agent to Foundry
- Work with hosted agent
- Create agent in Azure
- Work with invoke agent
- Evaluate agent in Azure
- Run batch eval in Azure
- Optimize prompt in Azure
- Work with improve prompt, prompt optimization, prompt optimizer, and improve agent instructions
- Optimize agent instructions in Azure
- Optimize system prompt in Azure

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Deploy, evaluate, and manage Foundry agents end-to-end: Docker build, acr push, hosted/prompt agent create, container start, batch eval, prompt optimization, prompt optimizer workflows, agent.yaml, dataset curation from traces.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "How do I deploy an AI model from Microsoft Foundry catalog?"
- "Build a RAG application with Azure AI Foundry knowledge index"
- "Create an AI agent in Microsoft Foundry with web search"
- "Evaluate agent performance using Foundry evaluators"
- "Optimize my prompt for a Microsoft Foundry agent"
- "Improve my agent instructions in Azure AI Foundry"
- "Use a prompt optimizer on my Foundry system prompt"
- "Set up agent monitoring and continuous evaluation in Foundry"
- "Help me with Microsoft Foundry model deployment"
- "How to use knowledge index for RAG in Azure AI Foundry?"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
