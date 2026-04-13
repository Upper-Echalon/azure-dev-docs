---
title: Azure skill for prepare
description: Prepare Azure apps for deployment (infra Bicep/Terraform, azure.yaml, Dockerfiles).
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for prepare

Prepare Azure apps for deployment (infra Bicep/Terraform, azure.yaml, Dockerfiles).

**Skill:** `azure-prepare` | [Source code](https://github.com/microsoft/azure-skills/tree/main/skills/azure-prepare)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **Azure CLI with Bicep** (v2.60.0+)—Install: `az bicep install`
- **Terraform** (v1.5+)—Install: `https://developer.hashicorp.com/terraform/install`

## When to use this skill

Use this skill when you need to:

- Create app in Azure
- Build web app in Azure
- Create API in Azure
- Create serverless HTTP API
- Create front end in Azure
- Create back end in Azure
- Build a service in Azure
- Work with modernize application
- Update application in Azure
- Add authentication in Azure

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Prepare Azure apps for deployment (infra Bicep/Terraform, azure.yaml, Dockerfiles).

## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

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

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
