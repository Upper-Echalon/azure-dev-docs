---
title: Azure skill for enterprise infrastructure planning
description: Architect and provision enterprise Azure infrastructure from workload descriptions. For cloud architects and platform engineers planning networking, identity, security, compliance, and multi-resource topologies with waf alignment. Generates Bicep or Terraform directly (no azd).
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for enterprise infrastructure planning

Architect and provision enterprise Azure infrastructure from workload descriptions. For cloud architects and platform engineers planning networking, identity, security, compliance, and multi-resource topologies with waf alignment. Generates Bicep or Terraform directly (no `azd`).

**Skill:** `azure-enterprise-infra-planner` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-enterprise-infra-planner)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use this skill when you need to:

- Plan Azure infrastructure
- Work with architect Azure landing zone
- Design hub-spoke network in Azure
- Plan multi-region Dr topology
- Set up VNets firewalls and private endpoints
- Subscription-scope Bicep deployment'. Prefer `azure-prepare` For app-centric workflows

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Architect and provision enterprise Azure infrastructure from workload descriptions. For cloud architects and platform engineers planning networking, identity, security, compliance, and multi-resource topologies with waf alignment. Generates Bicep or Terraform directly (no `azd`).




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Deploy a geo-redundant backup solution for on-premises SQL servers using Azure Backup, configure encryption-at-rest, and automate monthly DR tests."
- "Deploy 3-tier architecture with hardened OS images, virtual machine (VM) backups scheduled daily, and application-level redundancy for the business logic tier."
- "Configure a site recovery plan for disaster failover from East to West Azure region, replicate major VM workloads, and automate DNS failbacks."
- "Provision a jumpbox VM for secure management, establish NSGs for each tier, and connect tiers using internal Azure Load Balancer."
- "Spin up Linux VMs for each tier using Terraform, automate patch management through Azure Automation, and log traffic between subnets for compliance."
- "Deploy three distinct VM scale sets for a legacy app, route incoming HTTP/S through Application Gateway with Web Application Firewall (WAF), and encrypt all data disks."
- "Set up Azure Backup for critical VM workloads, create a long-term retention policy for compliance, and test backup restores quarterly."
- "Deploy disaster recovery for VMware VMs using Azure Site Recovery, configure runbooks for smooth failover, and maintain compliance audit trails."


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
