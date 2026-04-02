---
title: Entra App Registration
description: Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Entra App Registration

Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.

**Skill:** `entra-app-registration` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/entra-app-registration)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI with Bicep** (v2.60.0+) — Install: `az bicep install`

### Required resources

- **Azure Key Vault** — Key vault for secrets and certificate management

## When to use this skill

Use the **Entra App Registration** skill when you need to:

- Create app registration in Azure
- Work with register Microsoft Entra ID app
- Configure OAuth in Azure
- Set up authentication in Azure
- Add API permissions in Azure
- Work with generate service principal, MSAL example, console app auth, and Entra ID setup
- Work with Microsoft Entra ID authentication

## What it provides

The Entra App Registration skill provides GitHub Copilot with specialized knowledge. Guides Microsoft Entra ID app registration, OAuth 2.0 authentication, and MSAL integration.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

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
