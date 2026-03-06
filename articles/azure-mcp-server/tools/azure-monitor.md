---
title: Azure Monitor Tools 
description: "Use the Azure MCP Server with Azure Monitor to query Log Analytics workspaces, analyze metrics, and manage workbooks using natural language prompts."
keywords: azure mcp server, azmcp, azure monitor, log analytics
author: diberry
ms.author: diberry
ms.date: 03/06/2026
content_well_notification: 
  - AI-contribution
ai-usage: ai-assisted
ms.topic: concept-article
ms.custom: build-2025
tool_count for monitor: 11
tool_count for workbooks: 5
mcp-cli.version: 2.0.0-beta.25+02aa516434538ce124a06a01d89bcaa190b7e1ad
ms.reviewer: jong
--- 
# Azure Monitor tools for the Azure MCP Server overview

The Azure MCP Server allows you to manage Azure Monitor resources using natural language prompts. You can query Log Analytics workspaces, analyze operational data, monitor resource health, retrieve performance metrics, and manage Azure Monitor workbooks without needing to know complex KQL syntax.

[Azure Monitor](/azure/azure-monitor/overview) helps you maximize the availability and performance of your applications and services. It provides a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments. 

Workbooks provide a flexible canvas for data analysis and the creation of rich visual reports within the Azure portal. They allow you to tap into multiple data sources from across Azure and combine them into unified interactive experiences. Workbooks let you combine multiple kinds of visualizations and analyses, making them great for freeform exploration. For more information, see [Azure Monitor workbooks documentation](/azure/azure-monitor/visualize/workbooks-overview).

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

## Activity Log: List activity log

<!-- monitor activitylog list -->

List activity logs for the specified Azure resource over the given prior number of hours.

Example prompts include:

- **Recent critical events**: "Show activity logs for resource 'web-app-prod' for the last 4 hours with Critical and Error events only"
- **Storage account activity**: "Get activity logs for resource 'mystorageaccount' of type 'Microsoft.Storage/storageAccounts' from the last 24 hours, limit to top 50 entries"
- **VM monitoring**: "List all activity logs for resource 'production-vm01' from the past 12 hours"

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Resource name** |  Required | The name of the Azure resource to retrieve activity logs for. |
| **Resource type** |  Optional | The type of the Azure resource (for example, `Microsoft.Storage/storageAccounts`). Only provide this if needed to disambiguate between multiple resources with the same name. |
| **Hours** |  Optional | The number of hours prior to now to retrieve activity logs for. |
| **Event level** |  Optional | The level of activity logs to retrieve. Valid levels are: Critical, Error, Informational, Verbose, Warning. If not provided, returns all levels. |
| **Top** |  Optional | The maximum number of activity logs to retrieve. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor activitylog list](../includes/tools/annotations/azure-monitor-activity-log-list-annotations.md)]

## Web Tests: Create or update web tests

<!-- monitor webtests createorupdate 2.0.0-beta.19 -->

Create or update a standard web test in Azure Monitor to monitor endpoint availability. Use this command to set up new web tests or modify existing ones with configurations such as URL, frequency, locations, and expected responses. This command automatically creates a new test if it doesn't exist or updates an existing test with new settings.

