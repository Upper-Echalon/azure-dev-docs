---
title: Azure skill for storage
description: Azure Storage Services including Blob Storage, File Shares, Queue Storage, Table Storage, and Data Lake. Provides object storage, SMB file shares, async messaging, NoSQL key-value, and big data analytics capabilities. Includes access tiers (hot, cool, archive) and lifecycle management.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for storage

Azure Storage Services including Blob Storage, File Shares, Queue Storage, Table Storage, and Data Lake. Provides object storage, SMB file shares, async messaging, NoSQL key-value, and big data analytics capabilities. Includes access tiers (hot, cool, archive) and lifecycle management.

**Skill:** `azure-storage` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-storage)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`
- **Azure Storage account**—Storage account for blob, file, queue, or table data
- **Azure Cosmos DB account**—Cosmos DB account for NoSQL data

## When to use this skill

Use this skill when you need to:

- Work with blob storage, file shares, queue storage, and table storage
- Work with data lake
- Upload files in Azure
- Work with download blobs, storage accounts, access tiers, and lifecycle management

## What it provides

This skill provides GitHub Copilot with specialized knowledge. Azure Storage Services including Blob Storage, File Shares, Queue Storage, Table Storage, and Data Lake. Provides object storage, SMB file shares, async messaging, NoSQL key-value, and big data analytics capabilities. Includes access tiers (hot, cool, archive) and lifecycle management.

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
