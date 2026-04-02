---
title: microsoft-foundry
description: Deploy, evaluate, and manage Foundry agents end-to-end: Docker build, ACR push, hosted/prompt agent create, container start, batch eval, prompt optimization, prompt optimizer workflows, agent.yaml, dataset curation from traces.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# microsoft-foundry

Deploy, evaluate, and manage Foundry agents end-to-end: Docker build, Azure Container Registry (ACR) push, hosted/prompt agent create, container start, batch eval, prompt optimization, prompt optimizer workflows, agent.yaml, dataset curation from traces.

**Skill:** `microsoft-foundry` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/microsoft-foundry)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **microsoft-foundry** skill when you need to:

- Deploy agent to Foundry
- Work with hosted agent
- Create agent
- Work with invoke agent
- Evaluate agent
- Run batch eval
- Optimize prompt
- Work with improve prompt, prompt optimization, prompt optimizer, and improve agent instructions
- Optimize agent instructions
- Optimize system prompt
- Deploy model
- Work with Foundry project, role-based access control (RBAC), role assignment, and permissions
- Work with quota, capacity, and region
- Troubleshoot agent
- Work with deployment failure
- Create dataset from traces
- Work with dataset versioning and eval trending
- Create AI Services
- Work with Cognitive Services
- Create Foundry resource
- Provision resource
- Work with knowledge index, agent monitoring, customize deployment, and onboard
- Work with availability

### When NOT to use this skill

Don't use this skill for:

- Work with Azure Functions and App Service
- General Azure deploy (use `azure-deploy`)
- General Azure prep (use `azure-prepare`)

## What it provides

The microsoft-foundry skill provides GitHub Copilot with specialized knowledge. Deploy, evaluate, and manage Foundry agents end-to-end: Docker build, ACR push, hosted/prompt agent create, container start, batch eval, prompt optimization, prompt optimizer workflows, agent.yaml, dataset curation from traces.






## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
