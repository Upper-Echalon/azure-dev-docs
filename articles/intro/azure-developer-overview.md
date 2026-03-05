---
title: Azure for developers overview
description: An overview of Azure from a developer's perspective.
keywords: azure billing, azure portal
ms.service: azure
ms.topic: overview
ms.date: 09/22/2025
ms.custom: overview
---

# Azure for developers overview

If you're new to developing applications for the cloud, start with this seven-article series.

* Part 1: **Azure for developers overview**
* Part 2: [Key Azure services for developers](azure-developer-key-services.md)
* Part 3: [Hosting applications on Azure](hosting-apps-on-azure.md)
* Part 4: [Connect your app to Azure services](connect-to-azure-services.md)
* Part 5: [How do I create and manage resources in Azure?](azure-developer-create-resources.md)
* Part 6: [Key concepts for building Azure apps](azure-developer-key-concepts.md)
* Part 7: [How am I billed?](azure-developer-billing.md)

Azure is a cloud platform designed to simplify the process of building modern applications. Whether you choose to host your applications entirely in Azure or extend your on-premises applications with Azure services, Azure helps you create applications that are scalable, reliable, and maintainable.

Azure supports the most popular programming languages in use today, including Python, JavaScript, Java, .NET, and Go. With a comprehensive SDK library and extensive support in tools you already use like VS Code, Visual Studio, IntelliJ, and Eclipse, Azure builds on the skills you already have and helps you be productive right away.

Azure also provides a suite of [developer tools](#azure-developer-tools) that streamline how you build, deploy, and manage cloud applications.

## Application development scenarios on Azure

Incorporate Azure into your application in different ways depending on your needs. The following video provides a helpful overview of the most popular development scenarios for Azure developers:


> [!VIDEO e882f09e-efff-465d-a72e-1b430631e6bf]


Common software development and deployment scenarios on Azure:

- **Application hosting on Azure -** Host your entire application stack: web applications, APIs, databases, and storage services. Azure supports various hosting models from fully managed services to containers to virtual machines. When you use fully managed Azure services, your applications take advantage of the scalability, high availability, and security built into Azure.

- **Consuming cloud services from existing on-premises applications -** Extend existing on-premises apps with Azure services. For example, an application can use Azure Blob Storage to store files, Azure Key Vault to securely store application secrets, or [Azure AI Search](/azure/search/search-what-is-azure-search) to add full-text search capability. These fully managed services integrate with your apps without changing your application architecture or deployment model.

- **Container based architectures -** Use container-based services to modernize your apps. Whether you need a private registry for container images, you're containerizing an existing app for easier deployment, deploying microservices-based applications, or managing containers at scale, Azure has solutions that support your needs.

- **AI driven applications -** Build AI-powered applications on your terms, in your preferred programming language, in the cloud, on-premises, or at the edge. Get tools, services, and guidelines to help you apply AI responsibly in your applications while preserving data privacy, transparency, and trust. Use Azure AI to add speech, vision, language, and decision capabilities to your applications, create chatbots, and uncover insights with AI-powered search.

- **Modern serverless architectures -** Use Azure Functions to simplify building event-driven solutions, whether responding to HTTP requests, handling file uploads in Blob storage, or processing queue events. You write only the code necessary to handle your event without worrying about servers or framework code. Use over 250 connectors to Azure and other services to tackle integration problems.


How do you implement those scenarios? The next article, "Key Azure services for developers", gives several Azure service options to implement each scenario.

## Azure developer tools

Azure provides tools designed for every stage of the development lifecycle. These tools work alongside the Azure services described in the rest of this series.

| Tool | Description |
|------|-------------|
| [Azure Developer CLI (`azd`)](../azure-developer-cli/overview.md) | A developer-focused command-line tool that reduces the time it takes to get your app from a local development environment to Azure. Use starter templates to provision infrastructure and deploy code with a single command. |
| [GitHub Copilot for Azure](../github-copilot-azure/introduction.md) | An AI-powered extension for GitHub Copilot that helps you learn about Azure services, design solutions, troubleshoot issues, and deploy resources using natural language. |
| [Azure Tools for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) | An extension pack for Visual Studio Code that lets you create, manage, and deploy Azure resources directly from your editor. Includes extensions for App Service, Functions, Storage, Databases, and more. |
| [Azure development with Visual Studio](/visualstudio/azure/overview-azure-integration) | Visual Studio includes built-in Azure workloads for creating, debugging, and deploying cloud applications. Connected Services simplify adding Azure dependencies to your projects. |

For a hands-on walkthrough of these tools, see [Get started with Azure as a developer](get-started-developer-path.md). To learn how these tools fit into the broader set of options for creating and managing Azure resources, see [Part 5: How do I create and manage resources in Azure?](azure-developer-create-resources.md).

> [!div class="nextstepaction"]
> [Continue to part 2: Key Azure services for developers](azure-developer-key-services.md)