Example prompts include:
- "Create or update web test resource 'mywebtest' in resource group 'rg-prod' to monitor `https://example.com` every 300 seconds."
- "Update the web test 'status-check' in resource group 'rg-dev' with expected status code `200` and enable SSL check."
- "What web tests are configured in resource group 'rg-test'?"
- "List all web test resources in 'rg-production'."
- "I need to create or update the web test 'api-monitor' in resource group 'rg-app' with a frequency of 600 seconds."

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Resource group** | Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Webtest resource** | Required | The name of the Web Test resource to operate on. |
| **App Insights component** | Optional | The resource ID of the Application Insights component to associate with the web test. |
| **Description** | Optional | The description of the web test. |
| **Enabled** | Optional | Whether the web test is enabled. |
| **Expected status code** | Optional | Expected HTTP status code. |
| **Follow redirects** | Optional | Whether to follow redirects. |
| **Frequency** | Optional | Test frequency in seconds. Supported values: 300, 600, 900 seconds. |
| **Headers** | Optional | HTTP headers to include in the request. Comma-separated `KEY=VALUE`. |
| **HTTP verb** | Optional | HTTP method (`get`, `post`, etc.). |
| **Ignore status code** | Optional | Whether to ignore the status code validation. |
| **Location** | Optional | The location where the web test resource is created. This should match the App Insights component location. |
| **Parse requests** | Optional | Whether to parse dependent requests. |
| **Request body** | Optional | The body of the request. |
| **Request URL** | Optional | The absolute URL to test. |
| **Retry enabled** | Optional | Whether retries are enabled. |
| **SSL check** | Optional | Whether to check SSL certificates. |
| **SSL lifetime check** | Optional | Number of days to check SSL certificate lifetime. |
| **Timeout** | Optional | Request timeout in seconds (max 2 minutes). Supported values: 30, 60, 90, 120 seconds. |
| **Webtest** | Optional | The name of the test in web test resource. |
| **Webtest locations** | Optional | List of locations to run the test from (comma-separated values). Location refers to the geo-location population tag specific to Availability Tests. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Web Tests: Get or list web tests

<!-- monitor webtests get 2.0.0-beta.19 -->

Retrieve details for a specific web test or list all web tests. When the webtest resource is provided, you get detailed information about a single web test. If the webtest resource is omitted, you receive a list of all web tests in your subscription, optionally filtered by resource group.

Example prompts include:

- "List all web tests in my subscription"
- "What web tests are available in my subscription?"
- "Get details for web test `homepage-load-test`"
- "Show me the specifics of the web test `api-response-check`"
- "Can you provide information on web test `checkout-validation` in my subscription?"

| Parameter            | Required or optional | Description                                               |
|----------------------|----------------------|-----------------------------------------------------------|
| **Webtest resource**  | Optional             | The name of the Web Test resource to operate on.         |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌


## Log Analytics: List workspaces

<!-- monitor workspace list -->

The Azure MCP Server lists all Log Analytics workspaces in a subscription. This provides an overview of your monitoring resources.

Example prompts include:

- **List workspaces**: "Show me all Log Analytics workspaces in my subscription."
- **View workspaces**: "What workspaces do I have?"
- **Find workspaces**: "List monitoring workspaces."

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor workspace list](../includes/tools/annotations/azure-monitor-workspace-list-annotations.md)]

## Log Analytics: List table types

<!-- monitor table type list -->

Lists available table types in a Log Analytics workspace. 

Example prompts include:

- **List table types**: "Show me table types in the centralmonitoring workspace in resource group 'my-resource-group'"
- **View available types**: "What table types are available in my Log Analytics workspace in resource group 'my-resource-group'?"
- **Find table categories**: "List table types for security-logs workspace in resource group 'my-resource-group'"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource group** |  Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Workspace** | Required | The Log Analytics workspace ID or name. This can be either the unique identifier (GUID) or the display name of your workspace. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor table type list](../includes/tools/annotations/azure-monitor-table-type-list-annotations.md)]

## Log Analytics: List tables

<!-- monitor table list -->

The Azure MCP Server lists all tables in a Log Analytics workspace. This helps you understand the data available for querying.

Example prompts include:

- **List tables**: "Show tables in centralmonitoring workspace in resource group 'my-resource-group'"
- **View tables**: "What tables are in workspace app-monitoring in resource group 'my-resource-group'?"
- **Find tables**: "List tables in security-logs workspace in resource group 'my-resource-group'"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource group** |  Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Workspace** | Required | The Log Analytics workspace ID or name. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor table list](../includes/tools/annotations/azure-monitor-table-list-annotations.md)]

## Log Analytics: Query workspace logs

<!-- monitor workspace log query -->

The Azure MCP Server can execute Kusto Query Language (KQL) queries against a Log Analytics workspace. This powerful feature allows you to analyze your operational data.

Example prompts include:

