---
title: Azure skill for AI Services
description: Azure AI Services including AI Search, Speech, OpenAI, and Document Intelligence.
ms.topic: reference
ms.date: 4/2/2026
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# Azure skill for AI Services



**Skill:** `azure-ai` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-AI)

## Prerequisites

- **Azure authentication**—Sign in with `az login` or use a service principal.
- **Azure subscription**—An active Azure subscription is required.
- **GitHub Copilot**—GitHub Copilot with the Azure extension enabled.
- **Azure CLI** (v2.60.0+)—Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash` (Azure Command-Line Interface)

## When to use this skill

Use this skill when you need to:

- Query and manage Azure AI Search resources.
- Perform full-text, vector, hybrid, and semantic search queries.
- Execute vector, hybrid, and semantic search queries.
- Convert speech to text and text to speech using Azure Cognitive Services.

## What it provides

This skill provides GitHub Copilot with specialized knowledge about Azure AI Services services and workflows in Azure.

### Azure services knowledge

| Service | When to use |
|---------|------------|
| AI Search | Full-text, vector, hybrid search |
| Speech | Speech-to-text, text-to-speech |
| OpenAI | GPT models, embeddings, DALL-E |
| Document Intelligence | Form extraction, OCR |





## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/developer/azure-mcp-server/overview)
- [GitHub Copilot for Azure documentation](/azure/developer/github-copilot-azure/introduction)
