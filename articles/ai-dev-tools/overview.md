---
title: Azure AI Tools overview
description: Learn about Azure AI Tools — a collection of AI-powered developer tools including GitHub Copilot for Azure, Azure MCP Server, and Azure Skills that help you build, deploy, and manage Azure applications using natural language.
author: diberry
ms.author: diberry
ms.date: 04/02/2026
ms.topic: overview
ms.collection: ce-skilling-ai-copilot
ms.custom: build-2025
---

# Azure AI Tools overview

Azure AI Tools is a collection of AI-powered developer tools that help you manage, deploy, and troubleshoot Azure resources using natural language. The toolset includes GitHub Copilot for Azure, the Azure MCP Server, and Azure Skills. These tools work together across IDEs, terminals, and CI/CD pipelines.

## Why Azure AI Tools?

Building on Azure typically requires navigating portal UIs, reading documentation across multiple services, writing infrastructure-as-code templates, and debugging deployment issues. These tasks add friction before you write your first line of application code. This slows teams down and creates a steep learning curve, especially for developers new to Azure.

Azure AI Tools eliminates this friction by bringing Azure directly into your development workflow:

- **Reduce context switching:** Ask questions about Azure services, manage resources, and deploy applications without leaving your IDE or terminal.
- **Accelerate onboarding:** New team members can discover and use Azure services through natural language instead of memorizing CLI commands, portal navigation, or ARM/Bicep syntax.
- **Enforce best practices automatically:** Azure Skills embed guardrails and proven patterns into every workflow. Deployments follow organizational standards without manual review checklists.
- **Work where you already are:** Whether you use VS Code, Visual Studio, Cursor, IntelliJ, or a CLI, Azure AI Tools meets you in your existing environment.

## Key tools

| Tool | What it does | Best for |
|---|---|---|
| [GitHub Copilot for Azure](../github-copilot-azure/introduction.md) | VS Code and Visual Studio extension that surfaces Azure tools, skills, and instruction files through GitHub Copilot | Developers who want an integrated IDE experience with Azure-specific guidance |
| [Azure MCP Server](../azure-mcp-server/overview.md) | Standalone MCP server providing 35+ Azure service tools with Entra ID auth and RBAC | Developers who want Azure tools in any MCP-compatible client (VS Code, Cursor, Windsurf, IntelliJ, CLI) |
| [Azure Skills](../azure-skills/overview.md) | Domain-specific knowledge modules that provide end-to-end workflows with guardrails for common Azure scenarios | Developers who want guided, best-practice workflows for deployment, security, diagnostics, and more |

## Choose the right tool

Use the following decision flow to determine which Azure AI Tool best fits your scenario.

1. **Do you need remote or self-hosted AI tooling?**
   - Yes → **Azure MCP Server (self-hosted)** — Deploy as a remote MCP server for your team.
   - No → Continue to step 2.

2. **Are you using Visual Studio?**
   - Yes → **[GitHub Copilot for Azure (Visual Studio extension)](../github-copilot-azure/introduction.md)** — The only option for Visual Studio today.
   - No → Continue to step 3.

3. **Do you want interactive Azure tooling (ask questions, get answers)?**
   - Yes, and you want the VS Code extension experience → **[GitHub Copilot for Azure (VS Code extension)](../github-copilot-azure/introduction.md)**.
   - Yes, and you want IDE flexibility (Cursor, IntelliJ, Windsurf, etc.) → **[Azure MCP Server (local)](../azure-mcp-server/overview.md)**.
   - No → Continue to step 4.

4. **Do you want end-to-end Azure workflows with guardrails and best practices?**
   - Yes → **[Azure Skills](../azure-skills/overview.md)** — Available in GitHub Copilot CLI, Claude Code, VS Code, and other tools.

## Supported development environments

| Environment | GitHub Copilot for Azure | Azure MCP Server | Azure Skills |
|---|---|---|---|
| VS Code | ✅ Extension + MCP Server | ✅ | ✅ |
| Visual Studio 2022 | ✅ Extension | ✅ | ❌ |
| Cursor | ❌ | ✅ | ✅ |
| Windsurf | ❌ | ✅ | ✅ |
| IntelliJ | ❌ | ✅ | ✅ |
| GitHub Copilot CLI | ❌ | ✅ (via `/mcp add`) | ✅ |
| Claude Code | ❌ | ✅ | ✅ |

## How it works

Azure AI Tools uses a layered architecture to connect your development environment to Azure services:

- **Developer surfaces** (IDEs, CLIs) act as MCP clients. They send natural-language requests to MCP servers.
- **GitHub Copilot agent mode** selects the best tool from available MCP servers based on your request.
- **Azure MCP Server** translates tool calls into authenticated Azure API operations. It uses Microsoft Entra ID and RBAC for authorization.
- **Azure Skills** provide domain-specific knowledge that guides the AI through complex, multi-step workflows. Each skill includes built-in guardrails and best practices.

## Primary scenarios

| Scenario | Recommended tool | Example prompts |
|---|---|---|
| Learn about Azure services | GitHub Copilot for Azure | "What Azure services should I use with my app?" |
| Manage Azure resources | Azure MCP Server | "List all my storage accounts" |
| Deploy an application | Azure Skills (azure-deploy) | "Deploy my app to Azure" |
| Troubleshoot a failing app | GitHub Copilot for Azure + Azure MCP Server | "Why is my app returning 500 errors?" |
| Query resources across subscriptions | Azure MCP Server | "Show me all VMs across my subscriptions" |
| Set up E2E deployment pipeline | Azure Skills (azure-prepare → azure-validate → azure-deploy) | "Prepare and deploy my Node.js app to Azure" |

## Related content

- [GitHub Copilot for Azure documentation](../github-copilot-azure/introduction.md)
- [Azure MCP Server documentation](../azure-mcp-server/overview.md)
- [Azure Skills documentation](../azure-skills/overview.md)
