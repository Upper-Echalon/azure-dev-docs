---
title: Azure Skills reference
description: Complete reference of all 18 Azure Skills with descriptions and use cases.
ms.topic: reference
ms.date: 03/16/2026
author: diberry
ms.author: diberry
ms.service: azure-ai-dev-tools
---

# Azure Skills reference

This reference documents all 18 Azure Skills available in the Azure Skills plugin. Each skill provides a specific capability for managing Azure resources, deploying applications, and monitoring services.

## Development lifecycle skills

These core skills manage the prepare-validate-deploy workflow. Use them in order for safe, auditable deployments.

### azure-prepare

**Description:** Plan your Azure deployment without making changes.

**What it does:**
- Analyzes your application and codebase
- Identifies required Azure services
- Creates `.azure/plan.md` with deployment strategy
- Generates infrastructure-as-code (Bicep, Terraform, or Azure CLI)
- Waits for your approval before proceeding

**Use when:**
- Starting any Azure deployment work
- Adding new components to an existing app
- Modernizing or migrating applications to Azure
- Preparing infrastructure for a new service

**Ask your assistant:**
- "Prepare my app for Azure deployment"
- "Create a deployment plan for my web app"
- "Modernize my legacy app to Azure"

**Output:**
- `.azure/plan.md` (deployment plan)
- Infrastructure-as-code files
- status: `Approved`

### azure-validate

**Description:** Validate your deployment plan before deploying to Azure.

**What it does:**
- Loads your plan from `.azure/plan.md`
- Runs configuration checks and syntax validation
- Verifies Azure permissions and regional availability
- Records validation proof
- Updates plan status to `Validated` (required before deployment)

**Use when:**
- After reviewing and approving the prepare plan
- Before deploying to ensure no issues
- After significant changes to your application

**Ask your assistant:**
- "Validate this deployment plan"
- "Check if my app is ready to deploy"
- "Run preflight checks before deployment"

**Prerequisite:** Plan must have status `Approved` (from azure-prepare)

**Output:**
- `.azure/plan.md` updated with status: `Validated`
- Validation proof section populated
- Command output and results

### azure-deploy

**Description:** Execute deployment of your application to Azure.

**What it does:**
- Verifies plan has status `Validated`
- Provisions Azure resources (storage, compute, services)
- Deploys application code
- Configures application settings and connections
- Provides access endpoints and credentials

**Use when:**
- Plan is approved and validated
- Deploying to production
- Redeploying after application updates
- Deploying to a different environment

**Ask your assistant:**
- "Deploy my app to Azure"
- "Run the deployment"
- "Push my app to production"

**Prerequisites:**
- `.azure/plan.md` exists
- Plan status: `Validated` (only azure-validate can set this)

**Output:**
- Deployed Azure resources
- Application URLs
- Storage credentials and connection strings
- Monitoring access (Application Insights)

---

## AI & Machine Learning skills

Use these skills to integrate AI services into your application.

### azure-ai

**Description:** Work with Azure AI services: AI Search, Speech, OpenAI, Document Intelligence.

**Services covered:**
- Azure AI Search (full-text, semantic, vector search)
- Azure Speech Services (speech-to-text, text-to-speech, translation)
- OpenAI models
- Document Intelligence (OCR, forms, tables)

**Use when:**
- Building search functionality
- Adding speech capabilities to your app
- Processing documents or images
- Integrating LLM APIs
- Implementing semantic search

**Ask your assistant:**
- "Add search capability to my app"
- "Configure Azure OpenAI for my application"
- "Set up speech-to-text in my app"
- "Add document processing to my workflow"

**Key MCP tools:**
- Azure AI Search service management
- Azure OpenAI model deployment
- Speech Services configuration
- Document Intelligence setup

### azure-aigateway

**Description:** Manage Azure AI Gateway for unified API access to multiple AI services.

**What it does:**
- Configures centralized AI service endpoints
- Manages authentication and rate limiting
- Handles load balancing across AI services
- Provides unified logging and monitoring

**Use when:**
- Using multiple AI services from one app
- Need centralized AI service management
- Building AI platforms or multi-tenant systems
- Implementing rate limiting and quotas

**Ask your assistant:**
- "Set up an AI Gateway for my services"
- "Configure AI Gateway endpoints"
- "Manage authentication for my AI services"

**Key MCP tools:**
- Azure AI Gateway creation and management
- Endpoint configuration
- Quota and rate limit setup

### microsoft-foundry

**Description:** Microsoft Foundry: Deploy AI models, build RAG applications, create and evaluate AI agents.

**Services covered:**
- Deploy models from model catalog (meta-llama, gpt-4, Phi, etc.)
- Build RAG (Retrieval-Augmented Generation) applications
- Create AI agents with tool use
- Evaluate agent performance
- Manage RBAC and quotas

**Use when:**
- Deploying state-of-the-art AI models
- Building RAG applications with knowledge bases
- Creating autonomous AI agents
- Fine-tuning models
- Evaluating AI system performance

**Ask your assistant:**
- "Deploy a Llama model for my application"
- "Create a RAG application with my documents"
- "Build an AI agent that can call tools"
- "Evaluate my agent's performance"
- "What models are available in Foundry?"

