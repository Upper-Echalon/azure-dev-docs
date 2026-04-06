---
title: Azure skill for App Insights instrumentation
description: Guidance for instrumenting webapps with Azure Application Insights. Provides telemetry patterns, SDK setup, and configuration references.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for App Insights instrumentation

Guidance for instrumenting webapps with Azure Application Insights. Provides telemetry patterns, SDK setup, and configuration references.

**Skill:** `appinsights-instrumentation` | [Source code](https://github.com/microsoft/azure-skills/tree/main/skills/appinsights-instrumentation)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **PowerShell** (v7.4+)—Install: `winget install Microsoft.PowerShell`
- **Azure CLI with Bicep** (v2.60.0+)—Install: `az bicep install`

## When to use this skill

Use this skill when you need to:

- Work with App Insights SDK, telemetry patterns, Application Insights guidance, and instrumentation examples
- Work with Apm best practices

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Guidance for instrumenting webapps with Azure Application Insights. Provides telemetry patterns, SDK setup, and configuration references.




## Example prompts

Try these prompts with GitHub Copilot to activate this skill:

- "Instrument my webapp to send telemetry to App Insights"
- "How do I instrument my app with Azure App Insights?"
- "Add AppInsights instrumentation to my web application"
- "Add App Insights instrumentation to my Node.js app"
- "Configure Application Insights for my Python webapp"
- "Set up telemetry monitoring in Azure"
- "Instrument my application to send data to App Insights"
- "Add observability to my Azure web application"
- "How to enable App Insights autoinstrumentation?"
- "Configure telemetry for my Azure App Service"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
