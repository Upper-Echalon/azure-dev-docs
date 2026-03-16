---
title: "Azure Skills reference: azure-storage"
description: "Work with Azure Storage services: Blob Storage, File Shares, Queue Storage, Table Storage. Store and retrieve files at scale."
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# azure-storage

## Overview

**Description:** Work with Azure Storage services: Blob Storage, File Shares, Queue Storage, Table Storage.

## Services covered

- **Blob Storage** — Object storage, data lakes, backups
- **File Shares** — SMB file sharing for applications and users
- **Queue Storage** — Asynchronous messaging
- **Table Storage** — NoSQL key-value data

## When to use

- Storing and retrieving files at scale
- Sharing files between systems
- Implementing message queues
- Storing structured data without SQL
- Managing data lifecycle (hot, cool, archive tiers)

## Example prompts

Ask your assistant:
- "Create a storage account for my app"
- "Upload a file to blob storage"
- "Set up a file share"
- "Send a message to a queue"
- "Move old data to cool storage"

## Key MCP tools

- Storage account and container management
- Blob upload, download, and listing
- File share creation and mounting
- Queue message operations
- Access key and SAS token management
- Lifecycle policy configuration

## Related

- [azure-postgres](azure-postgres.md) — Manage PostgreSQL databases
- [azure-kusto](azure-kusto.md) — Large-scale data analytics
- [Azure Skills overview](../overview.md)
