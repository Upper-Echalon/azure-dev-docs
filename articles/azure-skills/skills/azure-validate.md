---
title: "Azure Skills reference: azure-validate"
description: "Validate your deployment plan before deploying to Azure. Runs configuration checks, syntax validation, and permission verification."
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# azure-validate

## Overview

**Description:** Validate your deployment plan before deploying to Azure.

## What it does

- Loads your plan from `.azure/plan.md`
- Runs configuration checks and syntax validation
- Verifies Azure permissions and regional availability
- Records validation proof
- Updates plan status to `Validated` (required before deployment)

## When to use

- After reviewing and approving the prepare plan
- Before deploying to ensure no issues
- After significant changes to your application

## Example prompts

Ask your assistant:
- "Validate this deployment plan"
- "Check if my app is ready to deploy"
- "Run preflight checks before deployment"

## Prerequisites

- Plan must have status `Approved` (from azure-prepare)

## Output

- `.azure/plan.md` updated with status: `Validated`
- Validation proof section populated
- Command output and results

## Related

- [azure-prepare](azure-prepare.md) — Create a deployment plan
- [azure-deploy](azure-deploy.md) — Execute the deployment
- [Get started with Azure Skills](../quickstart.md)
