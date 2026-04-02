---
title: entra-app-registration
description: Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.
ms.topic: reference
ms.date: 2026-04-02
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

- create app registration
- register Microsoft Entra ID app
- configure OAuth
- set up authentication
- add API permissions
- generate service principal
- Msal example
- console app auth
- Entra ID setup
- Microsoft Entra ID authentication

### When NOT to use this skill

Don't use this skill for:

- Azure role-based access control (RBAC) or role assignments (use `azure-rbac`)
- Key Vault secrets (use `azure-keyvault-expiration-audit`)
- general Azure resource security guidance

## What it provides

The entra-app-registration skill provides GitHub Copilot with specialized knowledge. Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.





## Example prompts

Try these prompts with GitHub Copilot:

- "How do I create an app registration in Azure?"
- "Register an Microsoft Entra ID app for my web application"
- "Configure OAuth authentication for my application"
- "Set up authentication with Microsoft Entra ID"
- "Add API permissions to my Entra app registration"
- "Generate a service principal for Azure authentication"
- "Show me an MSAL example for Entra authentication"
- "Create a console app with Microsoft Entra ID authentication"
- "Help me set up Entra ID authentication for my app"
- "Configure Microsoft Entra ID OAuth authentication for my API"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
