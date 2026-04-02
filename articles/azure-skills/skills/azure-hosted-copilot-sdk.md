---
title: Azure Hosted Copilot SDK
description: Build and deploy GitHub Copilot SDK apps to Azure.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Hosted Copilot SDK

Build and deploy GitHub Copilot SDK apps to Azure.

**Skill:** `azure-hosted-copilot-sdk` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-hosted-copilot-sdk)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **Azure Hosted Copilot SDK** skill when you need to:

- Build copilot app
- Create copilot app
- Work with copilot SDK, @github/copilot-sdk, scaffold copilot project, and copilot-powered app
- Deploy copilot app
- Work with host on azure, azure model, Byom, and bring your own model
- Use my own model
- Work with azure openai model, DefaultAzureCredential, self-hosted model, and copilot SDK service
- Work with chat app with copilot, copilot-sdk-service template, azd init copilot, and CopilotClient
- Work with createSession, sendAndWait, and GitHub Models API

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Work with Explain quantum computing

## What it provides

The Azure Hosted Copilot SDK skill provides GitHub Copilot with specialized knowledge. Build and deploy GitHub Copilot SDK apps to Azure.




## Example prompts

Try these prompts with GitHub Copilot:

- "Build a Copilot SDK app and deploy it"
- "Create a new copilot SDK service"
- "Scaffold a copilot-powered app on Azure"
- "Build with the GitHub Copilot SDK and host it"
- "Build a Copilot SDK app with my own Azure model"
- "Create a copilot app using my Azure OpenAI model"
- "Set up a copilot service with BYOM and DefaultAzureCredential"
- "Build a copilot app that uses a self-hosted model on Azure"
- "Deploy a copilot SDK app with my own endpoint"
- "Create a copilot app and bring your own model from Azure OpenAI"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
