---
ms.topic: include
ms.date: 02/26/2026
title: "Working with Assessment in Visual Studio Code: Comprehensive guide to application assessment with GitHub Copilot App Modernization for Java"
description: Learn how to effectively work with application assessments in GitHub Copilot app modernization in Visual Studio Code, including configuration, interpretation, and report management.
---

Key capabilities include:

- **Multiple reports per run**: Each assessment run generates an independent report. Previous reports are preserved and accessible from the report list, enabling you to track assessment history and compare results over time.
- **Two assessment entries for different purposes**: GitHub Copilot app modernization provides two ways to start an assessment:
  - **Recommended assessment**: Quickly start an assessment by selecting from recommended domains without manual configuration.
  - **Custom assessment**: Configure specific assessment properties to tailor the analysis to your exact needs.

## Recommended assessment

Recommended assessment provides a streamlined way to start an assessment without manual configuration. This approach is ideal when you want to quickly evaluate your application's readiness for common migration scenarios.

To run a recommended assessment, use the following steps:

1. Select **Start Assessment** or **Open Assessment Dashboard** in the **QUICKSTART** section of the GitHub Copilot app modernization pane.
1. Select **Recommended Assessment**.
1. Select the domains you want to assess from the list of recommended options. Each domain represents a common migration scenario with preconfigured settings.
1. Select **OK** to start the assessment.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/recommended-assessment.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/recommended-assessment.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization Recommended Assessment interface with domain selection options.":::

After the assessment completes, a new report is generated and added to the report list. You can view the report by selecting it from the list.

## Custom assessment

Custom assessment enables you to tailor the assessment analysis to your specific migration needs. Use this approach when you need fine-grained control over the assessment configuration.

To configure and run a custom assessment, use the following steps:

1. Select **Start Assessment** or **Open Assessment Dashboard** in the **QUICKSTART** section of the GitHub Copilot app modernization pane.
1. Select **Custom Assessment**.
1. Configure the assessment properties as described in the following section.
1. Select **Run** to start the assessment.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/custom-assessment.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/custom-assessment.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization Assessment pane with the Custom Assessment button highlighted.":::

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/custom-assessment-properties.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/custom-assessment-properties.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization Assessment pane with the Custom Assessment properties.":::

### Configuration properties

The custom assessment configuration form consists of general settings and domain-specific settings. The domain-specific settings are displayed based on the assessment domains you select.

#### General: Assessment Domains

Select one or more domains to include in the assessment. Assessment time depends on domain selection and app size.

| Domain               | Description                                                                          |
|----------------------|--------------------------------------------------------------------------------------|
| **Java Upgrade**     | Identify outdated app stacks and get upgrade recommendations.                        |
| **Cloud Readiness**  | Assess your app's readiness for Azure, with actionable migration guidance.           |
| **Security**         | Scan your code for security issues using ISO 5055 guidelines, with recommended fixes.|

#### General: Analysis Coverage

Select what the assessment should analyze.

| Value                                  | Description                                                                             |
|----------------------------------------|-----------------------------------------------------------------------------------------|
| **Issue only**                         | Analyze source code to detect issues.                                                   |
| **Issues & Technologies**              | Analyze source code to detect issues and identify used technologies.                    |
| **Issues, Technologies & Dependencies**| Analyze source code to detect issues, identify used technologies, and map dependencies. |

#### Java Upgrade: Target Runtime

This setting is displayed when you select the **Java Upgrade** domain. Select a target JDK to analyze dependencies and outdated app stack.

| Value              | Description                                       |
|--------------------|---------------------------------------------------|
| **OpenJDK 21**     | Best practices for migrating to OpenJDK 21. (Recommended) |
| **OpenJDK 17**     | Best practices for migrating to OpenJDK 17.       |
| **OpenJDK 11**     | Best practices for migrating to OpenJDK 11.       |

#### Cloud Readiness: Target Compute Services

This setting is displayed when you select the **Cloud Readiness** domain. Select target Azure compute services to migrate your application. Choose multiple targets if you haven't decided which one to use. You can then compare the targets on the assessment report.

| Value                              | Description                                                            |
|------------------------------------|------------------------------------------------------------------------|
| **Azure App Service**              | Best practices for deploying an app to Azure App Service.              |
| **Azure Kubernetes Service (AKS)** | Best practices for deploying an app to Azure Kubernetes Service.       |
| **Azure Container Apps (ACA)**     | Best practices for deploying an app to Azure Container Apps.           |

#### Cloud Readiness: Target Operating System

This setting is displayed when you select the **Cloud Readiness** domain. Select target operating systems to run the apps on.

| Value       | Description                                                            |
|-------------|------------------------------------------------------------------------|
| **Linux**   | Best practices for migrating applications to the Linux platform.       |
| **Windows** | Best practices for migrating applications to the Windows platform.     |

#### Cloud Readiness: Containerization

This setting is displayed when you select the **Cloud Readiness** domain. Enable to analyze issues that need to be fixed to containerize your app.

| Value                        | Description                                    |
|------------------------------|------------------------------------------------|
| **Enable Containerization**  | Best practices for containerizing applications.|

### Examples

The following examples describe some common configuration scenarios:

- Example one: you'd like to migrate your apps to AKS as Linux containers and want to understand what are the issues to be fixed. Use the following configuration:

  - **Assessment Domains**: Select **Cloud Readiness**
  - **Analysis Coverage**: Select **Issue only**
  - **Target Compute Services**: Select **Azure Kubernetes Service (AKS)**
  - **Target Operating System**: Select **Linux**
  - **Containerization**: Select **Enable Containerization**

