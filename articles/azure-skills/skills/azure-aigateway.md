---
title: Azure skill for AI Gateway
description: Configure Azure API Management as an AI Gateway for AI models, MCP tools, and agents.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for AI Gateway

Configure Azure API Management as an AI Gateway for AI models, Model Context Protocol (MCP) tools, and agents.

**Skill:** `azure-aigateway` | [Source code](https://github.com/microsoft/azure-skills/tree/main/skills/azure-aigateway)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use this skill when you need to:

- Work with semantic caching, token limit, content safety, and load balancing
- Work with AI model governance, MCP rate limiting, and jailbreak detection
- Add Azure OpenAI back end
- Add AI Foundry model
- Test AI gateway in Azure
- Work with LLM policies
- Configure AI back end in Azure
- Work with token metrics, AI cost control, convert API to MCP, and import OpenAPI to gateway

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Configure Azure API Management as an AI Gateway for AI models, MCP tools, and agents.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Set up an AI Gateway for my Azure OpenAI models"
- "Configure Azure API Management as a gateway for my AI models"
- "Add a gateway to my MCP server"
- "Set up APIM for my AI workloads"
- "Add rate limiting to my model requests"
- "Limit tokens for my AI API"
- "How do I ratelimit my MCP server?"
- "Enable semantic caching for my AI API"
- "Set up semantic cache for Azure OpenAI in APIM"
- "Add content safety to my AI endpoint"


## Related content

- [Azure MCP Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
