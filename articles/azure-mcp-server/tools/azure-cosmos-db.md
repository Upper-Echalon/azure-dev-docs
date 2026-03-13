---
title: Azure Cosmos DB Tools 
description: Learn how to use the Azure MCP Server with Azure Cosmos DB to manage NoSQL databases, containers, and query data using natural language prompts.
keywords: azure mcp server, azmcp, cosmos db
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
# Azure Cosmos DB tools for the Azure MCP Server overview

The Azure MCP Server allows you to manage Azure resources, including Azure Cosmos DB accounts, databases, and containers with natural language prompts. Query and manage your NoSQL databases using simple conversational commands.

[Azure Cosmos DB](/azure/cosmos-db/introduction) is a fully managed NoSQL database service for modern app development. Azure Cosmos DB offers single-digit millisecond response times, automatic and instant scalability, along with guaranteed speed at any scale.

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

## Get Azure Cosmos DB resources list

<!-- @mcpcli cosmos list -->

List Azure Cosmos DB accounts, databases, or containers. By default, this command returns all accounts in your subscription. 

Example prompts include:

- "List all Azure Cosmos DB accounts in my subscription"
- "Show me my Azure Cosmos DB accounts"
- "Show me the Azure Cosmos DB accounts in my subscription"
- "List all the databases in the Azure Cosmos DB account `<account>`"
- "Show me the databases in the Azure Cosmos DB account `<account>`"
- "List all the containers in the database `<database>` for the Azure Cosmos DB account `<account>`"
- "Show me the containers in the database `<database>` for the Azure Cosmos DB account `<account>`"

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Account** |  Optional | The name of the Azure Cosmos DB account. When not specified, this command lists all accounts in the subscription. Specify this parameter to list databases, or combine with **Database** to list containers. |
| **Database** |  Optional | The name of the database. Requires **Account** to be specified. When provided, this command lists containers within the specified database. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Query Azure Cosmos DB container items

<!-- @mcpcli cosmos database container item query -->

List items from an Azure Cosmos DB container by specifying the account name, database name, and container name. Optionally, you can provide a custom SQL query to filter results.

Example prompts include:

- "Show me the items in the container `my-container` from database `my-database` for the Cosmos DB account `my-cosmos-account`."
- "Show me orders with their related customer information in container 'my-container' in database 'my-database' in Cosmos DB account `my-cosmos-account` where the order total is greater than 100."
- "Count how many orders we have by status in the 'my-container' container in database 'my-database' in Cosmos DB account `my-cosmos-account`"

| Parameter  | Required or optional | Description |
|------------|----------------------|-------------|
| **Account** | Required | The name of the Azure Cosmos DB account to query. |
| **Container** | Required | The name of the container to query. |
| **Database** | Required | The name of the database to query. |
| **Query** | Optional | SQL query to execute against the container, using Azure Cosmos DB SQL syntax. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Cosmos DB documentation](/azure/cosmos-db/)