- Example two: you'd like to migrate your apps to App Service Linux and want to understand what are the issues to be fixed. Use the following configuration:

  - **Assessment Domains**: Select **Cloud Readiness**
  - **Analysis Coverage**: Select **Issue only**
  - **Target Compute Services**: Select **Azure App Service**
  - **Target Operating System**: Select **Linux**

- Example three: you'd like to modernize your apps to JDK 21 and want to understand what are the issues to be fixed. Use the following configuration:

  - **Assessment Domains**: Select **Java Upgrade**
  - **Analysis Coverage**: Select **Issue only**
  - **Target Runtime**: Select **OpenJDK 21**

After the tool completes the assessment, a new report is generated and added to the report list. The interactive dashboard opens automatically, providing comprehensive analysis results. After you configure multiple Azure service targets, you can easily switch between them to compare migration approaches and view service-specific recommendations.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/list-azure-service-target-for-assessment-report-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/list-azure-service-target-for-assessment-report-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment dashboard with Azure service target selection options.":::

## Interpret the assessment report

The assessment report provide comprehensive analysis results to help you understand your application's readiness for Azure migration and modernization. This section guides you through the report structure and helps you interpret the findings to make informed migration decisions.

### Report structure overview

The assessment report consists of several key sections:

- **Application Information**: Basic information about your application including Java version, frameworks, build tools, project structure.
- **Issue Summary**: Overview of migration issues categorized by domain with criticality percentages.
- **Detailed Analysis**: The detail report is organized into the following four subsections.
  - **Issues**: Provides a concise summary of all issues that require attention.
  - **Dependencies**: Displays all Java-packaged dependencies found within the application.
  - **Technologies**: Displays all embedded libraries grouped by functionality, enabling you to quickly view the technologies used in the application.
  - **Insights**: Displays file details and information to help you understand the detected technologies.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-dashboard-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-dashboard-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report dashboard.":::

#### Issues

Access this part by selecting the **Issues** tab. This tab provides a categorized issues list of various aspects of Cloud Readiness, Java Upgrade and Security that you need to address to successfully migrate the application to Azure. The following tables describe the **Domain** and **Criticality** values:

| Domain               | Description                                                                          |
|----------------------|--------------------------------------------------------------------------------------|
| **Java Upgrade**     | Identify outdated app stacks and get upgrade recommendations.                        |
| **Cloud Readiness**  | Assess your app's readiness for Azure, with actionable migration guidance.           |
| **Security**         | Scan your code for security issues using ISO 5055 guidelines, with recommended fixes.|

| Criticality         | Description                                                   |
|---------------------|---------------------------------------------------------------|
| **Mandatory**       | Issues that must be fixed for migration to Azure.             |
| **Potential**       | Issues that might impact migration and need review.           |
| **Optional**        | Low-impact issues. Fixing them is recommended but optional.   |

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-issue-list-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-issue-list-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report issue list.":::

For more information, you can expand each reported issue by selecting the title. The report provides the following information:

- A list of files where the incidents occurred, along with the number of code lines impacted. If the file is a Java source file, then selecting the file line number directs you to the corresponding source report.
- A detailed description of the issue. This description outlines the problem, provides any known solutions, and references supporting documentation regarding either the issue or resolution.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-issue-detail-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-issue-detail-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report issue detail.":::

#### Dependencies

Access this part by selecting the **Dependencies** tab. This tab displays all Java-packaged dependencies found within the application.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-dependency-list-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-dependency-list-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report dependency list.":::

#### Technologies

Access this part by selecting the **Technologies** tab. This tab lists the occurrences of technologies, grouped by function, in the analyzed application. This report is an overview of the technologies found in the application, and is designed to assist you in quickly understanding each application's purpose.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-technology-list-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-technology-list-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report technology list.":::

#### Insights

Access this part by selecting the **Insights** tab. Displays file details and information to help you understand the detected technologies.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-insight-list-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/assessment-report-insight-list-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report insight list.":::

## Operate assessment reports

Effective report management enables collaboration, maintains assessment history, and integrates with existing workflows. Each assessment run generates an independent report in the report list, and you can import, export, or delete individual reports as needed.

### Import assessment report

Besides running the assessment directly in GitHub Copilot app modernization, you can also import assessment reports. The reports can come from [AppCAT](https://aka.ms/appcat-java) CLI results - such as **report.json**, a GitHub Copilot app modernization exported report, or an app context file from Dr. Migrate.

To import an assessment report to GitHub Copilot app modernization, select **Import** in the assessment reports page, or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> and then search for **import assessment report**.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/import-assessment-report-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/import-assessment-report-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report import interface.":::

### Export assessment report

In the assessment dashboard, you can view the issues detected by assessment and choose the migration solution to determine the decision. You can export the report and share it with others. If so, other people don't need to run assessment by themselves and can import the report and view the assessment and migration decision directly.

To export an assessment report from GitHub Copilot app modernization, select the **...** (more actions) button on the target report in the report list and then select **Export**.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/export-assessment-report-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/export-assessment-report-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization assessment report export options and interface.":::

### Delete assessment report

If you no longer need a report, you can delete it from the report list.

To remove an assessment report, select the **...** (more actions) button on the target report in the report list and then select **Delete**.

:::image type="content" source="../media/migrate-github-copilot-app-modernization-for-java/delete-assessment-report-new.png" lightbox="../media/migrate-github-copilot-app-modernization-for-java/delete-assessment-report-new.png" alt-text="Screenshot of Visual Studio Code that shows the GitHub Copilot app modernization delete an assessment report.":::
