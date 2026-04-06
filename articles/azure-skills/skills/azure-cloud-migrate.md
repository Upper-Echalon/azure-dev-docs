---
title: Azure skill for cloud migration
description: Assess and migrate cross-cloud workloads to Azure with migration reports and code conversion guidance. Supports AWS, GCP, and other providers.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for cloud migration

Assess and migrate cross-cloud workloads to Azure with migration reports and code conversion guidance. Supports AWS, GCP, and other providers.

**Skill:** `azure-cloud-migrate` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-cloud-migrate)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use this skill when you need to:

- Migrate Lambda to Azure Functions
- Migrate AWS to Azure
- Work with Lambda migration assessment
- Convert AWS serverless to Azure
- Work with migration readiness report
- Migrate from AWS in Azure
- Migrate from GCP in Azure
- Work with cross-cloud migration

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Assess and migrate cross-cloud workloads to Azure with migration reports and code conversion guidance. Supports AWS, GCP, and other providers.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "How do I migrate my AWS Lambda functions to Azure Functions?"
- "I want to migrate from AWS to Azure"
- "Can you do a Lambda migration assessment for my project?"
- "Convert my serverless functions to Azure"
- "Generate a migration readiness report for my Lambda functions"
- "Help me migrate code to Azure Functions"
- "Assess my AWS Lambda project for Azure migration"
- "I need to move my Lambda workloads to Azure Functions"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
