---
title: Azure MCP Server tools for Azure Monitor and Workbooks
description: Use Azure MCP Server tools to query Azure Monitor logs and metrics, monitor resource health, and manage Azure Workbooks with natural language prompts from your IDE.
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
ms.date: 03/23/2026
content_well_notification: 
  - AI-contribution
ai-usage: ai-assisted
ms.topic: concept-article
ms.custom: build-2025
tool_count for monitor: 17
tool_count for workbooks: 5
ms.reviewer: jong
mcp-cli.version: 2.0.0-beta.31
---
# Azure MCP Server tools for Azure Monitor and Workbooks

The Azure Model Context Protocol (MCP) Server lets you manage Azure Monitor and Workbooks resources with natural language prompts. You can query Log Analytics workspaces, analyze operational data, monitor resource health, retrieve performance metrics, and manage Azure Monitor workbooks.

[Azure Monitor](/azure/azure-monitor/overview) helps you maximize the availability and performance of your applications and services. It provides a comprehensive solution for collecting, analyzing, and acting on telemetry from your cloud and on-premises environments. 

Workbooks provide a flexible canvas for data analysis and the creation of rich visual reports within the Azure portal. They allow you to tap into multiple data sources from across Azure and combine them into unified interactive experiences. Workbooks let you combine multiple kinds of visualizations and analyses, making them great for freeform exploration. For more information, see [Azure Monitor workbooks documentation](/azure/azure-monitor/visualize/workbooks-overview).

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

## Activity Log: List activity log

<!-- @mcpcli monitor activitylog list -->

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

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Web Tests: Create web test

<!-- @mcpcli monitor webtests create -->

Create a new standard web test in Azure Monitor to monitor endpoint availability. Specify the web test resource name, associated Application Insights component, test location, and the URL to monitor.

Example prompts include:

- "Create a new Standard Web Test with name 'mywebtest' in resource group 'rg-prod' for a given App Insights component"
- "Set up a web test to monitor `https://example.com` every 300 seconds in resource group 'rg-dev'"
- "Create web test 'api-monitor' in resource group 'rg-app' with a frequency of 600 seconds"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Resource group** | Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Webtest resource** | Required | The name of the Web Test resource to operate on. |
| **App Insights component** | Required | The resource ID of the Application Insights component to associate with the web test. |
| **Location** | Required | The location where the web test resource is created. This should match the App Insights component location. |
| **Webtest locations** | Required | List of locations to run the test from (comma-separated values). Location refers to the geo-location population tag specific to Availability Tests. |
| **Request URL** | Required | The absolute URL to test. |
| **Webtest** | Optional | The name of the test in web test resource. |
| **Description** | Optional | The description of the web test. |
| **Enabled** | Optional | Whether the web test is enabled. |
| **Expected status code** | Optional | Expected HTTP status code. |
| **Follow redirects** | Optional | Whether to follow redirects. |
| **Frequency** | Optional | Test frequency in seconds. Supported values: 300, 600, 900 seconds. |
| **Headers** | Optional | HTTP headers to include in the request. Comma-separated `KEY=VALUE`. |
| **HTTP verb** | Optional | HTTP method (`get`, `post`, etc.). |
| **Ignore status code** | Optional | Whether to ignore the status code validation. |
| **Parse requests** | Optional | Whether to parse dependent requests. |
| **Request body** | Optional | The body of the request. |
| **Retry enabled** | Optional | Whether retries are enabled. |
| **SSL check** | Optional | Whether to check SSL certificates. |
| **SSL lifetime check** | Optional | Number of days to check SSL certificate lifetime. |
| **Timeout** | Optional | Request timeout in seconds (max 2 minutes). Supported values: 30, 60, 90, 120 seconds. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Web Tests: Get web test details

<!-- @mcpcli monitor webtests get -->

Retrieve details for a specific web test by its resource name. Returns configuration, status, and test settings for the specified web test.

Example prompts include:

- "Get Web Test details for 'homepage-load-test' in resource group 'rg-prod'"
- "Show me the configuration of web test 'api-response-check' in resource group 'rg-test'"
- "Get details for web test 'checkout-validation' in resource group 'rg-dev'"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Resource group** | Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Webtest resource** | Required | The name of the Web Test resource to operate on. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Web Tests: List web tests

<!-- @mcpcli monitor webtests list -->

List all web tests in your subscription, optionally filtered by resource group.

Example prompts include:

- "List all Web Test resources in my subscription"
- "List all web tests in resource group 'rg-production'"
- "What web tests are available in my subscription?"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Resource group** | Optional | The name of the Azure resource group to filter web tests by. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Web Tests: Update web test

