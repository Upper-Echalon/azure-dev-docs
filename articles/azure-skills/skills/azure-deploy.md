---
title: azure-deploy
description: Execute Azure deployments for ALREADY-PREPARED applications that have existing . azure/deployment-plan.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-deploy

Execute Azure deployments for ALREADY-PREPARED applications that have existing . azure/deployment-plan.

**Skill:** `azure-deploy` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-deploy)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-deploy`** skill when you need to:

- run azd up
- run azd deploy
- execute deployment
- push to production
- push to cloud
- go live
- ship it
- bicep deploy
- terraform apply
- publish to Azure
- launch on Azure

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-deploy` skill provides GitHub Copilot with specialized knowledge. Execute Azure deployments for ALREADY-PREPARED applications that have existing . azure/deployment-plan.





## Example prompts

Try these prompts with GitHub Copilot:

- "Execute deployment to Azure production"
- "Deploy and provision my Azure infrastructure"
- "Push my deploy to Azure production"
- "Ship and deploy my Azure app"
- "Run the Azure deployment now"
- "Deploy my Azure Functions app to the cloud using azd"
- "Deploy my serverless function app to Azure"
- "Deploy Azure Functions to production"
- "Deploy my app and verify the role-based access control (RBAC) roles are assigned correctly"
- "Run deployment and check live role assignments on Azure"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
