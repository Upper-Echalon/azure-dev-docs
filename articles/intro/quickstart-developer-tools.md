---
title: "Quickstart: Azure developer tools"
description: Get hands-on with the Azure Developer CLI, Azure Tools for VS Code, Visual Studio Azure tools, and GitHub Copilot for Azure.
ms.service: azure
ms.topic: quickstart
ms.date: 03/04/2026
ms.custom: devx-track-azdevcli
ai-usage: ai-generated
---

# Quickstart: Azure developer tools

In this quickstart, you use the core Azure developer tools to deploy a sample application to Azure. By the end, you'll have hands-on experience with:

- **Azure Developer CLI (`azd`)** to scaffold and deploy a full-stack app
- **Azure Tools for VS Code** to browse and manage your deployed resources
- **Visual Studio Azure development** to connect your projects to Azure services
- **GitHub Copilot for Azure** to get AI-assisted answers about your Azure resources

## Prerequisites

- An Azure account with an active subscription. [Create one for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- A [GitHub Copilot](https://github.com/features/copilot) subscription - required by GitHub Copilot for Azure
- You can use either the local installation of the tools or the browser-based VS Code for the Web experience. For the local installation, ensure you have:
    - [Visual Studio Code](https://code.visualstudio.com/)
    - [Git](https://git-scm.com/downloads) - required by `azd init --template` to clone the template repository

## Set up the tools

# [VS Code for the Web](#tab/vscode-web)

The fastest way to get started is with [VS Code for the Web (vscode.dev/azure)](https://vscode.dev/azure), which gives you a browser-based VS Code environment with the Azure Tools extension pack and GitHub Copilot for Azure preinstalled. No local installation is required.

1. Open <https://vscode.dev/azure> in your browser.
1. Sign in with your Azure account when prompted.
1. You now have access to the Azure Tools extensions and GitHub Copilot for Azure directly in the browser.

> [!NOTE]
> The `azd` CLI commands in this quickstart require a local terminal. You can use vscode.dev/azure to browse resources and chat with GitHub Copilot for Azure, but open a local terminal for the `azd init`, `azd up`, and `azd down` commands. Install `azd` locally by following the steps in [Install the Azure Developer CLI](../azure-developer-cli/install-azd.md).

# [Install tools locally](#tab/local-install)

Install the Azure Developer CLI, the Azure Tools extension pack for VS Code, and the GitHub Copilot for Azure extension.

1.  The Azure Developer CLI (`azd`) is a command-line tool that simplifies provisioning and deploying applications to Azure. Follow the steps in [Install the Azure Developer CLI](../azure-developer-cli/install-azd.md) for your operating system.
1. The [Azure Tools extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) includes extensions for Azure App Service, Azure Functions, Azure Storage, Azure Databases, and more.
1. [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) provides AI-powered code completions, chat, and suggestions directly in VS Code.
1. [GitHub Copilot for Azure](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azure-github-copilot) extends Copilot with Azure-specific knowledge so you can ask questions about your Azure resources, get deployment guidance, and troubleshoot issues.

After installation, sign in to your GitHub account when prompted.

---

## Deploy a sample app with azd

Use the Azure Developer CLI to deploy a full-stack to-do application to Azure. This step creates all the Azure resources and deploys the application code.

1. Open a terminal (`Ctrl+\``) and initialize a project from a starter template:

    ```bash
    mkdir my-todo-app && cd my-todo-app
    azd init --template todo-nodejs-mongo
    ```

1. When prompted, enter an environment name like `my-todo-dev`. This name is used as a prefix for the Azure resources.

1. Sign in to Azure:

    ```bash
    azd auth login --use-device-code
    ```

    The `--use-device-code` flag displays a URL and a one-time code in the terminal. Open the URL in any browser, enter the code, and sign in with your Azure account. This method works even if your terminal doesn't support interactive login.

1. Provision Azure resources and deploy the application:

    ```bash
    azd up
    ```

    When prompted, select a subscription and region. The `azd up` command:
    - Creates a resource group with the infrastructure defined in the template.
    - Provisions the required Azure services (App Service, Azure Cosmos DB, and others).
    - Deploys the application code.

    This process takes a few minutes. When it finishes, `azd` displays the URL of your deployed application.

1. Open the URL in your browser to verify the application is running. You should see a to-do application where you can add and complete tasks.

## Browse resources with Azure Tools for VS Code

Now use the Azure Tools extension to explore the resources that `azd` created.

1. Verify that you're signed in to Azure by running the following command in the terminal:

    ```bash
    az account show
    ```

    If the command returns your account details, you're already signed in. If not, sign in through VS Code:
    - Open the Command Palette (**Ctrl+Shift+P**).
    - Type **Azure: Sign In** and select it.
    - Complete the sign-in flow in your browser.

1. Open the Azure view by selecting the Azure icon in the Activity Bar (left sidebar).

1. Expand **Resources** to see your Azure subscriptions. Make sure the resource list is grouped by **Resource Group** (select the **Group By** icon at the top of the Resources view and choose **Resource Group** if needed). Expand your subscription and find the resource group created by `azd` (it starts with the environment name you chose).

1. Explore the deployed resources:
    - Expand the resource group to see the App Service, Cosmos DB account, and other resources.
    - Right-click the **App Service** resource and select **Browse Website** to open your deployed app.
    - Right-click the **Cosmos DB** account and select **Open in Portal** to view the database in the Azure portal.

1. View application logs:
    - Right-click the **App Service** resource.
    - Select **Start Streaming Logs** to see live log output from your running application.
    - Open your to-do app in a browser and add a task to see log entries appear.

## Use GitHub Copilot for Azure

Use GitHub Copilot for Azure to learn about the resources you deployed and get guidance on next steps.

1. In VS Code, open the Copilot Chat view by selecting the chat icon in the Activity Bar or pressing **Ctrl+Shift+I**.

1. Ask about your deployed resources. Type:

    ```text
    @azure What resources are in my resource group that contains "todo"?
    ```

    GitHub Copilot for Azure queries your subscription and lists the resources created by `azd`.

1. Ask for guidance on your application:

    ```text
    @azure How can I add authentication to my Azure App Service?
    ```

    Copilot provides step-by-step guidance tailored to your deployed application.

1. Troubleshoot issues. If your app isn't working as expected, try:

    ```text
    @azure Are there any errors in my App Service logs?
    ```

1. Learn about cost. Ask about the cost implications of your deployment:

    ```text
    @azure What is the estimated monthly cost of the resources in my resource group?
    ```

## Visual Studio Azure development

If you use Visual Studio, you can manage Azure services through its built-in tooling.

1. Open Visual Studio and install the **Azure development** workload if you haven't already:
    - Go to **Tools** > **Get Tools and Features**.
    - Select the **Azure development** workload and install it.

1. Sign in to Azure:
    - Go to **Tools** > **Options** > **Azure Service Authentication**.
    - Select your Azure account.

1. View your Azure resources:
    - Open **View** > **Cloud Explorer**.
    - Expand your subscription to browse the same resources you created with `azd`.

1. Add Azure service dependencies to a project:
    - Right-click the project in Solution Explorer.
    - Select **Add** > **Connected Service**.
    - Connected Services lets you add Azure Storage, Azure Key Vault, Azure SQL, and other services with guided configuration.

## Clean up resources

When you're done exploring, delete the Azure resources to avoid incurring charges:

```bash
azd down
```

This command deletes all Azure resources created by `azd up`, including the resource group, App Service, and Cosmos DB account.

## Next steps

Now that you've used the core Azure developer tools, explore more:

- [Azure Developer CLI templates](../azure-developer-cli/azd-templates.md) - Find templates for different languages and architectures.
- [Azure for developers overview](azure-developer-overview.md) - Understand the key Azure concepts for application developers.
- [GitHub Copilot for Azure documentation](../github-copilot-azure/introduction.md) - Learn more about AI-assisted Azure development.
- [Azure Tools for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) - Explore all available extensions.
