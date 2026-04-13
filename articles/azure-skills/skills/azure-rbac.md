---
title: Azure skill for role-based access control (RBAC)
description: Helps users find the right Azure RBAC role for an identity with least privilege access, then generate CLI commands and Bicep code to assign it. Also provides guidance on permissions required to grant roles.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for role-based access control (RBAC)

Helps users find the right Azure RBAC role for an identity with least privilege access, then generate CLI commands and Bicep code to assign it. Also provides guidance on permissions required to grant roles.

**Skill:** `azure-rbac` | [Source code](https://github.com/microsoft/azure-skills/blob/main/skills/azure-rbac/skill.md)

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Helps users find the right Azure RBAC role for an identity with least privilege access, then generate CLI commands and Bicep code to assign it. Also provides guidance on permissions required to grant roles.

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use this skill when you need to:

- Work with bicep for role assignment, least privilege role, RBAC role for, and role to read blobs
- Work with role for managed identity and custom role definition
- Assign role to identity
- Work with permissions to assign roles

## Example prompts

Try these prompts to activate this skill:

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

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [Skill source code](https://github.com/microsoft/azure-skills/blob/main/skills/azure-rbac/skill.md)
