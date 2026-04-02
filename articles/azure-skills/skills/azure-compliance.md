---
title: azure-compliance
description: Run Azure compliance and security audits with azqr plus Key Vault expiration checks. Covers best-practice assessment, resource review, policy/compliance validation, and security posture checks.
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-compliance

Run Azure compliance and security audits with azqr plus Key Vault expiration checks. Covers best-practice assessment, resource review, policy/compliance validation, and security posture checks.

**Skill:** `azure-compliance` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-compliance)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-compliance`** skill when you need to:

- compliance scan
- security audit
- Before running azqr (compliance cli tool)
- Azure best practices
- Key Vault expiration check
- expired certificates
- expiring secrets
- orphaned resources
- compliance assessment

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The `azure-compliance` skill provides GitHub Copilot with specialized knowledge. Run Azure compliance and security audits with azqr plus Key Vault expiration checks. Covers best-practice assessment, resource review, policy/compliance validation, and security posture checks.





## Example prompts

Try these prompts with GitHub Copilot:

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

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