<!-- @mcpcli monitor webtests update -->

Update an existing web test in Azure Monitor with new configuration settings. Modify properties such as URL, frequency, locations, and expected responses.

Example prompts include:

- "Update the web test 'status-check' in resource group 'rg-dev' with expected status code 200"
- "Change the frequency of web test 'api-monitor' in resource group 'rg-app' to 600 seconds"
- "Update web test 'mywebtest' in resource group 'rg-prod' to enable SSL check"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Resource group** | Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Webtest resource** | Required | The name of the Web Test resource to operate on. |
| **App Insights component** | Optional | The resource ID of the Application Insights component to associate with the web test. |
| **Location** | Optional | The location where the web test resource is created. This should match the App Insights component location. |
| **Webtest locations** | Optional | List of locations to run the test from (comma-separated values). Location refers to the geo-location population tag specific to Availability Tests. |
| **Request URL** | Optional | The absolute URL to test. |
| **Webtest** | Optional | The name of the test in web test resource. |
| **Description** | Optional | The description of the web test. |
| **Enabled** | Optional | Whether the web test is enabled. |
| **Expected status code** | Optional | Expected HTTP status code. |
| **Follow redirects** | Optional | Whether to follow redirects. |
| **Frequency** | Optional | Test frequency in seconds. Supported values: 300, 600, 900 seconds. |
| **Headers** | Optional | HTTP headers to include in the request. Comma-separated `KEY=VALUE`. |
| **HTTP verb** | Optional | HTTP method (`get`, `post`, etc.). |
| **Ignore status code** | Optional | Whether to ignore the status code validation. |
| **Parse requests** | Optional | Whether to parse dependent requests. |
| **Request body** | Optional | The body of the request. |
| **Retry enabled** | Optional | Whether retries are enabled. |
| **SSL check** | Optional | Whether to check SSL certificates. |
| **SSL lifetime check** | Optional | Number of days to check SSL certificate lifetime. |
| **Timeout** | Optional | Request timeout in seconds (max 2 minutes). Supported values: 30, 60, 90, 120 seconds. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Log Analytics: List workspaces

<!-- @mcpcli monitor workspace list -->

The Azure MCP Server lists all Log Analytics workspaces in a subscription. This provides an overview of your monitoring resources.

Example prompts include:

- **List workspaces**: "Show me all Log Analytics workspaces in my subscription."
- **View workspaces**: "What workspaces do I have?"
- **Find workspaces**: "List monitoring workspaces."

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Log Analytics: List tables

<!-- @mcpcli monitor table list -->

The Azure MCP Server lists all tables in a Log Analytics workspace. This helps you understand the data available for querying.

Example prompts include:

- **List tables**: "Show tables in centralmonitoring workspace in resource group 'my-resource-group'"
- **View tables**: "What tables are in workspace app-monitoring in resource group 'my-resource-group'?"
- **Find tables**: "List tables in security-logs workspace in resource group 'my-resource-group'"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource group** |  Required | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Workspace** | Required | The Log Analytics workspace ID or name. |
| **Table type** | Required | The type of table to query (for example, `CustomLog`, `AzureMetrics`). |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Log Analytics: Query workspace logs

<!-- @mcpcli monitor workspace log query -->

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

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Log Analytics: Query resource logs

<!-- @mcpcli monitor resource log query -->

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

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Health: Get entity health

<!-- @mcpcli monitor healthmodels entity get -->

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

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Metrics: Query metrics

<!-- @mcpcli monitor metrics query -->

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

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Metrics: List metric definitions

<!-- @mcpcli monitor metrics definitions -->

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

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Instrumentation: Get learning resource

<!-- @mcpcli monitor instrumentation get-learning-resource -->

Get a specific learning resource by path or list all available Azure Monitor onboarding learning resources.

Example prompts include:

- "Get the onboarding learning resource at path 'getting-started/overview'"
- "List all available Azure Monitor onboarding learning resources"
- "What learning resources are available for Azure Monitor instrumentation onboarding?"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Path** | Optional | The path of the learning resource to retrieve. If omitted, lists all available resources. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ✅

## Instrumentation: Start orchestration

<!-- @mcpcli monitor instrumentation orchestrator-start -->

Start deterministic instrumentation orchestration for a local workspace. Analyzes the workspace and returns the first Azure Monitor instrumentation step.

Example prompts include:

