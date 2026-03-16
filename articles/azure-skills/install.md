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

This article walks you through installing Azure Skills into your AI assistant and verifying it works. After setup, you'll be able to ask questions about your Azure resources, prepare deployment plans, and manage cloud operations—all from your chat interface.

## Prerequisites

Make sure you have:

- **Node.js 18 or later** — [Download from nodejs.org](https://nodejs.org) or use a version manager like [nvm](https://github.com/nvm-sh/nvm)
- **Azure account** — [Create a free account](https://azure.microsoft.com/free/) if you don't have one
- **An AI assistant** — [GitHub Copilot CLI](../github-copilot-azure/overview.md), Claude Code, or another platform that supports Azure Skills plugins
- **Azure CLI** (optional but recommended) — Recommended for easier authentication during development

> [!NOTE]
> Azure Skills uses the same authentication patterns as [Azure MCP Server](../../developer/azure-mcp-server/overview.md). If you're already authenticated for Azure MCP Server, Azure Skills can use those same credentials.

## Authenticate to Azure

Azure Skills needs credentials to access your Azure resources. Choose the authentication method that fits your use case.

### Option A: Azure CLI (recommended for development)

This is the easiest method for local development and testing.

1. **Install Azure CLI:**
   - Visit the [Azure CLI installation guide](https://learn.microsoft.com/cli/azure/install-azure-cli)
   - Or use a package manager: `brew install azure-cli` (macOS), `apt-get install azure-cli` (Linux)

2. **Sign in to Azure:**
   ```bash
   az login
   ```
   A browser window opens. Sign in with your Azure account credentials.

3. **Verify authentication:**
   ```bash
   az account show
   ```
   You see your subscription details printed to the terminal. Azure Skills automatically detects this authentication.

### Option B: Environment Variables (for CI/CD and automation)

Use environment variables when you need to authenticate in scripts, CI/CD pipelines, or environments where the Azure CLI isn't available. You'll need a [service principal](https://learn.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli).

**Bash or Zsh:**
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

Azure Skills picks up these environment variables automatically.

### Option C: Managed Identity (for Azure-hosted resources)

If you're running Azure Skills on an Azure resource (VM, Container Apps, Azure Functions), managed identity handles authentication automatically. No manual setup needed.

For more details, see [Azure managed identities](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/).

## Install the plugin

In your AI assistant, install Azure Skills from the plugin marketplace:

```bash
/plugin marketplace add microsoft/github-copilot-for-azure
/plugin install azure@github-copilot-for-azure
```

These commands:
- Register the Azure plugin marketplace with your AI assistant
- Download and install the Azure Skills plugin (latest version from the marketplace)

## Verify installation

After installation, confirm Azure Skills is ready to use.

1. List installed plugins:
   ```bash
   /plugin list
   ```
   You should see `azure (github-copilot-for-azure)` in the output, with a list of available skills.

2. Test with a quick command:
   ```bash
   /ask List my Azure subscriptions
   ```
   Your AI assistant queries your Azure account and displays your subscriptions. The response shows subscription names, IDs, and status.

## Try it out: Your first Azure Skills interaction

Now that Azure Skills is installed and verified, try a real interaction. This shows you how to ask questions and explore your cloud resources.

Open your AI assistant's chat window and try these prompts:

**Explore your subscriptions:**
```prompt
What Azure subscriptions do I have access to?
```

Expected response: The assistant lists your subscriptions with names, IDs, resource group counts, and current status.

**Discover available skills:**
```prompt
What Azure Skills are available to me?
```

Expected response: The assistant displays all available skills organized by category: deployment (azure-prepare, azure-validate, azure-deploy), AI & ML (azure-ai), data access (azure-storage, azure-kusto), security (azure-rbac), and more.

**Try a skill in action:**
```prompt
Prepare a deployment plan for deploying an Azure App Service with a SQL Database
```

Expected response: The assistant uses the `azure-prepare` skill to generate a deployment plan showing resources, dependencies, and prerequisites.

## Supported AI assistants

Azure Skills is available across these platforms:

- **[GitHub Copilot CLI](../github-copilot-azure/overview.md)** — Full integration with GitHub Copilot tools
- **Claude Code** — Through the MCP protocol  
- **Other MCP-compatible AI assistants** — Any tool that supports the Model Context Protocol

For a complete list of tools that support Azure integration, see [Azure MCP Server supported tools](../../developer/azure-mcp-server/get-started.md#connect-to-azure-mcp-server).

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

## Related content

- [Azure Skills concepts](concepts.md) — Learn about skills, the prepare-validate-deploy workflow, and how Azure Skills integrates with Azure MCP Server
- [Overview of Azure Skills](overview.md) — Understand the business value and capabilities of Azure Skills
- [GitHub Copilot for Azure](/azure/copilot/overview) — Learn about GitHub Copilot's Azure integration features
- [Azure MCP Server get started guide](../../developer/azure-mcp-server/get-started.md) — Connect Azure MCP Server to your development tools
