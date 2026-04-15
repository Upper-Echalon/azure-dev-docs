---
title: Azure AI developer tools overview
description: The Azure AI developer tools help you build, deploy, and manage Azure applications with natural language through GitHub Copilot for Azure, Azure MCP Server, and Azure Skills.
author: diberry
ms.author: diberry
ms.date: 04/02/2026
ms.topic: overview
ms.collection: ce-skilling-ai-copilot
ms.custom: build-2025
---

# Azure AI developer tools overview

The Azure AI developer tools are a collection of AI-powered tools that help you manage, deploy, and troubleshoot Azure resources by using natural language. The toolset includes GitHub Copilot for Azure, the Azure MCP Server, and Azure Skills. These tools work together across IDEs, terminals, and CI/CD pipelines.

## Why use Azure AI developer tools?

Building on Azure typically requires navigating portal UIs, reading documentation across multiple services, writing infrastructure-as-code templates, and debugging deployment issues. These tasks add friction before you write your first line of application code. This friction slows teams down and creates a steep learning curve, especially for developers new to Azure.

The Azure AI developer tools eliminate this friction by bringing Azure directly into your development workflow:

- **Reduce context switching** - Ask questions about Azure services, manage resources, and deploy applications without leaving your IDE or terminal.
- **Accelerate onboarding** - New team members can discover and use Azure services through natural language. They don't need to memorize CLI commands, portal navigation, or ARM/Bicep syntax.
- **Enforce best practices automatically** - Azure Skills embed guardrails and proven patterns into every workflow. Deployments follow organizational standards without manual review checklists.
- **Work where you already are** - Whether you use VS Code, Visual Studio, Cursor, IntelliJ, or a CLI, the Azure AI developer tools meet you in your existing environment.

## Key tools

| Tool | What it does | Best for |
|---|---|---|
| [GitHub Copilot for Azure](../github-copilot-azure/introduction.md) | Extension that surfaces Azure tools and skills through GitHub Copilot | Integrated IDE experience in VS Code or Visual Studio |
| [Azure MCP Server](../azure-mcp-server/overview.md) | Standalone MCP server with 270+ tools across 50+ Azure services and Microsoft Entra ID authentication | Azure tools in any MCP-compatible client |
| [Azure Skills](../azure-skills/overview.md) | Knowledge modules that provide end-to-end workflows with guardrails | Guided, best-practice Azure workflows |

## Choose the right tool

Use the following decision flow to determine which tool best fits your scenario.

1. **Do you need remote or self-hosted AI tooling?**
   - Yes → **Azure MCP Server (self-hosted)** — Deploy as a remote MCP server for your team.
   - No → Continue to step 2.

1. **Are you using Visual Studio?**
   - Yes → **[GitHub Copilot for Azure (Visual Studio extension)](../github-copilot-azure/introduction.md)** — The only option for Visual Studio today.
   - No → Continue to step 3.

1. **Do you want interactive Azure tooling?**
   - Yes, in VS Code → **[GitHub Copilot for Azure](../github-copilot-azure/introduction.md)**.
   - Yes, in another IDE such as Cursor, IntelliJ, or Windsurf → **[Azure MCP Server](../azure-mcp-server/overview.md)**.
   - No → Continue to step 4.

1. **Do you want end-to-end Azure workflows with guardrails and best practices?**
   - Yes → **[Azure Skills](../azure-skills/overview.md)** — Available in GitHub Copilot CLI, Claude Code, VS Code, and other tools.

## Supported development environments

| Environment | GitHub Copilot for Azure | Azure MCP Server | Azure Skills |
|---|---|---|---|
| VS Code | ✅ Extension + MCP Server | ✅ | ✅ |
| Visual Studio 2022 | ✅ Built-in (with Azure Workload) | ✅ | ❌ |
| Visual Studio 2026 | ✅ Built-in (with Azure Workload) | ✅ | ❌ |
| Cursor | ❌ | ✅ | ✅ |
| Windsurf | ❌ | ✅ | ✅ |
| IntelliJ | ❌ | ✅ | ✅ |
| GitHub Copilot CLI | ❌ | ✅ (via `/mcp add`) | ✅ |
| Claude Code | ❌ | ✅ | ✅ |

## Primary scenarios

| Scenario | Recommended tool | Example prompts |
|---|---|---|
| Learn about Azure services | GitHub Copilot for Azure | "What Azure services should I use with my app?" |
| Manage Azure resources | Azure MCP Server | "List all my storage accounts" |
| Deploy an application | Azure Skills (azure-deploy) | "Deploy my app to Azure" |
| Troubleshoot a failing app | GitHub Copilot for Azure | "Why is my app returning 500 errors?" |
| Query resources across subscriptions | Azure MCP Server | "Show me all VMs across my subscriptions" |
| Set up end-to-end deployment pipeline | Azure Skills (azure-prepare, azure-validate, azure-deploy) | "Prepare and deploy my Node.js app to Azure" |

## Related content

- [GitHub Copilot for Azure documentation](../github-copilot-azure/introduction.md)
- [Azure MCP Server documentation](../azure-mcp-server/overview.md)
- [Azure Skills documentation](../azure-skills/overview.md)
