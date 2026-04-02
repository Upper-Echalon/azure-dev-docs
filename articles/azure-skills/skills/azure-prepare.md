---
title: azure-prepare
description: Prepare Azure apps for deployment (infra Bicep/Terraform, azure.yaml, Dockerfiles).
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-prepare

Prepare Azure apps for deployment (infra Bicep/Terraform, azure.yaml, Dockerfiles).

**Skill:** `azure-prepare` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-prepare)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-prepare`** skill when you need to:

- create app
- build web app
- create API
- create serverless Http API
- create frontend
- create back end
- build a service
- modernize application
- update application
- add authentication
- add caching
- host on Azure
- create and deploy
- deploy to Azure
- deploy to Azure using Terraform
- deploy to Azure App Service
- deploy to Azure App Service using Terraform
- deploy to Azure Container Apps
- deploy to Azure Container Apps using Terraform
- generate Terraform
- generate Bicep
- function app
- timer trigger
- service bus trigger
- event-driven function
- containerized Node.js app
- social media app
- static portfolio website
- todo list with frontend and API
- prepare my Azure application to use Key Vault
- managed identity

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-prepare` skill provides GitHub Copilot with specialized knowledge. Prepare Azure apps for deployment (infra Bicep/Terraform, azure.yaml, Dockerfiles).





## Example prompts

Try these prompts with GitHub Copilot:

- "Create a dad joke generator and deploy to Azure"
- "Build a web app and host it on Azure"
- "I want to deploy my application to Azure"
- "Set up Azure infrastructure for my project"
- "Prepare my app for Azure deployment"
- "Create an API and run it on Azure"
- "Migrate my application to Azure"
- "Configure Azure hosting for my app"
- "Create a serverless HTTP API using Azure Functions and deploy to Azure"
- "Create an event-driven function app to process messages and deploy to Azure Functions"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
