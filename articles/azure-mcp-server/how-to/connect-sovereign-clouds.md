---
title: Connect Azure MCP Server to sovereign clouds
description: Learn how to configure Azure MCP Server for Azure China Cloud and Azure US Government.
ms.topic: how-to
ms.date: 03/24/2026
ai-usage: ai-generated
---

This article shows you how to configure Azure MCP Server to authenticate against a sovereign cloud instead of the Azure public cloud. For example, use these steps when your subscription is in Azure US Government or Azure China Cloud, or when you need to provide a custom authority host.

## Prerequisites

- Access to an Azure subscription in Azure China Cloud or Azure US Government.
- A client or local setup that can start Azure MCP Server. For setup options, see [Get started with the Azure MCP Server](../get-started.md).
- At least one supported local authentication tool, such as [Azure CLI](/cli/azure/install-azure-cli), [Azure PowerShell](/powershell/azure/install-az-ps), or [Azure Developer CLI](../../azure-developer-cli/install-azd.md).

## Supported sovereign clouds

Azure MCP Server recognizes the following cloud names and maps them to the correct Microsoft Entra authority host.

| Cloud | Authority host | Supported aliases |
| --- | --- | --- |
| Azure Public Cloud | `https://login.microsoftonline.com` | `AzureCloud`, `AzurePublicCloud`, `Public`, `AzurePublic` |
| Azure China Cloud | `https://login.chinacloudapi.cn` | `AzureChinaCloud`, `China`, `AzureChina` |
| Azure US Government | `https://login.microsoftonline.us` | `AzureUSGovernment`, `USGov`, `AzureUSGovernmentCloud`, `USGovernment` |

Aliases are case-insensitive.

> [!NOTE]
> You can also pass a custom authority host URL that starts with `https://` if you need to target a nonstandard environment.

## Configure the cloud for Azure MCP Server

You can set the cloud either in the server arguments or through configuration. If you specify the cloud in more than one place, Azure MCP Server resolves the value in this order.

| Priority | Source | Setting |
| --- | --- | --- |
| 1 | Command line | `--cloud` |
| 2 | .NET configuration providers | `AZURE_CLOUD`, `azure_cloud`, `cloud`, `Cloud` |
| 3 | Environment variable fallback | `AZURE_CLOUD` |
| Default | Fallback | `AzurePublicCloud` |

### Configure using a server argument

If your MCP client starts Azure MCP Server for you, add `--cloud` to the server arguments.

```json
{
  "servers": {
    "Azure MCP Server": {
      "type": "stdio",
      "command": "npx",
      "args": [
        "-y",
        "@azure/mcp@latest",
        "server",
        "start",
        "--cloud",
        "AzureChinaCloud"
      ]
    }
  }
}
```

Replace `AzureChinaCloud` with `AzureUSGovernment` when you connect to Azure US Government.

### Configure using environment variables

If you start Azure MCP Server from a shell, or if your MCP client supports environment variables, set `AZURE_CLOUD` before starting the server.

# [PowerShell](#tab/powershell)

```powershell
$env:AZURE_CLOUD = "AzureUSGovernment"
azmcp server start
```

# [Bash](#tab/bash)

```bash
export AZURE_CLOUD=AzureChinaCloud
azmcp server start
```

# [Windows Command Prompt](#tab/cmd)

```cmd
set AZURE_CLOUD=AzureChinaCloud
azmcp server start
```

---

## Authenticate your local tools to the same cloud

Before you start Azure MCP Server, sign in to the same sovereign cloud in the local tools that Azure MCP Server can use for authentication.

### Azure CLI

Use Azure CLI when your workflow relies on `az login` or the Azure CLI credential.

```bash
az cloud set --name AzureUSGovernment
az login
```

For Azure US Government, replace `AzureUSGovernment` with `AzureChinaCloud`.

### Azure PowerShell

Use Azure PowerShell when your workflow relies on the Azure PowerShell credential.

```powershell
Connect-AzAccount -Environment AzureUSGovernment
```

For Azure US Government, replace `AzureUSGovernment` with `AzureChinaCloud`.

### Azure Developer CLI

Use Azure Developer CLI when your workflow relies on `azd auth login` or Azure Developer CLI credentials.

```bash
azd config set cloud.name AzureUSGovernment
azd auth login
```

For Azure US Government, replace `AzureUSGovernment` with `AzureChinaCloud`.

## Configure a self-hosted remote server

If you deploy Azure MCP Server as a remote MCP server, make sure the host environment is configured for the target sovereign cloud before you publish the endpoint.

Set these environment variables on the host or container:

- `AZURE_CLOUD`.
- `AzureAd__ClientCredentials__0__TokenExchangeUrl`.

If you use the Microsoft-provided Azure Container Apps templates, verify that both values match the target sovereign cloud before you publish the remote endpoint. For template-based deployments, review the upstream template guidance in the Azure MCP Server repository.

## Verify the connection

1. Restart your MCP client after you change the cloud configuration.

1. Run a simple prompt that requires Azure context, such as `List my resource groups`.

1. If the request fails, verify that your local tools are authenticated to the same sovereign cloud and tenant as the Azure subscription you want to use.

## Troubleshoot sovereign cloud configuration

If authentication or discovery fails, check the following items.

- Confirm that the cloud name is valid. An unrecognized value falls back to the Azure public cloud.
- Confirm that your tenant belongs to the sovereign cloud subscription you want to access. For example, run `az account show --query tenantId -o tsv`.
- Confirm that you can reach the correct authority host for your cloud.
  - Azure China Cloud: `https://login.chinacloudapi.cn`.
  - Azure US Government: `https://login.microsoftonline.us`.
- Confirm that remote deployments set both `AZURE_CLOUD` and `AzureAd__ClientCredentials__0__TokenExchangeUrl`.

If you still have problems, see the Azure MCP Server [troubleshooting guide](https://github.com/microsoft/mcp/blob/main/servers/Azure.Mcp.Server/TROUBLESHOOTING.md#sovereign-cloud-support).

## Related content

- [Get started with the Azure MCP Server](../get-started.md)
- [Azure MCP Server overview](../overview.md)
- [Deploy a self-hosted remote Azure MCP Server and connect to it using Copilot Studio](deploy-remote-mcp-server-copilot-studio.md)
- [Deploy a self-hosted remote Azure MCP Server and connect to it using Microsoft Foundry](deploy-remote-mcp-server-microsoft-foundry.md)
