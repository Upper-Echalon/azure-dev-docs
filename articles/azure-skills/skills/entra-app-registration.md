---
title: Entra App Registration
description: Guides Microsoft Entra Id app registration, OAuth 2.0 authentication, and Msal integration.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Entra App Registration

Guides Microsoft Entra Id app registration, OAuth 2.0 authentication, and Msal integration.

**Skill:** `entra-app-registration` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/entra-app-registration)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **Entra App Registration** skill when you need to:

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

The Entra App Registration skill provides GitHub Copilot with specialized knowledge. Guides Microsoft Entra Id app registration, OAuth 2.0 authentication, and Msal integration.




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

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