- **Simple query**: "Query table 'AzureDiagnostics' with query 'AzureDiagnostics | where Level == "Error" | take 100' in workspace 'app-monitoring' in resource group 'monitoring-rg' for last 1 hour"
- **Filter query**: "Query table 'SecurityEvent' with query 'SecurityEvent | where EventID == 4625 | project TimeGenerated, Account, Computer' in workspace 'security-workspace' in resource group 'security-rg'"
- **Complex query**: "Query table 'Perf' with query 'Perf | where CounterName == "% Processor Time" and Computer contains "web" | summarize avg(CounterValue) by bin(TimeGenerated, 1h)' in workspace 'monitoring-workspace' in resource group 'prod-rg' for last 24 hours"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource group** |  Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Workspace** | Required | The Log Analytics workspace ID or name. |
| **Table** | Required | The name of the table to query. |
| **Query** | Required | The KQL query to execute against the Log Analytics workspace. |
| **Hours** | Optional | The number of hours to query back from now. |
| **Limit** | Optional | The maximum number of results to return. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor workspace log query](../includes/tools/annotations/azure-monitor-workspace-log-query-annotations.md)]

## Log Analytics: Query resource logs

<!-- monitor resource log query -->

Queries diagnostic and activity logs for a specific Azure resource in a Log Analytics workspace using Kusto Query Language (KQL). 

Example prompts include:

- **Query recent logs**: "Query table 'AppServiceConsoleLogs' with query 'recent' for resource '/subscriptions/abc123/resourceGroups/prod/providers/Microsoft.Web/sites/myapp'"
- **Find errors**: "Query table 'AppServiceHTTPLogs' with query 'errors' for resource '/subscriptions/abc123/resourceGroups/prod/providers/Microsoft.Web/sites/mywebapp' in the last 4 hours"
- **Resource diagnostics**: "Query table 'StorageBlobLogs' with query 'StorageBlobLogs | take 100' for resource '/subscriptions/abc123/resourceGroups/prod/providers/Microsoft.Storage/storageAccounts/mystorage' with limit 100"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource ID** | Required | The Azure Resource ID to query logs. Example: `/subscriptions/<YOUR-SUBSCRIPTION-ID>/resourceGroups/<YOUR-RESOURCE-GROUP>/providers/Microsoft.OperationalInsights/workspaces/<YOUR-WORKSPACE>`. |
| **Table** | Required | The name of the table to query. This is the specific table within the workspace. |
| **Query** | Required | The KQL query to execute against the Log Analytics workspace. You can use predefined queries by name such as `recent` which shows most recent logs ordered by TimeGenerated and `errors` which shows error-level logs ordered by TimeGenerated. Otherwise, provide a custom KQL query. |
| **Hours** | Optional | The number of hours to query back from now. |
| **Limit** | Optional | The maximum number of results to return. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor resource log query](../includes/tools/annotations/azure-monitor-resource-log-query-annotations.md)]

## Health: Get entity health

<!-- monitor healthmodels entity get -->

The Azure MCP Server gets the health status of an entity using Azure Monitor health models. This provides comprehensive health information and monitoring status for Azure resources and applications.

Example prompts include:

- **Check entity health**: "Get health for entity 'app-prod-001' with model 'webapp-health' in resource group 'prod-rg'"
- **Monitor resource health**: "What's the health of entity 'web-app-prod' using model 'application-health' in resource group 'monitoring-rg'?"
- **Check system status**: "Get health info for entity 'sql-prod-db' with model 'database-health' in resource group 'data-rg'"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource group** |  Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Model** | Required | The name of the health model. |
| **Entity** | Required | The entity ID to get health for. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor healthmodels entity get](../includes/tools/annotations/azure-monitor-health-models-entity-get-annotations.md)]

## Metrics: Query metrics

<!-- monitor metrics query -->

The Azure MCP Server queries Azure Monitor metrics for resources. This allows you to retrieve performance metrics, usage statistics, and monitoring data for your Azure resources over specified time periods.

Example prompts include:

