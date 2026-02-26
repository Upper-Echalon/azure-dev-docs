---
ms.topic: include
ms.date: 02/26/2026
title: "Quickstart: Assess and Migrate a Java Project Using GitHub Copilot app modernization in Visual Studio Code"
description: Shows you how to use GitHub Copilot app modernization to assess and migrate a Java project in Visual Studio Code.
---

## Upgrade JDK and dependency versions

There are two ways to upgrade your JDK version. Both ways use the **GitHub Copilot app modernization** pane in Visual Studio Code, which you can access from the sidebar.

One way to upgrade your JDK version is to select **Upgrade Runtime & Frameworks** in the **QUICKSTART** section. Another way is to run the **Upgraded Java Runtime** task in the **TASKS - Upgrade Tasks** section. For more information, see [Quickstart: upgrade a Java project with GitHub Copilot app modernization](/java/upgrade/quickstart-upgrade).

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/upgrade-java-version-vscode.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/upgrade-java-version-vscode.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Upgrade options highlighted.":::

To upgrade the Spring framework or a third-party dependency, run the **Upgrade Java Framework** task in the **TASKS - Upgrade Tasks** section. For more information, see [Upgrade a Java framework or third-party dependency by using GitHub Copilot app modernization](/java/upgrade/framework-upgrade).

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/upgrade-framework-version-vscode.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/upgrade-framework-version-vscode.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Upgrade Java Framework task highlighted.":::

## Assess cloud readiness

Use the following steps to start your migration process with solution assessment. This assessment helps you understand what your cloud readiness challenges are and how impactful they are. It also provides recommended solutions. A solution recommendation includes references to set up Azure resources, add configurations, and make code changes.

1. Clone the [Java migration copilot samples](https://github.com/Azure-Samples/java-migration-copilot-samples) repository and then check out to the **source** branch.

1. In Visual Studio Code, open the **mi-sql-public-demo** project folder in the samples repository.

1. On the sidebar, select the **GitHub Copilot app modernization** pane, and then select **Start Assessment** or **Open Assessment Dashboard** in the **QUICKSTART** section.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/run-assessment-vscode.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/run-assessment-vscode.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Start Assessment or Open Assessment Dashboard button highlighted.":::

1. Select **Recommended Assessment**, then select the **Cloud Readiness** domain and select **OK** to start the assessment.

1. Upon completion of the analysis, the modernization assessor produces a categorized view of cloud readiness issues in an opened **Assessment Report**.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-vscode.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-vscode.png" alt-text="Screenshot of the Visual Studio Code pane that shows the assessment report.":::

1. When reviewing the summary report, you can select **Migrate to Azure SQL Database (Spring)** from the solution list under the issue **Database Migration (Microsoft SQL)**. Then, select **Run Task** to move to the code remediation stage.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/confirm-sql-solution-vscode.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/confirm-sql-solution-vscode.png" alt-text="Screenshot of the Visual Studio Code Issues pane that shows the Migrate to Azure SQL Database option with the Run Task button highlighted.":::