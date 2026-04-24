---
title: Use GitHub Copilot with Azure Developer CLI
description: Learn how to use GitHub Copilot with the Azure Developer CLI (azd) for AI-assisted project scaffolding and intelligent deployment error troubleshooting.
author: alexwolfmsft
ms.author: alexwolf
ms.date: 04/20/2026
ms.service: azure-dev-cli
ms.topic: how-to
ms.custom: devx-track-azdevcli
ai-usage: ai-generated
---

# Use GitHub Copilot with Azure Developer CLI

The Azure Developer CLI (`azd`) integrates with GitHub Copilot to provide AI-assisted project scaffolding during `azd init` and intelligent error troubleshooting when commands fail.

## Prerequisites

To use these features, you need:

- **azd 1.23.11 or later** — Run `azd version` to check, or `azd update` to get the latest.
- **GitHub Copilot access** — An active GitHub Copilot subscription (Individual, Business, or Enterprise).
- **GitHub CLI (`gh`)** — `azd` automatically checks and prompts for login if needed.

## Copilot-powered project setup with `azd init`

Running `azd init` now presents a **Set up with GitHub Copilot (Preview)** option. Select it, and Copilot analyzes your codebase to scaffold the project, which includes generating `azure.yaml`, infrastructure templates, and deployment configuration based on your code's language, framework, and dependencies.

Copilot-powered init supports both new and existing projects. For new projects, Copilot generates the configuration and infrastructure from scratch. For existing projects, Copilot analyzes your codebase and generates the configuration needed to deploy it with `azd`.

Before making any changes, the flow runs preflight checks. It verifies your git working directory is clean so no uncommitted work is at risk. It also prompts for Model Context Protocol (MCP) server tool consent upfront so you can review what tools Copilot accesses.

To use Copilot-powered init:

```bash
azd init
# Select: "Set up with GitHub Copilot (Preview)"
```

The Copilot agent examines your project structure, proposes an `azure.yaml` configuration, and generates the necessary infrastructure files. You review and approve the changes before anything is written to disk.

### Example: scaffolding a Node.js app

For an Express API project with a `package.json`, a `src/` directory, and a PostgreSQL dependency, Copilot-powered init detects the Express framework and PostgreSQL dependency. It generates the `azure.yaml`, a Bicep module for Azure Container Apps, and a Bicep module for Azure Database for PostgreSQL. You review the generated files before they're written to disk.

## AI-assisted error troubleshooting

When an `azd` command fails, `azd` can use Copilot to analyze the error and suggest a fix. Copilot uses your project configuration and the error details to provide context-specific troubleshooting directly in your terminal. You can choose from several interactive options, configure a default behavior, or let Copilot auto-fix and retry.

### Copilot troubleshooting options

When an `azd` command fails, choose from four troubleshooting options:

- **Explain** — Get a plain-language explanation of what went wrong.
- **Guidance** — Receive step-by-step instructions to fix the issue.
- **Diagnose and Guide** — Get troubleshooting steps on what happened, why the error happened, and how to fix it. Let Copilot apply a fix (with your approval), then optionally retry the failed command.
- **Skip** — Dismiss and handle the error manually.

Copilot uses your project configuration, the command that failed, and the error details to provide suggestions specific to your situation.

### Set a default error handling behavior

If you prefer to use the same option consistently, set a default with `azd config` to skip the interactive prompt:

```bash
azd config set copilot.errorHandling.category troubleshoot
```

Available values for `copilot.errorHandling.category`:

| Value | Behavior |
| --- | --- |
| `explain` | Automatically get a plain-language explanation. |
| `guidance` | Automatically get step-by-step fix instructions. |
| `troubleshoot` | Automatically diagnose and guide. |
| `fix` | Automatically apply a fix. |
| `skip` | Always skip Copilot troubleshooting. |

You can also enable auto-fix and retry, so Copilot applies the fix and reruns the failed command automatically:

```bash
azd config set copilot.errorHandling.fix allow
```

To reset to the default interactive prompt, unset the config:

```bash
azd config unset copilot.errorHandling.category
```

### Common Azure deployment errors where Copilot helps

The following examples show common Azure deployment errors and how Copilot-assisted troubleshooting helps you resolve them.

#### `MissingSubscriptionRegistration` — resource provider not registered

A first-time deployment to a subscription often fails with:

```
ERROR: deployment failed: MissingSubscriptionRegistration:
The subscription is not registered to use namespace 'Microsoft.App'.
```

Azure requires resource providers to be registered before you can create certain resource types. If this Container App deployment is the first deployment in a given subscription, `Microsoft.App` isn't registered yet. The **Troubleshoot** option can register the provider and rerun the deployment automatically.

#### `SkuNotAvailable` / `OperationNotAllowed` — SKU or quota limits

You might encounter a SKU availability error:

```
ERROR: deployment failed: SkuNotAvailable:
The requested VM size 'Standard_D2s_v3' is not available in location 'westus'.
```

Or a quota variant:

```
ERROR: deployment failed: OperationNotAllowed:
Operation results in exceeding quota limits of Core.
Maximum allowed: 4, Current in use: 4, Additional requested: 2.
```

These errors are common when a region is capacity-constrained or your subscription hits its vCPU limit. Copilot's **Explain** option clarifies which SKU or quota is blocked, and **Guidance** suggests alternative regions or Virtual Machine (VM) sizes that are available or shows you how to request a quota increase.

#### `StorageAccountAlreadyTaken` — globally unique name collision

```
ERROR: deployment failed: StorageAccountAlreadyTaken:
The storage account named 'myappstorage' is already taken.
```

Storage account names must be unique across all of Azure. Copilot suggests updating your Bicep parameter or `azure.yaml` environment variable with a unique name, often by appending your environment name or a random suffix, and then retrying the deployment.

## Related content

- [Install or update azd](install-azd.md)
- [Explore the azd init workflow](azd-init-workflow.md)
- [Manage config settings](azd-config.md)
- [Troubleshoot the Azure Developer CLI](troubleshoot.md)
- [Sign up for azd user research](https://aka.ms/azd-user-research-signup)

[!INCLUDE [request-help](includes/request-help.md)]