- **Query VM metrics**: "Get metrics 'Percentage CPU,Available Memory Bytes' with namespace 'Microsoft.Compute/virtualMachines' for resource 'prod-vm01' from January 1 to January 2"
- **Query storage metrics**: "Show metrics 'Transactions,Availability' with namespace 'Microsoft.Storage/storageAccounts' for resource 'mystorageaccount'"
- **Query app metrics**: "Get metrics 'ResponseTime,Requests' with namespace 'Microsoft.Web/sites' for resource 'mywebapp' last 24 hours"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource** | Required | The name of the resource to query metrics for. |
| **Metric namespace** | Required | The metric namespace. |
| **Metrics** | Required | The metric names to query. |
| **Resource type** | Optional | The type of the resource. |
| **Start time** | Optional | The start time for the query. |
| **End time** | Optional | The end time for the query. |
| **Interval** | Optional | The interval for aggregation. |
| **Aggregation** | Optional | The aggregation method. |
| **Filter** | Optional | Filter for the metrics query. |
| **Max buckets** | Optional | Maximum number of buckets. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor metrics query](../includes/tools/annotations/azure-monitor-metrics-query-annotations.md)]

## Metrics: List metric definitions

<!-- monitor metrics definitions -->

The Azure MCP Server lists available metric definitions for a resource. This helps you discover what metrics are available for monitoring before querying specific metric data.

Example prompts include:

- **List storage metrics**: "Show metrics for mystorageaccount."
- **Find transaction metrics**: "Find transaction metrics for storageacct."
- **List VM metrics**: "List metrics for prod-vm in production group."

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource name** | Required | The name of the resource. |
| **Resource type** | Optional | The type of the resource. |
| **Metric namespace** | Optional | The metric namespace. |
| **Search string** | Optional | Search string to filter metrics. |
| **Limit** | Optional | Maximum number of results to return. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

[!INCLUDE [monitor metrics definitions](../includes/tools/annotations/azure-monitor-metrics-definitions-annotations.md)]

## Create workbook

<!-- @mcpcli workbooks create -->

Create a new workbook in the specified resource group and subscription. You can set the display name and the serialized JSON content for the workbook. The command returns the created workbook information upon successful completion.

<!-- @mcpcli workbooks create -->
<!-- Required parameters: 3 - '--resource-group', '--display-name', '--serialized-content' -->

Example prompts include:
- "Create a new workbook in resource group `my-resource-group` with display name `My Workbook` and content `{"key": "value"}`"

| Parameter          | Required or optional | Description                                                |
|--------------------|----------------------|------------------------------------------------------------|
| **Display name**        | Required              | The display name of the workbook.                                     |
| **Resource group**      | Required              | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Serialized content**   | Required              | The serialized JSON content of the workbook.                        |
| **Source ID**           | Optional              | The linked resource ID for the workbook. By default, this is `azure monitor`.            |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ✅ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Delete workbook

<!-- @mcpcli workbooks delete -->

Delete one or more workbooks by their Azure resource IDs. This command performs a soft delete, retaining the workbooks for 90 days. If necessary, you can restore them from the Recycle Bin through the Azure Portal.

**BATCH**: Accepts multiple `--workbook-ids` values. Partial failures are reported per workbook. Individual failures do not cause the entire batch operation to fail.

To learn more, visit: [Manage Azure Monitor workbooks](/azure/azure-monitor/visualize/workbooks-manage)

<!-- @mcpcli workbooks delete -->
<!-- Required parameters: 1 - '--workbook-ids' -->

Example prompts include:
- "Delete the workbooks with resource IDs `workbook_resource_id_1` and `workbook_resource_id_2`"

| Parameter         | Required or optional | Description                                                                                           |
|-------------------|----------------------|-------------------------------------------------------------------------------------------------------|
| **Workbook IDs**  | Required             | The Azure Resource IDs of the workbooks to operate on (supports multiple values for batch operations).|

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Get workbooks list

<!-- @mcpcli workbooks list -->

Search Azure Workbooks using Resource Graph for a fast metadata query.

**Use for**: Discovering, filtering, and counting workbooks across scopes.  
**Returns**: Workbook metadata, including `id`, `name`, `location`, `category`, and timestamps.  
**Does not return**: Full workbook content (`serializedData`) by default. Use `show` for that or set `--output-format=full`.  