- "Start Azure Monitor instrumentation orchestration for workspace '/path/to/project'"
- "Analyze workspace '/path/to/project' and return the first Azure Monitor instrumentation step"
- "Begin guided Azure Monitor onboarding for project at '/path/to/project' and give me step one"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Workspace path** | Required | The absolute path to the local workspace to analyze. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ✅

## Instrumentation: Continue orchestration

<!-- @mcpcli monitor instrumentation orchestrator-next -->

Continue orchestration after completing the previous action. Returns the next instrumentation step in the onboarding flow.

Example prompts include:

- "After completing the previous Azure Monitor instrumentation step, get the next action for session 'abc-123' with completion note 'installed SDK packages'"
- "Get the next onboarding action using session 'abc-123' after I completed 'configured telemetry exporters'"
- "I finished the previous instrumentation step; return the next step for session 'abc-123' with note 'added connection string'"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Session ID** | Required | The orchestration session identifier returned by orchestrator-start. |
| **Completion note** | Required | A description of what was completed in the previous step. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ✅

## Instrumentation: Send brownfield analysis

<!-- @mcpcli monitor instrumentation send-brownfield-analysis -->

Send brownfield analysis findings JSON to continue migration flow. Use this when the orchestrator returns an `analysis_needed` status with an analysis template.

Example prompts include:

- "Send brownfield code analysis findings JSON to Azure Monitor instrumentation session 'abc-123' after analysis was requested"
- "Continue migration orchestration by submitting analysis payload to session 'abc-123'"
- "Send completed brownfield telemetry analysis for onboarding session 'abc-123'"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Session ID** | Required | The orchestration session identifier. |
| **Findings JSON** | Required | The JSON payload matching the analysis template returned by orchestrator-start. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ✅

## Instrumentation: Send enhancement selection

<!-- @mcpcli monitor instrumentation send-enhancement-select -->

Submit enhancement selection when orchestrator-start returns `enhancement_available`. Sends one or more enhancement keys to continue the onboarding flow.

Example prompts include:

- "Submit enhancement selection keys 'logging,tracing' for Azure Monitor instrumentation session 'abc-123'"
- "Continue instrumentation enhancement flow by sending selected keys 'metrics' to session 'abc-123'"
- "Send chosen enhancement option key list 'logging,metrics,tracing' for onboarding session 'abc-123'"

| Parameter | Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Session ID** | Required | The orchestration session identifier. |
| **Enhancement keys** | Required | Comma-separated list of enhancement keys from the enhancement options. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ✅

## Workbooks: List workbooks

<!-- @mcpcli workbooks list -->

Search Azure Workbooks using Resource Graph for fast metadata queries. This tool helps you discover, filter, and count workbooks across different scopes.

It returns workbook metadata, including `id`, `name`, `location`, `category`, and timestamps. By default, it doesn't return full workbook content (`serializedData`) — use the show tool for that, or set `Output format` to `full`.

By default, the search targets workbooks in your current Azure context (tenant/subscription). You can use `Resource group` to explicitly specify your search scope. The tool returns the server-side total count by default. The maximum results returned is 50, with a maximum limit of 1000; adjust this with `Max results`. Choose `Output format` as `summary` for minimal tokens or `full` for complete `serializedData` output.

<!-- Required parameters: 0 -  -->

Example prompts include:

- "Show me all workbooks in resource group 'monitoring-rg'."
- "List the shared workbooks in resource group 'prod-rg'."
- "What workbooks were modified after 2024-01-15 in resource group 'analytics-rg'?"

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Resource group** | Optional | The name of the Azure resource group to scope the search. |
| **Category** | Optional | Filter workbooks by category (for example, `workbook`, `sentinel`, `TSG`). If not specified, all categories are returned. |
| **Include total count** | Optional | Include the total count of all matching workbooks in the response (default: true). |
| **Kind** | Optional | Filter workbooks by kind (for example, `shared`, `user`). If not specified, all kinds are returned. |
| **Max results** | Optional | Maximum number of results to return (default: 50, max: 1000). |
| **Modified after** | Optional | Filter workbooks modified after this date (ISO 8601 format, for example, `2024-01-15`). |
| **Name contains** | Optional | Filter workbooks where the display name contains this text (case-insensitive). |
| **Output format** | Optional | Output format: `summary` (ID and name only, minimal tokens), `standard` (metadata without content, default), `full` (includes `serializedData`). |
| **Source ID** | Optional | Filter workbooks by source resource ID (for example, `/subscriptions/abc123/resourceGroups/prod/providers/Microsoft.Insights/components/myapp`). If not specified, all workbooks are returned. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Workbooks: Show workbook details

