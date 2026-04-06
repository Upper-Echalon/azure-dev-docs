---
title: Get started with Azure Skills
description: Deploy your first Azure application using Azure Skills in 5 minutes.
ms.topic: quickstart
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Get started with Azure Skills

In this quickstart, you prepare, validate, and deploy a simple application to Azure using Azure Skills.

## Prerequisites

- Azure Skills installed ([Install and configure Azure Skills](install.md))
- Azure CLI authenticated (`az login` completed successfully)
- GitHub Copilot CLI or Claude Code ready to use
- A sample application (or create a simple Node.js app)

## Scenario

You have a simple Node.js application. You want to deploy it to Azure with:
- Web application hosting (Azure App Service)
- A storage account for application data
- Monitoring with Application Insights

## Step 1: Prepare your application

In your AI assistant, navigate to your project directory and ask:

```bash
Prepare my application for Azure deployment
```

The `azure-prepare` skill:
1. Analyzes your codebase
2. Identifies technology stack (Node.js, npm, etc.)
3. Creates `.azure/plan.md` with a deployment strategy
4. Generates infrastructure-as-code
5. Waits for your approval

### Review the generated plan

Open `.azure/plan.md` and review:
- **Project Information** — Application name and deployment mode
- **Requirements** — Classification and scale (small, medium, large)
- **Components** — Technologies detected
- **Deployment Strategy** — Technology used to deploy your application (Azure Developer CLI, Bicep, Terraform, or Azure CLI).
- **Architecture** — Azure services selected
- **Implementation Plan** — Step-by-step tasks

Example plan content:

```yaml
# Azure Deployment Plan

## Project Information
- Application: my-app
- Mode: NEW

## Requirements
- Classification: Web Application
- Scale: Small
- Environment: Production

## Components
- Runtime: Node.js 18+
- Package Manager: NPM
- Application Type: Express web server

## Recipe
- Type: AZD (Azure Developer CLI)

## Azure Services
- Azure App Service (web app hosting)
- Azure Storage Account (data)
- Application Insights (monitoring)

## Status: Awaiting Approval
```

### Approve the plan

If the plan looks correct, tell your AI assistant:

```bash
Approve this plan and proceed to validation
```

The skill updates the plan status to `Approved` and moves to the next step.

## Step 2: Validate the deployment plan

Your AI assistant now runs the `azure-validate` skill to check:
- Azure CLI access and permissions
- Bicep/Terraform template syntax (if applicable)
- Azure subscription and region availability
- Service quota limits
- Required permissions for your account

Validation completes and records proof of all checks in the plan. The plan status updates to `Validated`.

### Review validation results

Check `.azure/plan.md` for the **Validation Proof** section, which shows:
- Commands executed
- Timestamp
- Results (passed/failed)

Example:

```yaml
## Validation Proof
- Command: azd provision --preview
- Timestamp: 2026-03-16T14:22:00Z
- Result: ✓ All validation checks passed
```

If validation fails, review errors and ask your AI assistant to fix issues:

```bash
Fix the validation errors and try again
```

## Step 3: Deploy to Azure

When your plan is validated, tell your AI assistant:

```bash
Deploy my application to Azure
```

The `azure-deploy` skill:
1. Confirms plan status is `Validated`
2. Provisions Azure resources (storage, app service, monitoring)
3. Deploys your application code
4. Configures application settings
5. Provides your application endpoint

Deployment typically takes 3-5 minutes.

### View your deployed application

After successful deployment, your AI assistant provides:
- Application URL (for App Service)
- Storage account name and access keys
- Application Insights instrumentation key

Example:

```output
Deployment complete! 

Your app is live at: https://my-app-abcd1234.azurewebsites.net

Resources deployed:
- App Service: my-app-prod
- Storage Account: mystorageabcd1234
- Application Insights: my-app-insights

Monitor your app: https://portal.azure.com/...
```

Visit your application URL in a browser to verify it's running.

## Step 4: Verify your deployment

Test your application:

1. **Visit your URL** — Open the application URL in a browser
2. **Check monitoring** — View logs in Application Insights
3. **Test functionality** — Use key features of your app

Ask your AI assistant for monitoring status:

```bash
Show me the application logs and performance metrics
```

Your AI assistant queries Application Insights and displays recent activity, errors, and performance data.

## Step 5: Update and redeploy

If you make code changes, redeploy easily:

1. **Update your code** in your editor
2. **Ask your AI assistant:**
   ```bash
   Update the deployment with my latest changes
   ```
3. The skill runs `azure-prepare` to check for changes, then `azure-deploy` to update your resources.

Updated resources reuse existing infrastructure. Only changed components redeploy.

## Clean up resources

When you no longer need your application, delete Azure resources to avoid charges:

```bash
Delete all Azure resources for this application
```

Your AI assistant:
1. Lists resources to be deleted (for your confirmation)
2. Deletes the resource group and all contents
3. Confirms cleanup complete

Example:

```output
Resources to delete:
- Resource Group: my-app-rg
- All contained resources

Are you sure? (yes/no)
```

Type "yes" to confirm deletion.

## Troubleshooting

### Deployment fails with authentication error

**Problem:** Your AI assistant can't authenticate to Azure.

**Solution:** Re-authenticate with `az login` and try again.

### Plan validation fails

**Problem:** Azure Skills reports validation errors.

**Solution:** Ask your AI assistant to review and fix issues:
```bash
Why did validation fail? Fix the errors.
```

### Application not accessible after deployment

**Problem:** The provided URL returns an error or times out.

**Solution:**
1. Verify the URL is correct
2. Wait 1-2 minutes for DNS propagation
3. Check Application Insights logs for errors:
   ```bash
   Show me recent errors in Application Insights
   ```

## Next steps

- [Azure MCP Server documentation](../azure-mcp-server/overview.md) — Deeper technical details
