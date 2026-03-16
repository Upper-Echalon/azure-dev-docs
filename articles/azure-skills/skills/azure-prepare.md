---
title: "Azure Skills reference: azure-prepare"
description: "Plan your Azure deployment without making changes. Analyzes your application and generates deployment strategy and infrastructure-as-code."
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# azure-prepare

## Overview

**Description:** Plan your Azure deployment without making changes.

## What it does

- Analyzes your application and codebase
- Identifies required Azure services
- Creates `.azure/plan.md` with deployment strategy
- Generates infrastructure-as-code (Bicep, Terraform, or Azure CLI)
- Waits for your approval before proceeding

## When to use

- Starting any Azure deployment work
- Adding new components to an existing app
- Modernizing or migrating applications to Azure
- Preparing infrastructure for a new service

## Example prompts

Ask your assistant:
- "Prepare my app for Azure deployment"
- "Create a deployment plan for my web app"
- "Modernize my legacy app to Azure"

## Output

- `.azure/plan.md` (deployment plan)
- Infrastructure-as-code files
- Status: `Approved`

## Related

- [azure-validate](azure-validate.md) — Validate your deployment plan
- [azure-deploy](azure-deploy.md) — Execute the deployment
- [Get started with Azure Skills](../quickstart.md)
