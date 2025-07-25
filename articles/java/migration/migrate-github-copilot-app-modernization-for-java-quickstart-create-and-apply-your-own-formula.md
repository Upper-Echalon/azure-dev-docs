---
title: "Quickstart: Create and Apply Your Own Formula"
titleSuffix: GitHub Copilot App Modernization for Java - Azure
description: Shows you how to create and apply your own formula.
author: KarlErickson
ms.author: karler
ms.reviewer: xiading
ms.topic: quickstart
ms.date: 06/30/2025
ms.custom: devx-track-java
ms.service: azure-java
---

# Quickstart: create and apply your own formulas for GitHub Copilot App Modernization for Java

This quickstart shows you how to create and apply your own formulas when you use GitHub Copilot App Modernization for Java.

In code development, enterprises often have different processes and controls to adhere to their organizational policies and business needs. This area is where *custom formulas* come in. A custom formula is generated by analyzing code commits from already-migrated code. The formula then guides Copilot to remediate code, following the pattern established by the already-migrated code.

The following video demonstrates using GitHub Copilot App Modernization for Java to create and apply your own custom formula to migrate a Java project to Azure:

<br>

> [!VIDEO https://www.youtube.com/embed/ZiO3eznAl5w]

## Prerequisites

- A GitHub account with [GitHub Copilot](https://github.com/features/copilot) enabled. A Pro, Pro+, Business, or Enterprise plan is required.
- The latest version of [Visual Studio Code](https://code.visualstudio.com/). Must be version 1.101 or later.
- The latest version of the [GitHub Copilot extension in Visual Studio Code](https://code.visualstudio.com/docs/copilot/overview).
- [GitHub Copilot App Modernization](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-app-mod-pack) extension pack. For install instructions, see [Quickstart: assess and migrate a Java project using GitHub Copilot App Modernization for Java](migrate-github-copilot-app-modernization-for-java-quickstart-assess-migrate.md).

  This extension pack bundles the following two extensions:
  - [GitHub Copilot App Modernization for Java](migrate-github-copilot-app-modernization-for-java.md)
  - [GitHub Copilot App Modernization - upgrade for Java](/java/upgrade/overview)

  App Modernization doesn't require Java in your local environment. However, to build your project successfully, install the correct version of Java and Maven. We recommend the [Microsoft Build of OpenJDK](/java/openjdk/) and [Maven](https://maven.apache.org/download.cgi).

- [AppCAT](/azure/migrate/appcat/java). This tool is required for the app assessment feature.

## Create a custom formula

Use the following steps to create a custom formula:

1. Clone the [Java migration copilot samples](https://github.com/Azure-Samples/java-migration-copilot-samples) repository.

1. In Visual Studio Code, open the **rabbitmq-sender** project folder in the samples repository. Then, check out the project to the **expected** branch.

1. In the **Activity** sidebar, open the **App Modernization for Java** extension pane and then, in the **Formulas - Custom** section, select **Create Custom Formula**.

   :::image type="content" source="./media/migrate-github-copilot-app-modernization-for-java/create-formula-from-source-control.png" lightbox="./media/migrate-github-copilot-app-modernization-for-java/create-formula-from-source-control.png" alt-text="Screenshot of Visual Studio Code that shows the button for Create Custom Formula.":::

1. In the pop-up dialog box, select **Create new formula**.

   :::image type="content" source="./media/migrate-github-copilot-app-modernization-for-java/select-create-custom-formula.png" lightbox="./media/migrate-github-copilot-app-modernization-for-java/select-create-custom-formula.png" alt-text="Screenshot of Visual Studio Code that shows the Create new formula option.":::

1. Type **migrate rabbitmq to expected** to search for the commit that migrates RabbitMQ. Select the corresponding commit and then select **OK**.

   :::image type="content" source="./media/migrate-github-copilot-app-modernization-for-java/commit-for-custom-formula.png" lightbox="./media/migrate-github-copilot-app-modernization-for-java/commit-for-custom-formula.png" alt-text="Screenshot of the Visual Studio Code dialog box with the heading Select commits you want to save.":::

1. Select any uncommitted changes from **Working tree** if they exist, then select **OK**.

1. If you want to import the commits from a file, choose **Select Files** in the next pop-up dialog box. This option enables you to select files that contain the commit history you want to use for the custom formula. Then select **OK**. The file you selected is processed locally.

   :::image type="content" source="./media/migrate-github-copilot-app-modernization-for-java/import-diff-from-file.png" lightbox="./media/migrate-github-copilot-app-modernization-for-java/import-diff-from-file.png" alt-text="Screenshot of Visual Studio Code that shows the Describe changes using local files dialog box.":::

1. A default formula name is generated. Name it **custom formula migrate rabbitmq**, then press <kbd>Enter</kbd> to confirm. A formula description is generated. Press <kbd>Enter</kbd> to confirm.

1. Now, the custom formula for migrating `rabbitmq` is generated and shows in the **Formulas - Custom** section of the **App Modernization for Java** pane.

   :::image type="content" source="./media/migrate-github-copilot-app-modernization-for-java/custom-formula-rabbitmq.png" lightbox="./media/migrate-github-copilot-app-modernization-for-java/custom-formula-rabbitmq.png" alt-text="Screenshot of Visual Studio Code that shows the Formulas section with the rabbitmq formula showing.":::

## Apply the custom formula

Use the following steps to apply the custom formula:

1. Check out the project to the **main** branch. Find the custom formula in the **Formulas** section of **App Modernization for Java** pane. Run this formula by selecting **Run Formula**.

   :::image type="content" source="./media/migrate-github-copilot-app-modernization-for-java/run-formula.png" lightbox="./media/migrate-github-copilot-app-modernization-for-java/run-formula.png" alt-text="Screenshot of Visual Studio Code that shows the Formulas section with the Run formula button indicated by a tooltip.":::

   After you select the formula, the Copilot chat window with Agent Mode opens automatically.

1. Select **Continue** repeatedly to confirm each tool action in the Copilot Chat window. The Copilot Agent uses various tools to facilitate application modernization. Each tool's usage requires confirmation by selecting **Continue**.

1. After each step, manually input **continue** to confirm and proceed.

1. Wait for the code changes to be generated.

1. When you're prompted to run the **Java Application Build-Fix** tool, select **Continue** to build the project and fix errors. This tool attempts to resolve any build errors in up to 10 iterations.

1. After the Build-Fix tool begins, select **Continue** to proceed and show progress.

1. After the tool is finished, review the code changes and confirm them by selecting **Keep**.

## See also

[Predefined formulas for GitHub Copilot App Modernization for Java](migrate-github-copilot-app-modernization-for-java-predefined-formula.md)
