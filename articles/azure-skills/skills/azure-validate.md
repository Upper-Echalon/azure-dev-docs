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

- Validate my app
- Check deployment readiness
- Run preflight checks
- Verify configuration
- Check if ready to deploy
- Validate azure.yaml
- Validate Bicep
- Test before deploying
- Troubleshoot deployment errors
- Validate Azure Functions
- Validate function app
- Validate serverless deployment
- Verify RBAC roles
- Check role assignments
- Review managed identity permissions
- Work with what-if analysis


## What it provides

The `azure-validate` skill provides GitHub Copilot with specialized knowledge. Pre-deployment validation for Azure readiness. Run deep checks on configuration, infrastructure (Bicep or Terraform), RBAC role assignments, managed identity permissions, and prerequisites before deploying.






## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
