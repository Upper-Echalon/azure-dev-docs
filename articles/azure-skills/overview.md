---
title: Azure Skills overview
description: Connect your AI assistant to Azure to manage resources, deploy apps, and monitor services without leaving your editor.
ms.topic: overview
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# Azure Skills overview

**Azure Skills** is a plugin that connects GitHub Copilot CLI or Claude Code to your Azure account. It gives your AI assistant the ability to manage resources, deploy applications, and monitor services directly from your development environment.

Work with Azure without switching between tools, context windows, or documentation tabs. Ask your AI assistant to build, validate, and deploy—and it handles the Azure operations for you.

## Why Azure Skills?

Traditional Azure workflows require you to:
- Leave your editor to use the Azure portal
- Context-switch between documentation and your IDE
- Learn Azure CLI commands and service-specific workflows
- Run multiple validation steps manually

**Azure Skills** eliminates this friction. Your AI assistant becomes a full Azure development partner, understanding your application architecture and executing Azure operations at your direction.

## How it works

Azure Skills is built on the **Azure MCP Server**, which provides your AI assistant with tools to interact with 40+ Azure services. Skills layer high-level workflows on top of those tools.

When you ask your AI assistant to prepare an application for Azure, it:
1. Analyzes your codebase
2. Creates a detailed deployment plan
3. Generates infrastructure-as-code
4. Validates the setup
5. Deploys your app to Azure

All without you leaving your editor.

## The workflow: prepare → validate → deploy

Azure Skills follow a three-step workflow designed to prevent errors and ensure safe deployments.

| Step | Skill | What happens |
|------|-------|--------------|
| **Plan** | `azure-prepare` | Your assistant analyzes your app, creates `.azure/plan.md` with deployment strategy, and waits for your approval before proceeding. |
| **Check** | `azure-validate` | Validates the plan before deployment. Runs configuration checks, permission verification, and infrastructure validation. |
| **Deploy** | `azure-deploy` | Executes the deployment. Runs provisioning, infrastructure deployment, and application setup. |

This structured approach keeps deployments safe and auditable. You always review the plan before anything happens in Azure.

## Available skills

Azure Skills include 18 specialized capabilities, organized by function:

### Development lifecycle
- **azure-prepare** — Plan application deployment (entry point)
- **azure-validate** — Validate before deployment
- **azure-deploy** — Execute deployment

### AI & Machine Learning
- **azure-ai** — Azure AI Search, Speech, OpenAI, Document Intelligence
- **azure-aigateway** — AI Gateway service management
- **microsoft-foundry** — Microsoft Foundry models, deployments, RAG, agents

### Data & Analytics
- **azure-postgres** — Azure Database for PostgreSQL
- **azure-kusto** — Azure Data Explorer (KQL queries)
- **azure-storage** — Azure Storage services (Blob, Files, Tables)

### Security & Identity
- **azure-rbac** — Role-based access control
- **azure-compliance** — Compliance and governance checks
- **entra-app-registration** — Microsoft Entra app registration

### Infrastructure & Monitoring
- **azure-resource-lookup** — Find and inspect Azure resources
- **azure-resource-visualizer** — Visualize Azure resource topology
- **azure-diagnostics** — Debug and troubleshoot issues
- **azure-observability** — Monitoring, logging, and alerts
- **appinsights-instrumentation** — Application Insights setup
- **azure-cost-optimization** — Cost optimization recommendations

## Who is this for?

Azure Skills is designed for developers who:
- Build applications on Azure
- Use GitHub Copilot CLI or Claude Code
- Want to reduce context switching and manual Azure workflows
- Need to plan, validate, and deploy safely

## Get started

To use Azure Skills:

1. **Install Node.js 18 or later** — Azure Skills requires Node.js as its runtime.
2. **Authenticate to Azure** — Use Azure CLI (`az login`), environment variables, or managed identity.
3. **Install the plugin** — Run `/plugin marketplace add microsoft/github-copilot-for-azure` and `/plugin install azure@github-copilot-for-azure`.
4. **Start building** — Ask your AI assistant to prepare your application for Azure.

For detailed setup instructions, see [Install and configure Azure Skills](install.md).

For a hands-on walkthrough, see [Get started with Azure Skills](quickstart.md).

## Learn more

- [Key concepts in Azure Skills](concepts.md) — Understand how skills work and how they integrate with your development workflow.
- [Azure Skills reference](skills-reference.md) — Full documentation of all 18 skills and their capabilities.
- [Azure MCP Server](https://learn.microsoft.com/azure/developer/azure-mcp-server/) — Technical documentation for the underlying Azure integration.
