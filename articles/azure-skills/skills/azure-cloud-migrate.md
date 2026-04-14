---
title: Azure skill for cloud migration
description: Assess and migrate cross-cloud workloads to Azure with migration reports and code conversion guidance. Supports AWS, GCP, and other providers.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for cloud migration

Assess and migrate cross-cloud workloads to Azure with migration reports and code conversion guidance. Supports AWS, GCP, and other providers.

**Skill:** `azure-cloud-migrate` | [Source code](https://github.com/microsoft/azure-skills/blob/main/skills/azure-cloud-migrate/skill.md)

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Assess and migrate cross-cloud workloads to Azure with migration reports and code conversion guidance. Supports AWS, GCP, and other providers.

## Prerequisites

- **Azure subscription**: [Create a free account](https://azure.microsoft.com/free/) if you don't have one.
- **GitHub Copilot**: With the Azure extension enabled.
- **Azure CLI** (v2.60.0+): [Install](/cli/azure/install-azure-cli) and sign in with `az login`.

## When to use this skill

Use this skill when you need to:

- Migrate AWS Lambda functions to Azure Functions.
- Plan and execute migrations of AWS infrastructure to Azure.
- Perform readiness assessments for Lambda function migrations.
- Convert AWS serverless architectures to Azure Compute services.
- Generate migration readiness reports.
- Execute migrations from AWS to Azure Cloud.
- Execute migrations from Google Cloud Platform to Azure.
- Plan migrations across multiple cloud providers to Azure.

## Example prompts

Try these prompts to activate this skill:

- "How do I migrate my AWS Lambda functions to Azure Functions?"
- "I want to migrate from AWS to Azure"
- "Can you do a Lambda migration assessment for my project?"
- "Convert my serverless functions to Azure"
- "Generate a migration readiness report for my Lambda functions"
- "Help me migrate code to Azure Functions"
- "Assess my AWS Lambda project for Azure migration"
- "I need to move my Lambda workloads to Azure Functions"

## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [Skill source code](https://github.com/microsoft/azure-skills/blob/main/skills/azure-cloud-migrate/skill.md)