**Scope**: By default, this command searches for workbooks in your current Azure context (tenant/subscription). Use `--subscription` and `--resource-group` to explicitly control the scope.  
**Total Count**: Returns the server-side total count by default (not just the returned items).  
**Max Results**: The default is 50, with a maximum of 1000. Use `--max-results` to adjust.  
**Output Format**: Use `--output-format=summary` for a minimal response, or `--output-format=full` for `serializedData`.  

**Filters**: Use the following options for semantic filtering: `--name-contains`, `--category`, `--kind`, `--source-id`, and `--modified-after`.  

<!-- @mcpcli workbooks list -->
<!-- Required parameters: 0 -  -->

Example prompts include:
- "Show me all workbooks in resource group `my-rg`."
- "What workbooks are available in resource group `my-rg`?"

| Parameter               | Required or optional | Description                                                                                   |
|-------------------------|----------------------|-----------------------------------------------------------------------------------------------|
| **Category**            | Optional             | Filter workbooks by category (for example, `workbook`, `sentinel`, `TSG`). If not specified, all categories are returned. |
| **Include total count** | Optional             | Include the total count of all matching workbooks in the response (default: true).          |
| **Kind**                | Optional             | Filter workbooks by kind (for example, `shared`, `user`). If not specified, all kinds are returned. |
| **Max results**         | Optional             | Maximum number of results to return (default: 50, max: 1000).                              |
| **Modified after**      | Optional             | Filter workbooks modified after this date (ISO 8601 format, for example, `2024-01-15`).     |
| **Name contains**       | Optional             | Filter workbooks where the display name contains this text (case-insensitive).               |
| **Output format**       | Optional             | Output format: `summary` (ID and name only, minimal tokens), `standard` (metadata without content, default), `full` (includes `serializedData`). |
| **Source ID**           | Optional             | Filter workbooks by source resource ID (for example, Application Insights resource, Log Analytics workspace). If not specified, all workbooks are returned. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Get workbook details

<!-- @mcpcli workbooks show -->

Retrieve full workbook details via the Azure Resource Manager (ARM) API, including `serializedData` content.

**USE FOR:** Obtaining the complete workbook definition, including visualization JSON.  
**RETURNS:** Full workbook properties, `serializedData`, tags, and etag.

**BATCH:** Accepts multiple **workbook-ids** values. Partial failures are reported per workbook.  
**PERFORMANCE:** Use `list` first for discovery, then `show` for specific workbooks.

<!-- @mcpcli workbooks show -->
<!-- Required parameters: 1 - '--workbook-ids' -->

Example prompts include:
- "Retrieve details for the workbook with resource ID `<workbook_resource_id>`"
- "Display the workbook defined by resource ID `<workbook_resource_id>`"

| Parameter      | Required or optional | Description                                                                                      |
|----------------|----------------------|--------------------------------------------------------------------------------------------------|
| **Workbook IDs** | Required             | The Azure Resource IDs of the workbooks to operate on (supports multiple values for batch operations). |


[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Update workbook

<!-- @mcpcli workbooks update -->

Updates properties of an existing Azure Workbook by adding new steps, modifying content, or changing the display name. This command returns the updated workbook details. It requires the workbook resource ID and either new serialized content or a new display name.

<!-- @mcpcli workbooks update -->
<!-- Required parameters: 1 - '--workbook-id' -->

Example prompts include:
- Update the workbook `<workbook-id>` with a new display name `Annual Report`

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Workbook ID** | Required | The Azure Resource ID of the workbook to retrieve. |
| **Display name** | Optional | The display name of the workbook. |
| **Serialized content** | Optional | The JSON serialized content/data of the workbook. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Monitor](/azure/azure-monitor/overview)
- [Application Insights](/azure/azure-monitor/app/app-insights-overview)
- [Workbooks in Azure Monitor](/azure/azure-monitor/visualize/workbooks-overview)
- [Metrics in Azure Monitor](/azure/azure-monitor/platform/tutorial-metrics)
