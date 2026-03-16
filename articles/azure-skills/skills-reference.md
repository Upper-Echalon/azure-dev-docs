---
title: Azure Skills reference
description: Reference guide for all 18 Azure Skills organized by category. Each skill page includes descriptions, use cases, and example prompts.
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# Azure Skills reference

Azure Skills help you manage Azure resources, deploy applications, and monitor services. Choose a skill below to learn more about what it does and when to use it.

## Development lifecycle skills

Use these core skills to manage the prepare-validate-deploy workflow. Use them in order for safe, auditable deployments.

| Skill | Description |
|-------|-------------|
| [azure-prepare](skills/azure-prepare.md) | Plan your Azure deployment without making changes. |
| [azure-validate](skills/azure-validate.md) | Validate your deployment plan before deploying to Azure. |
| [azure-deploy](skills/azure-deploy.md) | Execute deployment of your application to Azure. |

## AI & Machine Learning skills

Use these skills to integrate AI services into your application.

| Skill | Description |
|-------|-------------|
| [azure-ai](skills/azure-ai.md) | Work with Azure AI services: AI Search, Speech, OpenAI, Document Intelligence. |
| [azure-aigateway](skills/azure-aigateway.md) | Manage Azure AI Gateway for unified API access to multiple AI services. |
| [microsoft-foundry](skills/microsoft-foundry.md) | Deploy AI models, build RAG applications, create and evaluate AI agents. |

## Data & Analytics skills

Use these skills for data processing, storage, and analysis.

| Skill | Description |
|-------|-------------|
| [azure-postgres](skills/azure-postgres.md) | Manage Azure Database for PostgreSQL: provisioning, queries, backups, and performance tuning. |
| [azure-kusto](skills/azure-kusto.md) | Query Azure Data Explorer (Kusto): large-scale data analytics and time-series analysis. |
| [azure-storage](skills/azure-storage.md) | Work with Azure Storage services: Blob Storage, File Shares, Queue Storage, Table Storage. |

## Security & Identity skills

Use these skills to implement access control and manage identity.

| Skill | Description |
|-------|-------------|
| [azure-rbac](skills/azure-rbac.md) | Find the right Azure Role-Based Access Control (RBAC) role and assign it with least privilege. |
| [azure-compliance](skills/azure-compliance.md) | Check compliance requirements and validate Azure configurations against compliance standards. |
| [entra-app-registration](skills/entra-app-registration.md) | Manage Microsoft Entra ID (formerly Azure AD) app registrations for secure authentication. |

## Infrastructure & Monitoring skills

Use these skills to manage resources, troubleshoot issues, and optimize costs.

| Skill | Description |
|-------|-------------|
| [azure-resource-lookup](skills/azure-resource-lookup.md) | Find and inspect Azure resources across your subscription. |
| [azure-resource-visualizer](skills/azure-resource-visualizer.md) | Visualize your Azure resource architecture and dependencies. |
| [azure-diagnostics](skills/azure-diagnostics.md) | Debug and troubleshoot production issues on Azure resources. |
| [azure-observability](skills/azure-observability.md) | Set up monitoring, logging, and alerting for your Azure resources. |
| [appinsights-instrumentation](skills/appinsights-instrumentation.md) | Configure Application Insights telemetry for performance monitoring and diagnostics. |
| [azure-cost-optimization](skills/azure-cost-optimization.md) | Get cost optimization recommendations for your Azure resources. |

## Next steps

- [Get started with Azure Skills](quickstart.md) — Complete a hands-on deployment
- [Install and configure Azure Skills](install.md) — Set up Azure Skills in your environment
- [Azure MCP Server documentation](https://learn.microsoft.com/azure/developer/azure-mcp-server/) — Technical details
