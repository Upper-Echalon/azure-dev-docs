---
title: "Azure Skills reference: azure-resource-lookup"
description: "Find and inspect Azure resources across your subscription. Search resources by name, type, or tag and retrieve detailed configuration."
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# azure-resource-lookup

## Overview

**Description:** Find and inspect Azure resources across your subscription.

## What it does

- Searches for resources by name, type, or tag
- Returns detailed resource properties and configuration
- Filters by resource group or subscription
- Exports resource information

## When to use

- Finding existing resources
- Inspecting resource configuration
- Auditing what's deployed
- Debugging connectivity issues
- Gathering information for troubleshooting

## Example prompts

Ask your assistant:
- "List all my storage accounts"
- "Find all resources tagged with [tag]"
- "Show me details about this resource"
- "What resources are in my resource group?"

## Key MCP tools

- Resource search and filtering
- Resource group listing
- Detailed resource property retrieval
- Tag-based filtering

## Related

- [azure-resource-visualizer](azure-resource-visualizer.md) — Visualize architecture and dependencies
- [azure-diagnostics](azure-diagnostics.md) — Debug and troubleshoot issues
- [azure-observability](azure-observability.md) — Monitoring and alerting
- [Azure Skills overview](../overview.md)
