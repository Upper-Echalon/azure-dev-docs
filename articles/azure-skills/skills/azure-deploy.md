---
title: Azure Deploy
description: Execute Azure deployments for already-prepared applications that have existing .azure/deployment-plan.md and infrastructure files.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Deploy

Execute Azure deployments for already-prepared applications that have existing .azure/deployment-plan.md and infrastructure files.

**Skill:** `azure-deploy` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-deploy)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **Azure Deploy** skill when you need to:

- Run `azd` up in Azure
- Run `azd` deploy in Azure
- Execute deployment in Azure
- Work with push to production, push to cloud, go live, and ship it
- Work with bicep deploy, terraform apply, publish to Azure, and launch on Azure

## What it provides

The Azure Deploy skill provides GitHub Copilot with specialized knowledge. Execute Azure deployments for already-prepared applications that have existing .azure/deployment-plan.md and infrastructure files.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Execute deployment to Azure production"
- "Deploy and provision my Azure infrastructure"
- "Push my deploy to Azure production"
- "Ship and deploy my Azure app"
- "Run the Azure deployment now"
- "Deploy my Azure Functions app to the cloud using `azd`"
- "Deploy my serverless function app to Azure"
- "Deploy Azure Functions to production"
- "Deploy my app and verify the role-based access control (RBAC) roles are assigned correctly"
- "Run deployment and check live role assignments on Azure"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
