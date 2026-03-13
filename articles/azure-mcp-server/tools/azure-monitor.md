---
title: Azure MCP Server tools for Azure Workbooks overview
description: Use Azure MCP Server tools to manage interactive reports and visualization with natural language prompts from your IDE.
ms.service: azure-mcp-server
ms.topic: concept-article
tool_count: 5
mcp-cli.version: 2.0.0-beta.27+b98ca4a635d73244ca470f7e273d3356f256c9eb
---

# Azure MCP Server tools for Azure Workbooks overview

The Azure MCP Server lets you manage interactive reports and visualizations, including creating, deleting, listing, and updating workbooks, with natural language prompts.

Azure Workbooks is a versatile tool for visualizing and analyzing structured data. For more information, see [Azure Workbooks documentation](/azure/monitor/visualize/workbooks-overview/).

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

## Create workbook

<!-- @mcpcli workbooks create -->

Create a new workbook in the specified `resource-group` and subscription. You can set the display name and the serialized JSON content for the workbook. This command returns the created workbook information upon successful completion.

<!-- @mcpcli workbooks create -->
<!-- Required parameters: 3 - 'Display name', 'Resource group', 'Serialized content' -->

Example prompts include:
- "Create a new workbook named <workbook_name> in resource group <resource-group> with content '<serialized-content>'"

| Parameter            | Required or optional | Description                                                               |
|----------------------|----------------------|---------------------------------------------------------------------------|
| **Display name**     | Required             | The display name of the workbook.                                         |
| **Resource group**   | Required             | The name of the Azure resource group. This is a logical container for Azure resources. |
| **Serialized content**| Required             | The serialized JSON content of the workbook.                             |
| **Source ID**        | Optional             | The linked resource ID for the workbook. By default, this is `azure monitor`. |


[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ✅ | Idempotent: ❌ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Delete workbook

<!-- @mcpcli workbooks delete -->

Delete one or more workbooks by their Azure resource IDs. This command performs a soft delete on workbooks, retaining them for 90 days. You can restore them from the Recycle Bin through the Azure Portal if needed.

For batch operations, you can accept multiple `workbook-ids` values. The command reports partial failures per workbook, ensuring that individual failures do not affect the entire batch operation.

To learn more, visit: [Manage Azure Monitor workbooks](https://learn.microsoft.com/azure/azure-monitor/visualize/workbooks-manage)

<!-- @mcpcli workbooks delete -->
<!-- Required parameters: 1 - 'Workbook IDs' -->

Example prompts include:
- "Delete the workbooks with resource IDs `workbook_resource_id_1` and `workbook_resource_id_2`"

| Parameter      | Required or optional | Description |
|----------------|----------------------|-------------|
| **Workbook IDs** | Required            | The Azure Resource IDs of the workbooks to operate on (supports multiple values for batch operations). |


[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Get workbook list

<!-- @mcpcli workbooks list -->

Search Azure Workbooks using Resource Graph for fast metadata queries. This tool helps you discover, filter, and count workbooks across different scopes.

It returns workbook metadata, including `id`, `name`, `location`, `category`, and timestamps. By default, it does not return full workbook content (`serializedData`) — use `show` for that or set `output format` to `full`.

By default, the search targets workbooks in your current Azure context (tenant/subscription). You can use `subscription` and `resource group` to explicitly specify your search scope. The tool returns the server-side total count by default, not just the returned items. The maximum results returned is 50, with a maximum limit of 1000; adjust this with `max results`. Choose `output format` as `summary` for minimal tokens or `full` for complete `serializedData` output.

Apply the following filters to refine your search: `name contains`, `category`, `kind`, `source ID`, and `modified after` for semantic filtering.

<!-- @mcpcli workbooks list -->
<!-- Required parameters: 0 -  -->

Example prompts include:
- "Show me all workbooks in resource group 'my-rg'"
- "What are the workbooks available in resource group 'my-rg'?"

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Category** |  Optional | Filter workbooks by category (for example, `workbook`, `sentinel`, `TSG`). If not specified, all categories will be returned. |
| **Include total count** |  Optional | Include the total count of all matching workbooks in the response (default: true). |
| **Kind** |  Optional | Filter workbooks by kind (for example, `shared`, `user`). If not specified, all kinds will be returned. |
| **Max results** |  Optional | Maximum number of results to return (default: 50, max: 1000). |
| **Modified after** |  Optional | Filter workbooks modified after this date (ISO 8601 format, for example, `2024-01-15`). |
| **Name contains** |  Optional | Filter workbooks where the display name contains this text (case-insensitive). |
| **Output format** |  Optional | Output format: `summary` (ID and name only, minimal tokens), `standard` (metadata without content, default), `full` (includes `serializedData`). |
| **Source ID** |  Optional | Filter workbooks by source resource ID (for example, Application Insights resource, Log Analytics workspace). If not specified, all workbooks will be returned. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Get workbook details

<!-- @mcpcli workbooks show -->

Retrieve full workbook details via the Azure Resource Manager (ARM) API, including the serializedData content.

This command lets you get the complete workbook definition, including the visualization JSON. It returns full workbook properties, `serializedData`, tags, and `ETag`.

You can provide multiple `workbook IDs` for batch operations. The command reports partial failures for individual workbooks. For better performance, use the `list` command to discover workbooks first, then use `show` for specific workbooks.

<!-- @mcpcli workbooks show -->
<!-- Required parameters: 1 - 'Workbook IDs' -->

Example prompts include:
- "Retrieve details for the workbook with resource ID `<workbook_resource_id>`"
- "Get the full definition of the workbook with resource ID `<workbook_resource_id>`"

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Workbook IDs** |  Required | The Azure Resource IDs of the workbooks you want to operate on. This parameter supports multiple values for batch operations. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Update workbook

<!-- @mcpcli workbooks update -->

Updates properties of an existing Azure Workbook by adding new steps, modifying content, or changing the display name. This action returns the updated workbook details. You need the workbook resource ID and can specify either new serialized content or a new display name.

<!-- @mcpcli workbooks update -->
<!-- Required parameters: 1 - 'Workbook ID' -->

Example prompts include:
- "Update the workbook `workbook_resource_id` with a new display name 'Monthly Report'"

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Workbook ID** |  Required | The Azure Resource ID of the workbook to retrieve. |
| **Display name** |  Optional | The display name of the workbook. |
| **Serialized content** |  Optional | The JSON serialized content/data of the workbook. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ✅ | Idempotent: ✅ | Open World: ❌ | Read Only: ❌ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Monitor workbooks documentation](/azure/azure-monitor/visualize/workbooks-overview)