---
title: "Azure Skills reference: azure-deploy"
description: "Execute deployment of your application to Azure. Provisions resources, deploys code, and configures application settings."
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# azure-deploy

## Overview

**Description:** Execute deployment of your application to Azure.

## What it does

- Verifies plan has status `Validated`
- Provisions Azure resources (storage, compute, services)
- Deploys application code
- Configures application settings and connections
- Provides access endpoints and credentials

## When to use

- Plan is approved and validated
- Deploying to production
- Redeploying after application updates
- Deploying to a different environment

## Example prompts

Ask your assistant:
- "Deploy my app to Azure"
- "Run the deployment"
- "Push my app to production"

## Prerequisites

- `.azure/plan.md` exists
- Plan status: `Validated` (only azure-validate can set this)

## Output

- Deployed Azure resources
- Application URLs
- Storage credentials and connection strings
- Monitoring access (Application Insights)

## Related

- [azure-prepare](azure-prepare.md) — Create a deployment plan
- [azure-validate](azure-validate.md) — Validate the deployment plan
- [Get started with Azure Skills](../quickstart.md)
