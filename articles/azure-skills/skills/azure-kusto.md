---
title: Azure skill for Kusto (Data Explorer)
description: This skill queries and analyzes data in Azure Data Explorer (also called Kusto or ADX) using Kusto Query Language (KQL) to support log analytics, telemetry monitoring, and time-series analysis.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for Kusto (Data Explorer)

This skill queries and analyzes data in Azure Data Explorer (also called Kusto or ADX) using Kusto Query Language (KQL) to support log analytics, telemetry monitoring, and time-series analysis.

**Skill:** `azure-kusto` | [Source code](https://github.com/microsoft/azure-skills/tree/main/skills/azure-kusto)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use this skill when you need to:

- Write KQL queries to analyze logs, telemetry data, and time-series information in Azure Data Explorer clusters.
- Perform log analytics, analyze time-series data from IoT devices, and detect anomalies.

## What it provides

This skill provides GitHub Copilot with specialized knowledge. This skill queries and analyzes data in Azure Data Explorer (also called Kusto or ADX) using Kusto Query Language (KQL) to support log analytics, telemetry monitoring, and time-series analysis.

## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
