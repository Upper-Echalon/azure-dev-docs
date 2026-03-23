---
title: Azure Developer CLI (azd) extensions overview
description: Learn what azd extensions are, why to use them, and how to enable, manage, and install extensions in the Azure Developer CLI.
author: alexwolfmsft
ms.author: alexwolf
ms.date: 05/14/2025
ms.service: azure-dev-cli
ms.topic: how-to
ms.custom: devx-track-azdevcli, devx-track-bicep
---

# Azure Developer CLI extensions overview

Azure Developer CLI (`azd`) extensions are modular components that extend the functionality of the Azure Developer CLI. They allow you to add new capabilities, automate workflows, and integrate with other services directly from the CLI. Extensions help you tailor `azd` to evolving team needs and Azure scenarios.

> [!NOTE]
> `azd` extensions are currently in beta.

## Manage extension sources

Extensions are distributed and managed through extension sources, making it easy to discover, install, and update them as your requirements grow.

- Extension sources are file or URL based manifests that provide lists of available `azd` extensions.
- Users can add custom extension sources that connect to private, local, or public registries.
- Extension sources are an equivalent concept to NuGet or Node Package Manager (NPM) feeds and must adhere to the [official extension registry schema](https://github.com/Azure/azure-dev/blob/main/cli/azd/extensions/registry.schema.json).

`azd` provides two extension source registries to help you get started with extensions:

- The **official extension source registry** is preconfigured in `azd` and is hosted at [https://aka.ms/azd/extensions/registry](https://aka.ms/azd/extensions/registry).
- The **development extension registry** can also be added to your `azd` configuration. This opt-in registry contains experimental extensions for internal testing that may or may not become official extensions.

To opt-in for the development registry run the following command:

```bash
# Add a new extension source name 'dev' to your `azd` configuration.
azd extension source add -n dev -t url -l "https://aka.ms/azd/extensions/registry/dev"
```

> [!CAUTION]
> Extensions hosted in the dev registry DO NOT contain signed binaries at the moment.

### Extension source commands

Use the following commands to manage extension sources for your `azd` installation.

**List installed extension sources**

```azdeveloper
azd extension source list
```

**Add a new extension source**

```azdeveloper
azd extension source add -n <name> -t url -l <registry-url>
```

- `-l, --location`: The location of the extension source.
- `-n, --name`: The name of the extension source.
- `-t, --type`: The type of extension source. Supported types are file and url.

**Remove an extension source**

```azdeveloper
azd extension source remove <name>
```

## Manage extensions

Once extensions are enabled and your extension sources are configured, you can install extensions to add new capabilities to `azd`. Visit the [Quickstart - use the AI extension](quickstart-ai-extension.md) article for an example of working with extensions.

**List extensions**

```azdeveloper
azd extension list [flags]
```

- `--installed` Displays a list of installed extensions.
- `--source` Only list extensions from the specified source.
- `--tags` Allows filtering extensions by tags (AI, test)

**Install an extension**

```azdeveloper
azd extension install <extension-names> [flags]
```

Replace `<extension-name>` with the name of the extension you want to install.

- `-v, --version` Specifies the version constraint to apply when installing extensions.
- `-s, --source` Specifies the extension source used for installations.

**Upgrade an extension**

```azdeveloper
azd extension upgrade <extension-name>
```

- `--all` Upgrades all previously installed extensions when specified.
- `-v, --version` Upgrades a specified extension using a version constraint, if provided.
- `-s, --source` Specifies the extension source used for installations.

**Uninstall an extension**

```azdeveloper
azd extension uninstall <extension-name>
```

- `--all` Removes all installed extensions when specified.

## Use azd extensions in dev containers

The Visual Studio Code Dev Containers Feature for `azd` supports an `extensions` option to auto-install specified `azd` extensions during the container build. Extensions configured this way are available immediately when the container starts, reducing manual setup and enabling `azd` commands to run with the required extensions already installed.

To auto-install extensions in a dev container, add the `extensions` option to the `azd` feature entry in your `devcontainer.json` file:

```json
{
    "name": "Azure Developer CLI",
    "image": "mcr.microsoft.com/devcontainers/python:3.10-bullseye",
    "features": {
        "ghcr.io/azure/azure-dev/azd:latest": {
            "extensions": "ai,test"
        }
    }
}
```

The `extensions` value is a comma-separated list of `azd` extension names. Installation occurs during the container build, so the extensions are ready to use as soon as the container starts. After modifying the extensions list, use the **Rebuild and Reopen in Dev Container** command in Visual Studio Code to rebuild the container with the updated extensions.

Learn more about the [azd Dev Container Feature](https://github.com/Azure/azure-dev/tree/main/cli/azd/resources/devcontainer-feature).

## Next steps

- [Quickstart - use the AI extension](quickstart-ai-extension.md)
- [Extension framework readme](https://github.com/Azure/azure-dev/blob/main/cli/azd/docs/extensions/extension-framework.md)
