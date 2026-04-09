---
title: Add custom prompts to your azd workflow
description: Learn how to add custom prompts and parameters to the Azure Developer CLI (azd) provisioning flow using Bicep decorators and hooks.
author: alexwolfmsft
ms.author: alexwolf
ms.date: 04/08/2026
ms.service: azure-dev-cli
ms.topic: how-to
ms.custom: devx-track-azdevcli
ai-usage: ai-generated
---

# Add custom prompts to your azd workflow

By default, `azd up` prompts for three things: environment name, subscription, and location. However, real projects often need additional input, such as an environment type, project owner, or team name. This article walks through three approaches for adding custom prompts, from simplest to most flexible. You can mix and match all three in the same template.

## Option 1: Selection list with the @allowed decorator

The simplest way to add a custom prompt is to use the `@allowed` decorator on a Bicep parameter. When `azd` encounters a parameter with `@allowed` values and no value is provided, it displays an interactive selection list, similar to the built-in subscription and location pickers.

Add the decorated parameter to your `infra/main.bicep` file:

```bicep
@description('The environment type')
@allowed([
  'dev'
  'staging'
  'prod'
])
param environmentType string
```

When you run `azd up`, `azd` automatically presents a pick list for this parameter. The user can navigate with arrow keys and type to filter, just like the subscription picker.

No extra configuration is needed. Add the parameter to your Bicep file and `azd` handles the rest.

> [!TIP]
> Use the `@metadata` decorator with `azd.default` to highlight a default selection:
>
> ```bicep
> @allowed(['dev', 'staging', 'prod'])
> @metadata({
>   azd: {
>     default: 'dev'
>   }
> })
> param environmentType string
> ```
>
> For more decorator options, see [Work with Azure Developer CLI metadata for Bicep input parameters](metadata.md).

## Option 2: Free-text input

If you need open-ended input instead of a fixed list, declare a parameter with no default value. When `azd` encounters a required parameter that has no default and no value in `main.parameters.json`, it prompts the user for free-text input.

Add the parameter to your `infra/main.bicep` file:

```bicep
@description('Who owns this project')
param projectOwner string
```

When you run `azd up`, the user types a value and presses Enter. That's all you need.

## Option 3: Hooks for custom logic

Bicep decorators cover most scenarios, but sometimes you need more flexibility, such as dynamic lists from an API, conditional prompts, validation, or a custom menu-style UI. In these cases, use a `preprovision` hook to run a custom script before `azd provision`.

### Understand the flow

The hook approach works through the following chain:

1. A hook script runs and prompts the user with custom menus, validation, or other logic.
1. The script stores values using `azd env set VARIABLE_NAME value`.
1. Values are persisted in `.azure/<env>/.env`.
1. `main.parameters.json` references the values as `${VARIABLE_NAME}`.
1. Bicep receives them as regular parameters during provisioning.

```
azure.yaml (hooks)  →  preprovision script  →  azd env set  →  .azure/<env>/.env
                                                                      |
main.bicep  ←  main.parameters.json references ${VARIABLE_NAME}  ←───┘
```

### Create the hook script

Create a `hooks/preprovision.ps1` file (or `preprovision.sh` for Linux/macOS) that prompts the user and stores values:

```powershell
Write-Host "========================================"
Write-Host "  Custom Pre-Provision Configuration"
Write-Host "========================================"

Write-Host "Available teams:"
Write-Host "  1) platform-engineering"
Write-Host "  2) app-development"
Write-Host "  3) data-science"
Write-Host "  4) devops"
Write-Host "  5) Enter custom value"

$choice = Read-Host "Select a team (1-5)"
$teamName = switch ($choice) {
    "1" { "platform-engineering" }
    "2" { "app-development" }
    "3" { "data-science" }
    "4" { "devops" }
    "5" { Read-Host "Enter custom team name" }
}

# Store in azd environment
azd env set CUSTOM_TEAM_NAME $teamName
```

> [!TIP]
> Make your hook scripts idempotent. Check for an existing value at the top of the script so that re-running `azd up` skips the prompt if a value is already set.

### Map the variable to a Bicep parameter

In your `main.parameters.json` file, reference the environment variable:

```json
{
  "parameters": {
    "customTeamName": {
      "value": "${CUSTOM_TEAM_NAME}"
    }
  }
}
```

In your `main.bicep` file, declare the parameter with a default so `azd` doesn't also prompt for it:

```bicep
@description('Team name - set by preprovision hook')
param customTeamName string = 'unset'
```

### Enable the hook

Add the hook configuration to your `azure.yaml`:

```yaml
hooks:
  preprovision:
    windows:
      shell: pwsh
      run: hooks/preprovision.ps1
      interactive: true
    posix:
      shell: sh
      run: hooks/preprovision.sh
      interactive: true
```

The `interactive: true` setting binds the script to the console so it can read user input. For more information on hook configuration, see [Customize your Azure Developer CLI workflows using command and event hooks](azd-extensibility.md).

> [!NOTE]
> Public templates should include both `.ps1` and `.sh` hook scripts for cross-platform support. If your team uses PowerShell 7 across all platforms, a single `.ps1` with `shell: pwsh` works everywhere.

## Choose the right approach

| Scenario | Approach |
|---|---|
| Pick from a fixed list of values. | `@allowed` decorator (Option 1) |
| Collect free-text input. | Parameter with no default (Option 2) |
| Dynamic lists, API calls, or conditional logic. | Hook script (Option 3) |
| Skip all prompts in CI/CD. | Pre-set values (see following section) |

## Skip prompts in CI/CD

All three options support non-interactive mode. Pre-set values before running `azd` and pass `--no-prompt`:

```bash
# Set hook values
azd env set CUSTOM_TEAM_NAME "platform-engineering"

# Set Bicep parameter values
azd env config set infra.parameters.environmentType "prod"
azd env config set infra.parameters.projectOwner "ci-bot"

# Run with no prompts
azd up --subscription <id> --location eastus --no-prompt
```

If a required value is missing, `azd` reports exactly which parameter is missing and shows the `azd env config set` command needed to fix it.

## Related content

- [Work with Azure Developer CLI metadata for Bicep input parameters](metadata.md)
- [Customize your Azure Developer CLI workflows using command and event hooks](azd-extensibility.md)
- [Work with Azure Developer CLI environment variables](manage-environment-variables.md)
- [Bicep parameters and decorators](/azure/azure-resource-manager/bicep/parameters)
- [Sample repo: azd-custom-parameters](https://github.com/jongio/azd-custom-parameters)
