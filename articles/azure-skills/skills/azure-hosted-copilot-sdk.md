---
title: Azure skill for Hosted Copilot SDK
description: Build and deploy GitHub Copilot SDK apps to Azure.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for Hosted Copilot SDK

Build and deploy GitHub Copilot SDK apps to Azure.

**Skill:** `azure-hosted-copilot-sdk` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-hosted-copilot-sdk)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use this skill when you need to:

- Build custom copilot applications on Azure infrastructure.
- Create and configure copilot applications.
- Use the GitHub Copilot SDK to scaffold and build copilot-powered applications.
- Deploy your copilot application to Azure infrastructure.
- Host applications on Azure using Azure OpenAI models or bring your own model (BYOM).
- Integrate your own large language model (LLM) with the Copilot SDK.
- Configure Azure OpenAI models, managed identity authentication, and the Copilot SDK service.
- Build chat applications using the Copilot SDK service template and the `CopilotClient` library.
- Implement session management and message handling using the GitHub Models API.

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Build and deploy GitHub Copilot SDK apps to Azure.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Build a Copilot SDK app and deploy it"
- "Create a new copilot SDK service"
- "Scaffold a copilot-powered app on Azure"
- "Build with the GitHub Copilot SDK and host it"
- "Build a Copilot SDK app with my own Azure model"
- "Create a copilot app using my Azure OpenAI model"
- "Set up a copilot service with `BYOM` and `DefaultAzureCredential`"
- "Build a copilot app that uses a self-hosted model on Azure"
- "Deploy a copilot SDK app with my own endpoint"
- "Create a copilot app and bring your own model from Azure OpenAI"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