**Key MCP tools:**
- Model deployment and management
- Knowledge index creation for RAG
- Agent creation and tool binding
- Evaluation framework and metrics
- RBAC and quota management

---

## Data & Analytics skills

Use these skills for data processing, storage, and analysis.

### azure-postgres

**Description:** Manage Azure Database for PostgreSQL: provisioning, queries, backups, and performance tuning.

**What it does:**
- Creates and configures PostgreSQL databases
- Executes SQL queries
- Manages backups and restoration
- Configures server parameters and performance
- Manages SSL and authentication

**Use when:**
- Setting up production PostgreSQL databases
- Querying and managing data
- Configuring replication or backup strategies
- Tuning database performance
- Troubleshooting connection issues

**Ask your assistant:**
- "Create a PostgreSQL database for my app"
- "Show me my database tables and schema"
- "Optimize my query performance"
- "Restore a backup from yesterday"

**Key MCP tools:**
- Database server creation and management
- SQL query execution
- Backup and restore operations
- Performance metrics and diagnostics
- Firewall rule configuration

### azure-kusto

**Description:** Query Azure Data Explorer (Kusto): large-scale data analytics and time-series analysis.

**What it does:**
- Executes KQL (Kusto Query Language) queries
- Analyzes logs and metrics at scale
- Performs time-series analysis
- Creates alerts and dashboards
- Manages data ingestion

**Use when:**
- Analyzing large volumes of logs or telemetry
- Running time-series analysis
- Building operational dashboards
- Investigating performance issues
- Creating custom reports

**Ask your assistant:**
- "Show me query response times over the last hour"
- "Find errors in my application logs"
- "Analyze user activity patterns"
- "Create a KQL query for [specific analysis]"

**Key MCP tools:**
- KQL query execution
- Cluster and database management
- Data ingestion and export
- Alert and dashboard creation

### azure-storage

**Description:** Work with Azure Storage services: Blob Storage, File Shares, Queue Storage, Table Storage.

**Services covered:**
- **Blob Storage** — Object storage, data lakes, backups
- **File Shares** — SMB file sharing for applications and users
- **Queue Storage** — Asynchronous messaging
- **Table Storage** — NoSQL key-value data

**Use when:**
- Storing and retrieving files at scale
- Sharing files between systems
- Implementing message queues
- Storing structured data without SQL
- Managing data lifecycle (hot, cool, archive tiers)

**Ask your assistant:**
- "Create a storage account for my app"
- "Upload a file to blob storage"
- "Set up a file share"
- "Send a message to a queue"
- "Move old data to cool storage"

**Key MCP tools:**
- Storage account and container management
- Blob upload, download, and listing
- File share creation and mounting
- Queue message operations
- Access key and SAS token management
- Lifecycle policy configuration

---

## Security & Identity skills

Use these skills to implement access control and manage identity.

### azure-rbac

**Description:** Find the right Azure Role-Based Access Control (RBAC) role and assign it with least privilege.

**What it does:**
- Identifies which Azure RBAC role matches your security requirements
- Generates CLI commands to assign roles
- Creates custom roles if needed
- Follows least-privilege principles
- Documents role assignments

**Use when:**
- Assigning permissions to users or service principals
- Implementing least-privilege access
- Reviewing role assignments
- Creating custom roles for specific needs
- Troubleshooting permission issues

**Ask your assistant:**
- "What role should I assign to this user?"
- "Give least-privilege access for this service principal"
- "Create a custom role for [function]"
- "Why do I get a permission denied error?"

**Key MCP tools:**
- Azure RBAC role lookup and filtering
- Role assignment creation
- Custom role definition and creation
- Permission analysis

### azure-compliance

**Description:** Check compliance requirements and validate Azure configurations against compliance standards.

**What it does:**
- Audits Azure resources for compliance policies
- Identifies misconfigurations
- Generates compliance reports
- Recommends remediation steps
- Tracks compliance status over time

**Use when:**
- Ensuring regulatory compliance (HIPAA, PCI-DSS, SOC 2, etc.)
- Auditing Azure configurations
- Preparing for compliance reviews
- Remediating non-compliant resources
- Building compliance dashboards

**Ask your assistant:**
- "Audit my Azure resources for compliance"
- "Is my database encrypted?"
- "Check for [specific compliance standard]"
- "What do I need to fix for compliance?"

**Key MCP tools:**
- Compliance policy scanning
- Resource auditing and reporting
- Remediation workflow automation
- Compliance status tracking

### entra-app-registration

**Description:** Manage Microsoft Entra ID (formerly Azure AD) app registrations for secure authentication.

**What it does:**
- Creates and manages app registrations
- Configures OAuth 2.0 and OpenID Connect flows
- Manages API permissions and scopes
- Generates client secrets and certificates
- Configures reply URLs and redirect URIs

**Use when:**
- Registering applications in Entra ID
- Setting up single sign-on (SSO)
- Configuring API access and permissions
- Managing multi-tenant applications
- Implementing secure authentication flows

