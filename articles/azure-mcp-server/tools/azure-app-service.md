---
title: Azure App Service tools - Azure MCP Server
description: Use the Azure App Service tools in Azure MCP Server to get guidance on Azure Functions development, deployment, and Azure SDK usage.
ms.service: azure-mcp-server
content_well_notification: 
  - AI-contribution
ai-usage: ai-assisted
ms.topic: concept-article
ms.date: 03/05/2026
author: diberry
ms.author: diberry
---

# Azure App Service tools for Azure MCP Server overview

Use Azure MCP Server to manage Azure resources, including Azure App Service instances, with natural language prompts. This feature lets you quickly manage your web applications without needing to remember complex syntax.

[Azure App Service](/azure/app-service/) is a managed platform for building, deploying, and scaling web apps. It offers built-in support for popular programming languages and frameworks, as well as features like autoscaling, custom domains, and SSL certificates. With Azure App Service, you can focus on application development rather than infrastructure management.

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]


## Database: Add connection

<!-- appservice database add -->

Add a [database connection](/azure/app-service/tutorial-connect-overview) to an App Service. This command configures database connection
settings for the specified App Service, allowing it to connect to a database server.

Example prompts include:

- Add database connection `connection_string` to app service `app` for database `database` in resource group `resource-group`.
- Configure SQL Server database `database` for app service `app` with connection string `connection_string` in resource group `resource-group`.
- Add MySQL database `database` to app service `app` using connection `connection_string` in resource group `resource-group`.
- Add PostgreSQL database `database` to app service `app` using connection `connection_string` in resource group `resource-group`.
- Connect Azure Cosmos DB database `database` using connection string `connection_string` to app service `app` in resource group `resource-group`.
- Add database connection `connection_string` for database `database` on server `database_server` to app service `app` in resource group `resource-group`.
- Add database connection string for `database` to app service `app` using connection string `connection_string` in resource group `resource-group`.
- Connect database `database` to app service `app` using connection string `connection_string` in resource group `resource-group`.
- Set up database `database` for app service `app` with connection string `connection_string` in resource group `resource-group`.
- Configure database `database` for app service `app` with connection string `connection_string` in resource group `resource-group`.

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **App** |  Required | The name of the Azure App Service (for example, `my-webapp`). |
| **Database** |  Required | The name of the database to connect to (for example, `mydb`). |
| **Database server** |  Required | The server name or endpoint for the database (for example, `myserver.database.windows.net`). |
| **Database type** |  Required | The type of database (for example, `SqlServer`, `MySQL`, `PostgreSQL`, `CosmosDB`). |
| **Resource group** |  Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Connection string** |  Optional | The connection string for the database. If not provided, a default will be generated. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ❌ | Open World: ✅ | Read Only: ❌ | Secret: ❌ | Local Required: ❌


## Get web app deployment details

<!-- @mcpcli appservice webapp deployment get -->

Retrieves detailed information about Azure App Service web app deployments, including deployment name, whether a deployment is currently happening, when the deployment started and ended, who authored and deployed it, and the type of deployment. If you do not provide a specific deployment ID, the command returns details for all deployments in the web app. You can specify a deployment ID to get details for a specific deployment.

Example prompts include:

- List all deployments for web app `my-webapp` in `my-resource-group`.
- Get details for deployment `deployment-id` in web app `my-webapp` from resource group `my-resource-group`.

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **App** | Required | The name of the Azure App Service (for example, `my-webapp`). |
| **Resource group** | Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Deployment ID** | Optional | The ID of the deployment. |


[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Get web app details

<!-- @mcpcli appservice webapp get -->

Retrieves detailed information about Azure App Service web apps, including app name, resource group, location, state, hostnames, and more. If you do not provide a specific app name, the command returns details for all web apps in your subscription or a specified resource group. You can specify the app name, resource group name, and subscription to get details for a specific web app.

Example prompts include:

- List all web apps in my subscription.
- Show me web apps in resource group `my-resource-group`.
- Get details for web app `my-webapp` in resource group `my-resource-group`.

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **App** | Optional | The name of the Azure App Service (for example, `my-webapp`). |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌


## Get application settings

<!-- @mcpcli appservice webapp settings get-appsettings -->

Retrieve the application settings for an App Service web app, returning key-value pairs that represent each setting. Be aware that application settings might contain sensitive information.

Example prompts include:

- List the application settings for web app `my-webapp` in `my-resource-group`.
- Get the application settings for web app `my-webapp` in `my-resource-group`.

| Parameter         | Required or optional | Description                                                                 |
|-------------------|----------------------|-----------------------------------------------------------------------------|
| **App**           | Required             | The name of the Azure App Service (for example, `my-webapp`).            |
| **Resource group**| Required             | The name of the Azure resource group. This serves as a logical container for Azure resources. |


[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ✅ | Local Required: ❌


## Update web app settings

<!-- @mcpcli appservice webapp settings update-appsettings -->

Updates the application setting for an Azure App Service web app. You can choose from three types of updates:

- **Add**. Adds a new application setting with the specified name and value. If the application setting already exists, the operation fails and returns an error message.
- **Set**. Sets the value of an application setting. If the application setting does not exist, this operation behaves the same as `add`. If the application setting already exists, the value is overwritten.
- **Delete**. Deletes an application setting with the specified name. If the application setting does not exist, nothing happens.

For both `add` and `set` update types, both the application setting name and value are required. For the `delete` update type, only the application setting name is required.

Example prompts include:

- Add application setting `setting-name` with `setting-value` to web app `app` in `resource-group`.
- Set application setting `setting-name` with `setting-value` to web app `app` in `resource-group`.
- Delete application setting `setting-name` from web app `app` in `resource-group`.

| Parameter                  | Required or optional | Description                                                                           |
|----------------------------|----------------------|---------------------------------------------------------------------------------------|
| **App**                    | Required             | The name of the Azure App Service (for example, `my-webapp`).                       |
| **Resource group**         | Required             | The name of the Azure resource group, which is a logical container for Azure resources. |
| **Setting name**           | Required             | The name of the application setting.                                                  |
| **Setting update type**    | Required             | The type of update to perform on the application setting.                             |
| **Setting value**          | Optional             | The value of the application setting. Required for `add` and `set` update types.     |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌


## Related resources

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)