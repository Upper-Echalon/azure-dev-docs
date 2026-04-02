---
title: entra-app-registration
description: Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# entra-app-registration

Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.

**Skill:** `entra-app-registration` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/entra-app-registration)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **entra-app-registration** skill when you need to:

- Create app registration
- Work with register Microsoft Entra ID app
- Configure OAuth
- Set up authentication
- Add API permissions
- Work with generate service principal, Msal example, console app auth, and Entra ID setup
- Work with Microsoft Entra ID authentication

### When NOT to use this skill

Don't use this skill for:

- Azure role-based access control (RBAC) or role assignments (use `azure-rbac`)
- Key Vault secrets (use `azure-keyvault-expiration-audit`)
- General Azure resource security guidance

## What it provides

The entra-app-registration skill provides GitHub Copilot with specialized knowledge. Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.






## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
