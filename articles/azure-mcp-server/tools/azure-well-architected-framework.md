---
title: Azure MCP Server tools for Azure Well-Architected Framework
description: Use Azure MCP Server tools to manage Azure Well-Architected Framework assessments and recommendations for cloud workloads with natural language prompts from your IDE.
ms.service: azure-mcp-server
ms.topic: concept-article
tool_count: 1
mcp-cli.version: 2.0.0-beta.31
---

# Azure MCP Server tools for Azure Well-Architected Framework

The Azure MCP Server lets you manage Azure Well-Architected Framework assessments, run workload reviews, view improvement recommendations, and track remediation plans with natural language prompts.

Azure Well-Architected Framework is a set of best practices and guidance that helps you design, build, and operate secure, high-performing, resilient, and cost-efficient cloud workloads; for more information, see [Azure Well-Architected Framework documentation](https://learn.microsoft.com/azure/architecture/framework/).

[!INCLUDE [tip-about-params](../includes/tools/parameter-consideration.md)]

## get

<!-- @mcpcli wellarchitectedframework serviceguide get -->

This tool retrieves Azure Well-Architected Framework guidance for a specific Azure service. If you don't specify a `service`, the tool lists all supported services. When you provide a `service`, it returns architectural best practices, design patterns, and recommendations across the five pillars: reliability, security, cost optimization, operational excellence, and performance efficiency.

Examples:
- "Show guidance for 'Cosmos DB'"
- "List all supported services"

<!-- Required parameters: 0 -  -->

Example prompts include:

- "Show all services with Well-Architected Framework guidance."
- "Which services have architectural guidance under the Well-Architected Framework?"
- "Retrieve Well-Architected Framework guidance for service 'App Service'."
- "What's the waf guidance for service 'Virtual Machine'?"
- "Show the architectural guidance for 'Azure Cosmos DB'."

| Parameter |  Required or optional | Description |
|-----------------------|----------------------|-------------|
| **Service** |  Optional | A single Azure service name. The value is case-insensitive and accepts hyphens, underscores, and spaces. If the name contains spaces, enclose it in double quotes. Examples: `cosmos-db`, `Cosmos_DB`, `Cosmos DB`, `cosmosdb`, `cosmos-database`. |

[Tool annotation hints](index.md#tool-annotations-for-azure-mcp-server):

Destructive: ❌ | Idempotent: ✅ | Open World: ❌ | Read Only: ✅ | Secret: ❌ | Local Required: ❌

## Related content

- [What are the Azure MCP Server tools?](index.md)
- [Get started using Azure MCP Server](../get-started.md)
- [Azure Well-Architected Framework documentation](/azure/architecture/framework/)