---
title: Azure Compliance
description: Run Azure compliance and security audits with azqr plus Key Vault expiration checks. Covers best-practice assessment, resource review, policy/compliance validation, and security posture checks.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure Compliance

Run Azure compliance and security audits with azqr plus Key Vault expiration checks. Covers best-practice assessment, resource review, policy/compliance validation, and security posture checks.

**Skill:** `azure-compliance` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-compliance)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

### Required resources

- **Azure Key Vault** — Key vault for secrets and certificate management

## When to use this skill

Use the **Azure Compliance** skill when you need to:

- Work with compliance scan and security audit
- Before running azqr (compliance cli tool)
- Work with Azure best practices, Key Vault expiration check, expired certificates, and expiring secrets
- Work with orphaned resources and compliance assessment

## What it provides

The Azure Compliance skill provides GitHub Copilot with specialized knowledge. Run Azure compliance and security audits with azqr plus Key Vault expiration checks. Covers best-practice assessment, resource review, policy/compliance validation, and security posture checks.




## Example triggers

Try these prompts with GitHub Copilot to activate this skill:

- "Run azqr to check Azure compliance"
- "Check my Azure subscription for compliance issues"
- "Perform compliance assessment using Azure Quick Review"
- "Assess my Azure resources against best practices"
- "Review my Azure security posture"
- "Run compliance scan on my Azure subscription"
- "Identify orphaned resources in Azure"
- "Find resources that don't comply with best practices"
- "Show me expired certificates in my Key Vault"
- "Check what secrets are expiring in the next 30 days"


## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
