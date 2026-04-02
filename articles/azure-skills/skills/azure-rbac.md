---
title: azure-rbac
description: Helps users find the right Azure RBAC role for an identity with least privilege access, then generate CLI commands and Bicep code to assign it. Also provides guidance on permissions required to grant roles.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-rbac

Helps users find the right Azure role-based access control (RBAC) role for an identity with least privilege access, then generate CLI commands and Bicep code to assign it. Also provides guidance on permissions required to grant roles.

**Skill:** `azure-rbac` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-rbac)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-rbac`** skill when you need to:

- bicep for role assignment
- what role should I assign
- least privilege role
- RBAC role for
- role to read blobs
- role for managed identity
- custom role definition
- assign role to identity
- what role do I need to grant access
- permissions to assign roles

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-rbac` skill provides GitHub Copilot with specialized knowledge. Helps users find the right Azure RBAC role for an identity with least privilege access, then generate CLI commands and Bicep code to assign it. Also provides guidance on permissions required to grant roles.





## Example prompts

Try these prompts with GitHub Copilot:

- "What Azure RBAC role should I assign to my managed identity?"
- "Which Azure role gives least privilege access to read blobs from storage?"
- "What role do I need for my identity to access Azure Key Vault secrets?"
- "Help me find the right Azure role for container registry access"
- "I need a custom role definition for my Azure storage account"
- "What Azure role should I use to give my function app access to Service Bus?"
- "Assign an Azure RBAC role to my identity for Cosmos DB read access"
- "What is the least privilege role for reading from a storage queue?"
- "I need to assign a role to my app service managed identity for database access"
- "Generate Bicep code for assigning a role to my function app"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
