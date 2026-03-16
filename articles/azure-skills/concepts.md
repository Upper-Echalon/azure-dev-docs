---
title: Key concepts in Azure Skills
description: Understand skills, the prepare-validate-deploy workflow, and how Azure Skills integrate with your development environment.
ms.topic: concept
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# Key concepts in Azure Skills

## What is a skill?

A skill is a capability that your AI assistant can invoke. Each skill represents a high-level Azure workflow or operation. Skills are composable—they work together to solve complex problems.

### Skills vs. tools

- **Tools** (from Azure MCP Server) are low-level operations. Examples: "Get storage account details," "List subscriptions," "Run KQL query."
- **Skills** are high-level workflows built on top of tools. Examples: "Prepare an application for Azure deployment," "Validate a Bicep template," "Deploy infrastructure."

When you ask your AI assistant to "prepare my app for Azure," it invokes the `azure-prepare` skill, which internally uses dozens of tools to analyze your codebase, research services, and generate a deployment plan.

## The prepare → validate → deploy workflow

Azure Skills enforce a three-step workflow to ensure safe, auditable deployments.

### Step 1: Prepare (azure-prepare skill)

**Purpose:** Plan the deployment without making any changes to Azure.

**What happens:**
1. Analyzes your application and codebase
2. Determines what Azure services you need
3. Creates `.azure/plan.md` with the deployment strategy
4. Generates infrastructure-as-code (Bicep, Terraform, or Azure CLI scripts)
5. **Waits for your approval** before proceeding

**Output:** `.azure/plan.md` file with status `Approved`

**When to use:** At the start of any Azure deployment work. This is the mandatory entry point.

### Step 2: Validate (azure-validate skill)

**Purpose:** Verify that your deployment plan is correct before you invest resources in Azure.

**What happens:**
1. Loads your plan from `.azure/plan.md`
2. Runs validation checks (infrastructure syntax, permissions, regional availability)
3. Records proof of validation (commands run, timestamps, results)
4. Reports any issues
5. Updates plan status to `Validated` only after all checks pass

**Prerequisite:** Your plan must have status `Approved` (from azure-prepare)

**Output:** `.azure/plan.md` updated with status `Validated` and validation proof

**When to use:** After reviewing and approving the prepare plan. Before deployment.

### Step 3: Deploy (azure-deploy skill)

**Purpose:** Execute the deployment to Azure.

**What happens:**
1. Loads your plan and validates it has status `Validated`
2. Runs the deployment (provisioning infrastructure, configuring services, deploying applications)
3. Verifies deployment success
4. Provides access endpoints

**Prerequisites:** 
- `.azure/plan.md` exists
- Plan status is `Validated` (only azure-validate can set this)

**Output:** Deployed Azure resources, application endpoints

**When to use:** When your plan is approved and validated. For deploying to Azure after any update to your plan.

## How skills use the plan file

The `.azure/plan.md` file is the contract between you and the Azure Skills.

**Plan structure:**

```markdown
# Project Information
- Application name
- Deployment mode (NEW, MODIFY, or MODERNIZE)

# Requirements
- Classification (web app, API, data pipeline, etc.)
- Scale (small, medium, large)
- Budget

# Components
- Technologies identified (Node.js, Python, databases, etc.)
- Dependencies

# Recipe
- Type (AZD, Bicep, Terraform, or Azure CLI)

# Architecture
- Azure services selected
- Component-to-service mapping

# Implementation Plan
- Step-by-step deployment tasks

# Validation Proof
- Commands executed by azure-validate
- Results and timestamps

# Status
NEW → APPROVED → VALIDATED → DEPLOYED
```

**Why the plan matters:**
- It's auditable—you can review exactly what will be deployed before it happens
- It's authoritative—azure-validate only validates plans, and azure-deploy only deploys validated plans
- It's safe—destructive operations require explicit user approval
- It's traceable—every decision and step is documented

## Skill categories

Azure Skills are organized into five categories based on function:

### Development lifecycle skills
These skills manage the core Azure deployment workflow.
- **azure-prepare** — Plan deployment (entry point)
- **azure-validate** — Validate before deployment
- **azure-deploy** — Execute deployment

### AI & Machine Learning skills
Use these to integrate AI services into your application.
- **azure-ai** — Azure AI Search, Speech, OpenAI, Document Intelligence
- **azure-aigateway** — AI Gateway service management
- **microsoft-foundry** — Deploy AI models, build RAG applications, create and evaluate AI agents

### Data & Analytics skills
Use these for data processing, storage, and analysis.
- **azure-postgres** — Azure Database for PostgreSQL operations
- **azure-kusto** — Azure Data Explorer and KQL queries
- **azure-storage** — Azure Storage (Blob, File Shares, Tables)

### Security & Identity skills
Use these to implement access control and compliance.
- **azure-rbac** — Assign least-privilege Azure RBAC roles
- **azure-compliance** — Check compliance requirements and configurations
- **entra-app-registration** — Manage Microsoft Entra app registrations

### Infrastructure & Monitoring skills
Use these to manage resources, troubleshoot issues, and optimize costs.
- **azure-resource-lookup** — Find and inspect Azure resources
- **azure-resource-visualizer** — Visualize your Azure resource architecture
- **azure-diagnostics** — Debug production issues and troubleshoot problems
- **azure-observability** — Set up monitoring, logging, and alerts
- **appinsights-instrumentation** — Configure Application Insights telemetry
- **azure-cost-optimization** — Get cost optimization recommendations

## How skills connect to Azure

Azure Skills communicate with Azure through the **Azure MCP Server**. This server:

- Connects to your Azure account (using Azure CLI login, environment variables, or managed identity)
- Exposes tools for 40+ Azure services
- Translates skill requests into Azure API calls
- Handles authentication and error handling

When your AI assistant invokes a skill, it:

1. Receives the skill request
2. Uses the skill's logic to determine what to do
3. Calls Azure MCP Server tools as needed
4. Processes results and generates output (plans, resources, recommendations)
5. Returns results to you

## Recipe types

The prepare skill creates a "recipe"—a deployment strategy—based on your application type. Each recipe defines how your app will be deployed.

| Recipe | When to use |
|--------|------------|
| **AZD (Azure Developer CLI)** | Recommended for most applications. Single tool orchestrates infrastructure and application deployment. |
| **Bicep** | You need fine-grained control over infrastructure. Creates `.bicep` template files. |
| **Terraform** | Your organization uses Terraform for multi-cloud deployments. Creates `.tf` files. |
| **Azure CLI** | You prefer manual CLI commands for each step. Generates `.azcli` script files. |

The prepare skill selects the best recipe for your application. You can override this during planning.

## Subscription and location selection

During the prepare phase, Azure Skills confirm with you:
- **Subscription:** Which Azure subscription to deploy to (shown by name and ID)
- **Location:** Which Azure region to use (only showing regions that support all required services)

These choices are recorded in your plan and used consistently throughout validation and deployment.

## Learn more

- [Install and configure Azure Skills](install.md) — Set up Azure Skills in your environment
- [Get started with Azure Skills](quickstart.md) — Walk through a complete prepare-validate-deploy workflow
- [Azure Skills reference](skills-reference.md) — Details on all 18 skills
