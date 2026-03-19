---
title: Azure Cosmos DB Tools 
description: Learn how to use the Azure MCP Server with Azure Cosmos DB to manage NoSQL databases, containers, and query data using natural language prompts.
author: diberry
ms.author: diberry
ms.date: 03/06/2026
content_well_notification: 
  - AI-contribution
ai-usage: ai-assisted
ms.topic: reference
ms.custom: build-2025
tool_count: 2
mcp-cli.version: 2.0.0-beta.24+ef8d0acfa3d468e4a4a3ffe957063f7bfb7fe366
--- 
# Azure MCP Server tools for Azure Cosmos DB overview

The Azure MCP Server lets you manage Azure Cosmos DB, including database creation, resource scaling, and data querying, with natural language prompts.

Azure Cosmos DB is a globally distributed, multi-model database service for any scale. For more information, see [Azure Cosmos DB documentation](/azure/cosmos-db/).

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

## Get Cosmos database list

<!-- @mcpcli cosmos list -->

List Azure Cosmos DB accounts, databases, or containers. By default, this command returns all accounts in the subscription. You can specify the **Account** parameter to list databases within a specific account, or use both **Account** and **Database** to list containers in a specific database.

<!-- @mcpcli cosmos list -->
<!-- Required parameters: 0 -  -->

Example prompts include:
- "List all Cosmos DB accounts in my subscription"
- "Show me my Cosmos DB accounts"
- "Show me the Cosmos DB accounts in my subscription"
- "List all the databases in the Cosmos DB account `<account>`"
- "Get the databases in the Cosmos DB account `<account>`"
- "List all the containers in the database `<database>` for the Cosmos DB account `<account>`"
- "Show me the containers in the database `<database>` for the Cosmos DB account `<account>`"

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Account** |  Optional | The name of the Cosmos DB account. When not specified, this command lists all accounts in the subscription. Specify this to list databases or combine with **Database** to list containers. |
| **Database** |  Optional | The name of the database. Requires **Account** to be specified. When provided, this command lists containers within the specified database. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Cosmos DB documentation](/azure/cosmos-db/)