---
title: Deploy to Azure App Service slots with Azure Developer CLI
description: Learn how to use Azure Developer CLI to deploy to Azure App Service slots and swap slots for staging, promotion, or rollback. Get started today.
author: alexwolfmsft
ms.author: alexwolf
ms.date: 03/26/2026
ms.service: azure-dev-cli
ms.topic: how-to
ms.custom: devx-track-azdevcli
ai-usage: ai-generated
---

# Deploy to Azure App Service deployment slots with Azure Developer CLI

Azure Developer CLI (`azd`) supports Azure App Service deployment slots for apps hosted on App Service. You can define slots in your infrastructure, deploy code to a specific slot, and swap slots when you're ready to promote a release.

Use this approach for staging, blue-green deployments, smoke testing, and rollbacks without adding custom deployment scripts.

## Prerequisites

- An `azd` project that deploys a service to Azure App Service.
- Infrastructure-as-code that defines your App Service resources in Bicep.
- An App Service plan on Standard (`S1`) tier or higher. Free, Shared, and Basic tiers don't support deployment slots.

## Define a deployment slot in Bicep

Define your production site as usual, then add a `Microsoft.Web/sites/slots` resource for each slot you want `azd` to target.

```bicep
resource appServicePlan 'Microsoft.Web/serverfarms@2021-03-01' = {
  name: 'my-appservice-plan'
  location: resourceGroup().location
  sku: {
    name: 'S1'
    tier: 'Standard'
  }
}

resource webApp 'Microsoft.Web/sites@2021-03-01' = {
  name: 'my-appservice'
  location: resourceGroup().location
  kind: 'app'
  properties: {
    serverFarmId: appServicePlan.id
  }
}

resource stagingSlot 'Microsoft.Web/sites/slots@2021-03-01' = {
  name: '${webApp.name}/staging'
  location: webApp.location
  properties: {}
}
```

If you use Azure Verified Modules (AVM), define the web app and deployment slot modules in the same deployment and pass the app name to the slot module.

## Deploy to a slot with azd

Run `azd up` or `azd provision` and `azd deploy` as usual.

```bash
azd up
```

On the first deployment, `azd` deploys to the production site and any slots defined in your infrastructure. After that, if your service has more than one slot, `azd deploy` prompts you to choose the target slot.

To skip the prompt, set an environment variable for the service you want to deploy. Use the service name from `azure.yaml` in uppercase.

```bash
azd env set AZD_DEPLOY_MYAPI_SLOT_NAME staging
azd deploy myapi
```

For example, if your service is named `web`, set `AZD_DEPLOY_WEB_SLOT_NAME`. This approach is useful for CI/CD because you can set the same environment variable in your pipeline before running `azd deploy`.

## Swap Azure App Service deployment slots

Use the `azure.appservice` extension to swap slots after validation. If the extension isn't already installed, `azd` prompts you to install it the first time you run the command.

Run the interactive experience:

```bash
azd appservice swap
```

If only one nonproduction slot exists, `azd` skips the prompts and swaps directly with production.

For automation, specify the source and destination slots explicitly. Use `@main` to reference the production slot.

```bash
azd appservice swap --src staging --dst @main
azd appservice swap --src @main --dst staging
azd appservice swap --service myapi --src staging --dst @main
```

Use these patterns to support common release flows:

- Promote a validated staging deployment to production with `--src staging --dst @main`.
- Roll back by swapping production back into the staging slot with `--src @main --dst staging`.
- Target a specific App Service-backed service in a multiservice `azd` project with `--service`.

## Recommended deployment slot workflow

1. Define one or more App Service deployment slots in your Bicep templates.
1. Provision the App Service resources by using `azd provision` or `azd up`.
1. Deploy application code to a staging slot by setting `AZD_DEPLOY_<SERVICE_NAME>_SLOT_NAME` or by selecting the slot when prompted.
1. Validate the staged deployment.
1. Run `azd appservice swap --src <slot> --dst @main` to promote the release.
1. If needed, run the reverse swap to roll back.

## Related content

- [Azure Developer CLI commands overview](azd-commands.md)
- [Azure Developer CLI reference](reference.md)
- [Set up staging environments in Azure App Service](/azure/app-service/deploy-staging-slots)
- [Deploy to Azure App Service deployment slots with azd](https://devblogs.microsoft.com/azure-sdk/azd-app-service-slot/)
- [Azure Developer CLI (azd): One command to swap Azure App Service slots](https://devblogs.microsoft.com/azure-sdk/azd-appservice-swap/)
