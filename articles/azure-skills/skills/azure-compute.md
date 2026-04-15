---
title: Azure skill for compute
description: Azure VM and Virtual machine scale set (VMSS) router for recommendations, pricing, autoscale, orchestration, and connectivity troubleshooting.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
ms.custom: skill-version-2.1.0
---

# Azure skill for compute

Azure virtual machine (VM) and Virtual machine scale set (VMSS) router for recommendations, pricing, autoscale, orchestration, and connectivity troubleshooting.

**Skill:** `azure-compute` | [Source code](https://github.com/microsoft/azure-skills/blob/main/skills/azure-compute/SKILL.md)

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Azure VM and Virtual machine scale set (VMSS) router for recommendations, pricing, autoscale, orchestration, and connectivity troubleshooting.

## Prerequisites

- **Azure subscription**: [Create a free account](https://azure.microsoft.com/free/) if you don't have one.
- **[GitHub Copilot for Azure](/azure/developer/github-copilot-azure/get-started)**: With the Azure extension enabled.
- **Azure CLI** (v2.60.0+): [Install](/cli/azure/install-azure-cli) and sign in with `az login`.

## When to use this skill

Use this skill when you need to:

- Create and manage Azure virtual machines (VMs) and virtual machine scale sets (VMSS).
- Configure autoscaling for virtual machine scale sets.
- Select appropriate VM SKUs for your workload (server, web hosting, burstable compute, or lightweight).
- Optimize VM selection for different workloads, including development/test scenarios and back-end services.
- Work with autoscale, load balancer, Flexible orchestration, and Uniform orchestration
- Work with cost estimate, Linux, black screen, and reset password
- Configure remote desktop connectivity (RDP port 3389) for Windows virtual machines.

## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [Skill source code](https://github.com/microsoft/azure-skills/blob/main/skills/azure-compute/SKILL.md)
