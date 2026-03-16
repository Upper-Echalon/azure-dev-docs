---
title: Install and configure Azure Skills
description: Prerequisites, installation steps, and configuration options for Azure Skills plugin.
ms.topic: how-to
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# Install and configure Azure Skills

Set up Azure Skills to start using Azure from your AI assistant.

## Prerequisites

Before you begin, verify you have:

- **Node.js 18 or later** — Required for Azure Skills runtime
- **Azure account** — [Create a free account](https://azure.microsoft.com/free/) if you don't have one
- **Azure CLI** (optional but recommended) — For authentication
- **GitHub Copilot CLI** or **Claude Code** — The AI assistant you'll use

### Verify Node.js installation

Check your Node.js version:

```bash
node --version
```

If you need to install or upgrade Node.js, visit [nodejs.org](https://nodejs.org) or use a version manager like [nvm](https://github.com/nvm-sh/nvm).

## Step 1: Authenticate to Azure

Choose one of three authentication methods:

### Option A: Azure CLI (Recommended)

Use Azure CLI for development and testing.

1. **Install Azure CLI:**
   - Visit [Azure CLI installation guide](https://learn.microsoft.com/cli/azure/install-azure-cli)
   - Or use a package manager (brew, apt, etc.)

2. **Authenticate:**
   ```bash
   az login
   ```
   Your browser opens. Sign in with your Azure account.

3. **Verify:**
   ```bash
   az account show
   ```
   Your subscription details display.

Azure Skills automatically detect your CLI authentication.

### Option B: Environment Variables

Use environment variables for CI/CD pipelines or when Azure CLI isn't available.

Set these variables with your service principal credentials:

**Bash/Zsh:**
```bash
export AZURE_TENANT_ID="your-tenant-id"
export AZURE_CLIENT_ID="your-client-id"
export AZURE_CLIENT_SECRET="your-client-secret"
```

**PowerShell:**
```powershell
$env:AZURE_TENANT_ID = "your-tenant-id"
$env:AZURE_CLIENT_ID = "your-client-id"
$env:AZURE_CLIENT_SECRET = "your-client-secret"
```

**Windows Command Prompt:**
```cmd
set AZURE_TENANT_ID=your-tenant-id
set AZURE_CLIENT_ID=your-client-id
set AZURE_CLIENT_SECRET=your-client-secret
```

To create a service principal, see [Create an Azure service principal](https://learn.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli).

### Option C: Managed Identity

When running Azure Skills on Azure resources (VMs, Container Apps, Functions), managed identity handles authentication automatically. No configuration needed.

For setup details, see [Azure managed identities](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/).

## Step 2: Install the plugin

In your AI assistant, run these commands:

```
/plugin marketplace add microsoft/github-copilot-for-azure
/plugin install azure@github-copilot-for-azure
```

### What these commands do:

- **`/plugin marketplace add`** — Registers the Azure plugin marketplace
- **`/plugin install`** — Installs the Azure plugin (version: latest from marketplace)

## Verify installation

Ask your AI assistant to list available skills:

```
/plugin list
```

Azure Skills should appear in the plugin list. Example:

```
Available plugins:
- azure (github-copilot-for-azure)
  Skills: azure-prepare, azure-validate, azure-deploy, azure-ai, ...
```

Test with a simple command:

```
List my Azure subscriptions
```

Your AI assistant should query your Azure account and list subscriptions.

## Configuration options

### Telemetry

By default, Azure Skills collects usage telemetry to improve the service.

**To disable telemetry:**

```bash
export AZURE_MCP_COLLECT_TELEMETRY=false
```

## Troubleshooting

### "Authentication failed" error

**Problem:** Your AI assistant can't authenticate to Azure.

**Solutions:**
- **Azure CLI:** Run `az login` again and ensure you're authenticated
- **Environment variables:** Verify `AZURE_TENANT_ID`, `AZURE_CLIENT_ID`, and `AZURE_CLIENT_SECRET` are set correctly
- **Managed identity:** Confirm your Azure resource has an assigned managed identity

### "Plugin not found" error

**Problem:** Azure Skills plugin isn't installed or not recognized.

**Solutions:**
- Run `/plugin marketplace add microsoft/github-copilot-for-azure` to register the marketplace
- Run `/plugin install azure@github-copilot-for-azure` to install the plugin
- Restart your AI assistant
- Verify Node.js 18+ is installed

### "Insufficient permissions" error

**Problem:** Your Azure account doesn't have permissions for an operation.

**Solutions:**
- Check your [Azure RBAC role assignments](https://learn.microsoft.com/azure/role-based-access-control/role-assignments-list-portal)
- Request additional roles from your Azure administrator
- Use a different subscription where you have higher permissions

### "Invalid subscription" error

**Problem:** Azure Skills can't find or access your specified subscription.

**Solutions:**
- Run `az account list` to see available subscriptions
- Verify the subscription ID or name is correct
- Check that your credentials have access to the subscription

## Next steps

- [Get started with Azure Skills](quickstart.md) — Complete a hands-on deployment walkthrough
- [Azure Skills reference](skills-reference.md) — Learn what each skill does
- [Azure MCP Server documentation](https://learn.microsoft.com/azure/developer/azure-mcp-server/) — Understand the underlying Azure integration