<!-- @mcpcli workbooks show -->

Retrieve full workbook details via the Azure Resource Manager (ARM) API, including the `serializedData` content. This command lets you get the complete workbook definition, including the visualization JSON.

It returns full workbook properties, `serializedData`, tags, and `ETag`. You can provide multiple `Workbook IDs` for batch operations. The command reports partial failures for individual workbooks. For better performance, use the list tool to discover workbooks first, then use show for specific workbooks.

<!-- Required parameters: 1 - 'Workbook IDs' -->

Example prompts include:

- "Show me the details of the workbook with resource ID '/subscriptions/abc123/resourceGroups/monitoring/providers/Microsoft.Insights/workbooks/a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1'."
- "Get the full definition of the workbook '/subscriptions/xyz789/resourceGroups/prod-rg/providers/Microsoft.Insights/workbooks/b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2'."

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Workbook IDs** | Required | The Azure resource IDs of the workbooks to retrieve. Supports multiple values for batch operations. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Workbooks: Create workbook

<!-- @mcpcli workbooks create -->

Create a new workbook in the specified resource group and subscription. You can set the display name and the serialized JSON content for the workbook. This command returns the created workbook information upon successful completion.

<!-- Required parameters: 3 - 'Display name', 'Resource group', 'Serialized content' -->

Example prompts include:

- "Create a new workbook named 'Performance Dashboard' in resource group 'monitoring-rg' with the serialized content for a basic notebook."
- "Create a workbook called 'Infrastructure Overview' in resource group 'prod-rg' with content showing VM metrics."

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Display name** | Required | The display name of the workbook. |
| **Resource group** | Required | The name of the Azure resource group. |
| **Serialized content** | Required | The serialized JSON content of the workbook. |
| **Source ID** | Optional | The linked resource ID for the workbook. By default, this is `azure monitor`. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Workbooks: Update workbook

<!-- @mcpcli workbooks update -->

Update properties of an existing Azure workbook by adding new steps, modifying content, or changing the display name. This action returns the updated workbook details. You need the workbook resource ID and can specify either new serialized content or a new display name.

<!-- Required parameters: 1 - 'Workbook ID' -->

Example prompts include:

- "Update the workbook '/subscriptions/abc123/resourceGroups/monitoring-rg/providers/Microsoft.Insights/workbooks/a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1' with display name 'Monthly Report'."
- "Change the serialized content of workbook '/subscriptions/xyz789/resourceGroups/prod-rg/providers/Microsoft.Insights/workbooks/b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2' to include a new metrics chart."

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Workbook ID** | Required | The Azure resource ID of the workbook to update. |
| **Display name** | Optional | The display name of the workbook. |
| **Serialized content** | Optional | The JSON serialized content of the workbook. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Workbooks: Delete workbooks

<!-- @mcpcli workbooks delete -->

Delete one or more workbooks by their Azure resource IDs. This command performs a soft delete on workbooks, retaining them for 90 days. You can restore them from the Recycle Bin through the Azure portal if needed.

For batch operations, you can provide multiple `Workbook IDs` values. The command reports partial failures per workbook, ensuring that individual failures don't affect the entire batch operation.

To learn more, see [Manage Azure Monitor workbooks](/azure/azure-monitor/visualize/workbooks-manage).

<!-- Required parameters: 1 - 'Workbook IDs' -->

Example prompts include:

- "Delete the workbook with resource ID '/subscriptions/abc123/resourceGroups/monitoring/providers/Microsoft.Insights/workbooks/a0a0a0a0-bbbb-cccc-dddd-e1e1e1e1e1e1'."
- "Remove the workbooks with resource IDs '/subscriptions/xyz789/resourceGroups/prod-rg/providers/Microsoft.Insights/workbooks/b1b1b1b1-cccc-dddd-eeee-f2f2f2f2f2f2' and '/subscriptions/def456/resourceGroups/analytics-rg/providers/Microsoft.Insights/workbooks/c2c2c2c2-dddd-eeee-ffff-a3a3a3a3a3a3'."

| Parameter | Required or optional | Description |
|-----------|-------------|-------------|
| **Workbook IDs** | Required | The Azure resource IDs of the workbooks to delete. Supports multiple values for batch operations. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Monitor](/azure/azure-monitor/overview)
- [Application Insights](/azure/azure-monitor/app/app-insights-overview)
- [Workbooks in Azure Monitor](/azure/azure-monitor/visualize/workbooks-overview)
- [Metrics in Azure Monitor](/azure/azure-monitor/platform/tutorial-metrics)
