---
title: azure-validate
description: Pre-deployment validation for Azure readiness. Run deep checks on configuration, infrastructure (Bicep or Terraform), RBAC role assignments, managed identity permissions, and prerequisites before deploying.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-validate

Pre-deployment validation for Azure readiness. Run deep checks on configuration, infrastructure (Bicep or Terraform), role-based access control (RBAC) role assignments, managed identity permissions, and prerequisites before deploying.

**Skill:** `azure-validate` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-validate)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-validate`** skill when you need to:

- validate my app
- check deployment readiness
- run preflight checks
- verify configuration
- check if ready to deploy
- validate azure.yaml
- validate Bicep
- test before deploying
- troubleshoot deployment errors
- validate Azure Functions
- validate function app
- validate serverless deployment
- verify RBAC roles
- check role assignments
- review managed identity permissions
- what-if analysis

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-validate` skill provides GitHub Copilot with specialized knowledge. Pre-deployment validation for Azure readiness. Run deep checks on configuration, infrastructure (Bicep or Terraform), RBAC role assignments, managed identity permissions, and prerequisites before deploying.





## Example prompts

Try these prompts with GitHub Copilot:

- "Check if my app is ready to deploy to Azure"
- "Validate my azure.yaml configuration"
- "Run preflight checks before Azure deployment"
- "Troubleshoot deployment errors"
- "Verify my infrastructure configuration before deploying"
- "Is my app ready for Azure deployment?"
- "Validate my Bicep configuration"
- "Validate my Bicep template before deploying to Azure"
- "Check my deployment permissions before running azd up"
- "Verify my Bicep files are valid before provisioning"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
