---
title: azure-aigateway
description: Configure Azure API Management as an AI Gateway for AI models, MCP tools, and agents.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-aigateway

Configure Azure API Management as an AI Gateway for AI models, Model Context Protocol (MCP) tools, and agents.

**Skill:** `azure-aigateway` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-aigateway)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-aigateway`** skill when you need to:

- semantic caching
- token limit
- content safety
- load balancing
- AI model governance
- MCP rate limiting
- jailbreak detection
- add Azure OpenAI backend
- add AI Foundry model
- test AI gateway
- Llm policies
- configure AI backend
- token metrics
- AI cost control
- convert API to MCP
- import OpenAPI to gateway

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-aigateway` skill provides GitHub Copilot with specialized knowledge. Configure Azure API Management as an AI Gateway for AI models, MCP tools, and agents.





## Example prompts

Try these prompts with GitHub Copilot:

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

- [Azure MCP Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
