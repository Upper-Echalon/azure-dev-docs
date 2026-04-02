---
title: azure-ai
description: 
ms.topic: reference
ms.date: 2026-04-02
author: diberry
ms.author: diberry
ms.service: azure-mcp-server
---

# azure-AI



**Skill:** `azure-AI` | [Source code](https://github.com/microsoft/GitHub-Copilot-for-Azure/tree/main/plugin/skills/azure-AI)

## Prerequisites

- **Azure authentication** — Sign in with `az login` or use a service principal.
- **Azure subscription** — An active Azure subscription is required.
- **GitHub Copilot** — GitHub Copilot with the Azure extension enabled.

### Required tools

- **GitHub Copilot**
- **Azure CLI** (v2.60.0+) — Install: `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

## When to use this skill

Use the **azure-AI** skill when you need to:

- AI Search
- query search
- vector search
- hybrid search
- semantic search
- speech-to-text
- text-to-speech
- transcribe
- convert text to speech

### When NOT to use this skill

Don't use this skill for:

- What is the weather today?
- Help me write a poem
- Explain quantum computing

## What it provides

The azure-AI skill provides GitHub Copilot with specialized knowledge about azure-AI services and workflows in Azure.

### Azure services knowledge

| Service | When to use |
|---------|------------|
| AI Search | Full-text, vector, hybrid search |
| Speech | Speech-to-text, text-to-speech |
| OpenAI | GPT models, embeddings, DALL-E |
| Document Intelligence | Form extraction, OCR |






## Related content

- [Azure Model Context Protocol (MCP) Server overview](/azure/copilot/azure-mcp-server)
- [GitHub Copilot for Azure documentation](/azure/copilot/)
