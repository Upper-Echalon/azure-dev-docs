---
title: azure-storage
description: Azure Storage Services including Blob Storage, File Shares, Queue Storage, Table Storage, and Data Lake. Provides object storage, SMB file shares, async messaging, NoSQL key-value, and big data analytics capabilities. Includes access tiers (hot, cool, archive) and lifecycle management.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-storage

Azure Storage Services including Blob Storage, File Shares, Queue Storage, Table Storage, and Data Lake. Provides object storage, SMB file shares, async messaging, NoSQL key-value, and big data analytics capabilities. Includes access tiers (hot, cool, archive) and lifecycle management.

**Skill:** `azure-storage` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-storage)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **`azure-storage`** skill when you need to:

- Work with blob storage, file shares, queue storage, and table storage
- Work with data lake
- Upload files
- Work with download blobs, storage accounts, access tiers, and lifecycle management

### When NOT to use this skill

Don't use this skill for:

- Work with SQL databases and Cosmos DB (use `azure-prepare`)
- Messaging with Event Hubs or Service Bus (use `azure-messaging`)

## What it provides

The `azure-storage` skill provides GitHub Copilot with specialized knowledge. Azure Storage Services including Blob Storage, File Shares, Queue Storage, Table Storage, and Data Lake. Provides object storage, SMB file shares, async messaging, NoSQL key-value, and big data analytics capabilities. Includes access tiers (hot, cool, archive) and lifecycle management.

### Azure services knowledge

| Service | When to use |
|---------|------------|
| Blob Storage | Objects, files, backups, static content |
| File Shares | SMB file shares, lift-and-shift |
| Queue Storage | Async messaging, task queues |
| Table Storage | NoSQL key-value (consider Cosmos DB) |
| Data Lake | Big data analytics, hierarchical namespace |





## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