**Ask your assistant:**
- "Register my application in Entra ID"
- "Configure OAuth for my app"
- "Grant my app permission to Microsoft Graph"
- "Set up single sign-on"

**Key MCP tools:**
- App registration creation and management
- Permission and scope configuration
- Client secret and certificate management
- Authentication flow setup

---

## Infrastructure & Monitoring skills

Use these skills to manage resources, troubleshoot issues, and optimize costs.

### azure-resource-lookup

**Description:** Find and inspect Azure resources across your subscription.

**What it does:**
- Searches for resources by name, type, or tag
- Returns detailed resource properties and configuration
- Filters by resource group or subscription
- Exports resource information

**Use when:**
- Finding existing resources
- Inspecting resource configuration
- Auditing what's deployed
- Debugging connectivity issues
- Gathering information for troubleshooting

**Ask your assistant:**
- "List all my storage accounts"
- "Find all resources tagged with [tag]"
- "Show me details about this resource"
- "What resources are in my resource group?"

**Key MCP tools:**
- Resource search and filtering
- Resource group listing
- Detailed resource property retrieval
- Tag-based filtering

### azure-resource-visualizer

**Description:** Visualize your Azure resource architecture and dependencies.

**What it does:**
- Creates visual diagrams of resources
- Shows dependencies between resources
- Displays resource properties and connections
- Generates exportable architecture diagrams

**Use when:**
- Understanding your architecture
- Documenting deployments
- Analyzing resource dependencies
- Designing changes to infrastructure
- Creating architecture diagrams for documentation

**Ask your assistant:**
- "Show me my application architecture"
- "What's connected to this database?"
- "Create a diagram of my resources"
- "What dependencies might be affected if I change this?"

**Key MCP tools:**
- Resource topology visualization
- Dependency mapping
- Diagram generation and export
- Architecture analysis

### azure-diagnostics

**Description:** Debug and troubleshoot production issues on Azure resources.

**What it does:**
- Collects diagnostic logs from Azure services
- Analyzes common issue patterns
- Suggests remediation steps
- Runs health checks
- Queries diagnostic data

**Use when:**
- Application behaves unexpectedly
- Service is unavailable or slow
- Debugging container issues
- Investigating deployment failures
- Analyzing error patterns

**Ask your assistant:**
- "Why is my app not responding?"
- "Debug this container app issue"
- "What's causing these errors in my logs?"
- "Run a health check on my service"

**Key MCP tools:**
- Diagnostic data collection
- Error log analysis
- Health check execution
- Issue pattern detection

### azure-observability

**Description:** Set up monitoring, logging, and alerting for your Azure resources.

**Services covered:**
- Azure Monitor (metrics, logs, health)
- Application Insights (APM, tracing)
- Log Analytics (KQL queries, analysis)
- Alerts and action groups
- Workbooks (interactive reports)

**Use when:**
- Setting up production monitoring
- Tracking application performance
- Analyzing logs at scale
- Creating operational dashboards
- Setting up alerts for critical events

**Ask your assistant:**
- "Set up monitoring for my app"
- "Show me application performance metrics"
- "Create an alert for high CPU usage"
- "Build a dashboard for my team"

**Key MCP tools:**
- Azure Monitor configuration
- Metric and log querying
- Alert creation and management
- Workbook creation and sharing
- Application Insights instrumentation

### appinsights-instrumentation

**Description:** Configure Application Insights telemetry for performance monitoring and diagnostics.

**What it does:**
- Instruments applications with Application Insights SDK
- Configures telemetry collection (traces, metrics, exceptions)
- Sets up distributed tracing for microservices
- Creates custom metrics and events
- Configures sampling and retention

**Use when:**
- Adding performance monitoring to your app
- Implementing distributed tracing
- Tracking custom business metrics
- Troubleshooting application issues
- Meeting compliance logging requirements

**Ask your assistant:**
- "Add Application Insights to my app"
- "Configure distributed tracing"
- "Track this custom metric"
- "Show me exception data from my app"

**Key MCP tools:**
- SDK installation and configuration
- Telemetry collection setup
- Custom metric creation
- Sampling and retention policies
- Distributed tracing configuration

### azure-cost-optimization

**Description:** Get cost optimization recommendations for your Azure resources.

**What it does:**
- Analyzes resource usage and spending
- Identifies unused resources
- Recommends cost-saving changes
- Estimates savings from recommendations
- Tracks cost trends over time

**Use when:**
- Reducing Azure spending
- Optimizing resource sizing
- Identifying underutilized resources
- Planning budget improvements
- Reviewing spending trends

**Ask your assistant:**
- "How can I reduce my Azure costs?"
- "Are any of my resources underutilized?"
- "What storage tiers should I use?"
- "What are my biggest cost drivers?"

**Key MCP tools:**
- Usage analysis and reporting
- Cost estimation
- Recommendation engine
- Reserved instance analysis
- Spending trend visualization

---

## Next steps

- [Get started with Azure Skills](quickstart.md) — Complete a hands-on deployment
- [Key concepts in Azure Skills](concepts.md) — Understand how skills work together
- [Azure MCP Server documentation](https://learn.microsoft.com/azure/developer/azure-mcp-server/) — Technical details
