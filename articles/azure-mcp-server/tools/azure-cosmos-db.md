---
title: Azure Cosmos DB Tools 
description: Learn how to use the Azure MCP Server with Azure Cosmos DB to manage NoSQL databases, containers, and query data using natural language prompts.
keywords: azure mcp server, azmcp, cosmos db
author: diberry
ms.author: diberry
ms.date: 07/03/2026
content_well_notification: 
  - AI-contribution
ai-usage: ai-assisted
ms.topic: reference
ms.custom: build-2025
--- 
# Azure Cosmos DB tools for the Azure MCP Server

The Azure MCP Server allows you to manage Azure resources, including Cosmos DB accounts, databases, and containers with natural language prompts. Query and manage your NoSQL databases using simple conversational commands.

[Azure Cosmos DB](/azure/cosmos-db/introduction) is a fully managed NoSQL database service for modern app development. Azure Cosmos DB offers single-digit millisecond response times, automatic and instant scalability, along with guaranteed speed at any scale.

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

> [!NOTE]
> In Azure MCP Server v2.0.0-beta.23, the separate `cosmos_account_list`, `cosmos_database_list`, and `cosmos_database_container_list` commands were consolidated into a single `cosmos list` command. Use `cosmos list` with appropriate parameters to list accounts, databases, or containers.

## Get Cosmos DB resources list

<!-- @mcpcli cosmos list -->

List Azure Cosmos DB accounts, databases, or containers. By default, this command returns all accounts in your subscription. Specify `--account` to list databases in that account, or combine `--account` and `--database` to list containers in a specific database.

<!-- @mcpcli cosmos list -->
<!-- Required parameters: 0 -  -->

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

## Get container item query

<!-- @mcpcli cosmos database container item query -->

List items from a Cosmos DB container by specifying the account name, database name, and container name. Optionally, you can provide a custom SQL query to filter results.

<!-- @mcpcli cosmos database container item query -->
<!-- Required parameters: 3 - '--account', '--database', '--container' -->

Example prompts include:
- "Show me the items in the container `my-container` from database `my-database` for the Cosmos DB account `my-cosmos-account`."

| Parameter  | Required or optional | Description |
|------------|----------------------|-------------|
| **Account** | Required | The name of the Cosmos DB account to query. |
| **Container** | Required | The name of the container to query. |
| **Database** | Required | The name of the database to query. |
| **Query** | Optional | SQL query to execute against the container, using Cosmos DB SQL syntax. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):
Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Cosmos DB documentation](/azure/cosmos-db/)
