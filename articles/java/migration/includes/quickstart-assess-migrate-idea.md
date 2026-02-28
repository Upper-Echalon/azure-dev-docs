---
ms.topic: include
ms.date: 02/26/2026
title: "Quickstart: Assess and Migrate a Java Project Using GitHub Copilot app modernization in IntelliJ IDEA"
description: Shows you how to use GitHub Copilot app modernization to assess and migrate a Java project in IntelliJ IDEA.
---

## Prerequisites

- An Azure account with an active subscription. [Create one for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- A GitHub account with an active [GitHub Copilot](https://github.com/features/copilot) subscription under any plan.
- The latest version of [IntelliJ IDEA](https://www.jetbrains.com/idea/download). Must be version 2023.3 or later.
  - [GitHub Copilot](https://plugins.jetbrains.com/plugin/17718-github-copilot). Must be version 1.5.59 or later. For more instructions, see [Set up GitHub Copilot in IntelliJ IDEA](https://docs.github.com/en/copilot/get-started/quickstart). Be sure to sign in to your GitHub account within IntelliJ IDEA.
  - [GitHub Copilot app modernization](https://plugins.jetbrains.com/plugin/28791-github-copilot-app-modernization). Restart IntelliJ IDEA after installation. If you don't have GitHub Copilot installed, you can install GitHub Copilot app modernization directly.
- [Java 21](/java/openjdk/download) or later.
- [Maven](https://maven.apache.org/download.cgi) or [Gradle](https://gradle.org/install/) to build Java projects.

> [!NOTE]
> If you're using Gradle, only the Gradle wrapper version 5+ is supported. The Kotlin Domain Specific Language (DSL) isn't supported.
>
> The function `My Tasks` isn't supported yet for IntelliJ IDEA.

## Upgrade JDK and dependency versions

There are two ways to upgrade your JDK version. Both ways use the **GitHub Copilot app modernization** pane in IntelliJ IDEA, which you can access from the sidebar.

One way to upgrade your JDK version is to select **Upgrade Runtime & Frameworks** in the **QUICKSTART** section. Another way is to run the **Upgraded Java Runtime** task in the **TASKS - Upgrade Tasks** section. For more information, see [Quickstart: upgrade a Java project with GitHub Copilot app modernization](/java/upgrade/quickstart-upgrade).

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/upgrade-java-version-old.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/upgrade-java-version-old.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Upgrade options highlighted.":::

To upgrade the Spring framework or a third-party dependency, run the **Upgrade Java Framework** task in the **TASKS - Upgrade Tasks** section. For more information, see [Upgrade a Java framework or third-party dependency by using GitHub Copilot app modernization](/java/upgrade/framework-upgrade).

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/upgrade-framework-version-old.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/upgrade-framework-version-old.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Upgrade Java Framework task highlighted.":::

## Assess cloud readiness

Use the following steps to start your migration process with solution assessment. This assessment helps you understand what your cloud readiness challenges are and how impactful they are. It also provides recommended solutions. A solution recommendation includes references to set up Azure resources, add configurations, and make code changes.

1. Clone the [Java migration copilot samples](https://github.com/Azure-Samples/java-migration-copilot-samples) repository and then check out to the **source** branch.

1. In IntelliJ IDEA, open the **mi-sql-public-demo** project folder in the samples repository.

1. On the sidebar, select the **GitHub Copilot app modernization** pane, where you can select **Migrate to Azure** or **Run Assessment** in the **ASSESSMENT** section.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/run-assessment-old.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/run-assessment-old.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Migrate to Azure and Run Assessment buttons highlighted.":::

1. The GitHub Copilot chat window with agent mode opens to call the modernization assessor to execute the app modernization assessment. Select **Continue** to confirm.

1. The modernization assessor now opens **appcat.log**. This file shows the logs for running AppCAT, which performs the app assessment. Select **Continue** to confirm again.

1. The modernization assessor verifies your local environment first. If the AppCAT and its dependencies aren't installed, the agent helps you install them. After installation, the agent calls AppCAT to assess the current project. This step could take several minutes to complete.

1. Upon completion of the analysis, the modernization assessor produces a categorized view of cloud readiness issues in an opened **Assessment Report**.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-old.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-old.png" alt-text="Screenshot of the Visual Studio Code pane that shows the assessment report.":::

1. When reviewing the summary report, you can select **Migrate to Azure SQL Database (Spring)** from the solution list under the issue **Database Migration (Microsoft SQL)**. Then, select **Run Task** to move to the code remediation stage.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/confirm-sql-solution-old.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/confirm-sql-solution-old.png" alt-text="Screenshot of the Visual Studio Code Issues pane that shows the Migrate to Azure SQL Database option with the Run Task button highlighted.":::
