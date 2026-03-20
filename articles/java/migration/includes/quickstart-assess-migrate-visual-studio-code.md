---
ms.date: 03/20/2026
ms.collection: ce-skilling-ai-copilot
---

## Prerequisites

- An Azure account with an active subscription. [Create one for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- A GitHub account with an active [GitHub Copilot](https://github.com/features/copilot) subscription under any plan.
- The latest version of [Visual Studio Code](https://code.visualstudio.com/). Must be version 1.106 or later.
  - [GitHub Copilot in Visual Studio Code](https://code.visualstudio.com/docs/copilot/overview). For setup instructions, see [Set up GitHub Copilot in Visual Studio Code](https://code.visualstudio.com/docs/copilot/setup). Be sure to sign in to your GitHub account within Visual Studio Code.
  - [GitHub Copilot app modernization](https://marketplace.visualstudio.com/items?itemName=vscjava.migrate-java-to-azure). Restart Visual Studio Code after installation.
- [Java 21](/java/openjdk/download) or later.
- [Maven](https://maven.apache.org/download.cgi) or [Gradle](https://gradle.org/install/) to build Java projects.

> [!NOTE]
> If you're using Gradle, only the Gradle wrapper version 5+ is supported. The Kotlin Domain Specific Language (DSL) isn't supported.

## Upgrade JDK and dependency versions

There are two ways to upgrade your JDK version. Both ways use the **GitHub Copilot app modernization** pane in Visual Studio Code, which you can access from the sidebar.

One way to upgrade your JDK version is to select **Upgrade Runtime & Frameworks** in the **QUICKSTART** section. Another way is to run the **Upgraded Java Runtime** task in the **TASKS - Upgrade Tasks** section. For more information, see [Quickstart: upgrade a Java project with GitHub Copilot app modernization](/java/upgrade/quickstart-upgrade).

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/upgrade-java-version-visual-studio-code.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/upgrade-java-version-visual-studio-code.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Upgrade options highlighted.":::

To upgrade the Spring framework or a third-party dependency, run the **Upgrade Java Framework** task in the **TASKS - Upgrade Tasks** section. For more information, see [Upgrade a Java framework or third-party dependency by using GitHub Copilot app modernization](/java/upgrade/framework-upgrade).

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/upgrade-framework-version-visual-studio-code.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/upgrade-framework-version-visual-studio-code.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Upgrade Java Framework task highlighted.":::

## Assess cloud readiness

Use the following steps to start your migration process with solution assessment. This assessment helps you understand what your cloud readiness challenges are and how impactful they are. It also provides recommended solutions. A solution recommendation includes references to set up Azure resources, add configurations, and make code changes.

1. Clone the [Java migration copilot samples](https://github.com/Azure-Samples/java-migration-copilot-samples) repository and then check out to the **source** branch.

1. In Visual Studio Code, open the **mi-sql-public-demo** project folder in the samples repository.

1. On the sidebar, select the **GitHub Copilot app modernization** pane, and then select **Start Assessment** or **Open Assessment Dashboard** in the **QUICKSTART** section.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/run-assessment-visual-studio-code.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/run-assessment-visual-studio-code.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization pane with the Start Assessment or Open Assessment Dashboard button highlighted.":::

1. Select **Recommended Assessment**, then select the **Cloud Readiness** domain and select **OK** to start the assessment.

1. Upon completion of the analysis, the modernization assessor produces a categorized view of cloud readiness issues in an opened **Assessment Report**.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-visual-studio-code.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-visual-studio-code.png" alt-text="Screenshot of the Visual Studio Code pane that shows the assessment report.":::

1. When reviewing the summary report, you can select **Migrate to Azure SQL Database (Spring)** from the solution list under the issue **Database Migration (Microsoft SQL)**. Then, select **Run Task** to move to the code remediation stage.

   :::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/confirm-sql-solution-visual-studio-code.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/confirm-sql-solution-visual-studio-code.png" alt-text="Screenshot of the Visual Studio Code Issues pane that shows the Migrate to Azure SQL Database option with the Run Task button highlighted.":::