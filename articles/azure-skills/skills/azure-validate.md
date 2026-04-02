---
title: Azure Validate
description: Pre-deployment validation for Azure readiness. Run deep checks on configuration, infrastructure (Bicep or Terraform), RBAC role assignments, managed identity permissions, and prerequisites before deploying.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Validate

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

Use the **Azure Validate** skill when you need to:

- Validate my app in Azure
- Check deployment readiness in Azure
- Run preflight checks in Azure
- Verify configuration in Azure
- Check if ready to deploy
- Validate azure.yaml
- Validate Bicep in Azure
- Test before deploying in Azure
- Troubleshoot deployment errors in Azure
- Validate Azure Functions
- Validate function app in Azure
- Validate serverless deployment in Azure
- Verify RBAC roles in Azure
- Check role assignments in Azure
- Review managed identity permissions
- Work with what-if analysis

## What it provides

The Azure Validate skill provides GitHub Copilot with specialized knowledge. Pre-deployment validation for Azure readiness. Run deep checks on configuration, infrastructure (Bicep or Terraform), RBAC role assignments, managed identity permissions, and prerequisites before deploying.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Check if my app is ready to deploy to Azure"
- "Validate my azure.yaml configuration"
- "Run preflight checks before Azure deployment"
- "Troubleshoot deployment errors"
- "Verify my infrastructure configuration before deploying"
- "Is my app ready for Azure deployment?"
- "Validate my Bicep configuration"
- "Validate my Bicep template before deploying to Azure"
- "Check my deployment permissions before running `azd` up"
- "Verify my Bicep files are valid before provisioning"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
