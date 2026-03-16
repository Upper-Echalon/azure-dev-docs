---
title: "Azure Skills reference: azure-rbac"
description: "Find the right Azure Role-Based Access Control (RBAC) role and assign it with least privilege. Manage permissions and access control."
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# azure-rbac

## Overview

**Description:** Find the right Azure Role-Based Access Control (RBAC) role and assign it with least privilege.

## What it does

- Identifies which Azure RBAC role matches your security requirements
- Generates CLI commands to assign roles
- Creates custom roles if needed
- Follows least-privilege principles
- Documents role assignments

## When to use

- Assigning permissions to users or service principals
- Implementing least-privilege access
- Reviewing role assignments
- Creating custom roles for specific needs
- Troubleshooting permission issues

## Example prompts

Ask your assistant:
- "What role should I assign to this user?"
- "Give least-privilege access for this service principal"
- "Create a custom role for [function]"
- "Why do I get a permission denied error?"

## Key MCP tools

- Azure RBAC role lookup and filtering
- Role assignment creation
- Custom role definition and creation
- Permission analysis

## Related

- [azure-compliance](azure-compliance.md) — Check compliance requirements
- [entra-app-registration](entra-app-registration.md) — Manage Entra ID app registrations
- [Azure Skills overview](../overview.md)
