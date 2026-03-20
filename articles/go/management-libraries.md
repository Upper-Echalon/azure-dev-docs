---
title: Overview of the Azure SDK for Go management and client libraries
description: In this article, you learn the basic tasks of working with the Azure SDK for Go management and client libraries.
ms.date: 03/13/2026
ms.topic: overview
ms.custom: devx-track-go
ms.devlang: golang
ai-usage: ai-assisted
---

# Overview of the Azure SDK for Go libraries

The Azure SDK for Go includes both management libraries and data plane client libraries. This article provides an overview so you can understand what the libraries are, how they fit into Azure workflows, and where to go next for Go-specific patterns.

## Management libraries

Use the management libraries libraries to provision, configure, and govern Azure resources. They focus on managing the resources themselves rather than the data stored inside them. Management libraries perform *control plane* operations, which manage Azure resources and service configuration. Typical tasks include:

- Creating or updating resource groups, virtual networks, or virtual machines.
- Configuring security settings, identities, access policies, and diagnostics.
- Listing, tagging, and deleting Azure resources across a subscription.
- Automating deployment, cleanup, compliance, and platform operations.

Management library packages have names like `armcompute`, `armnetwork`, and `armkeyvault`. Management libraries are typically used during setup, configuration, and governance phases of an application lifecycle.  For detailed package documentation, search for the package on [pkg.go.dev](https://pkg.go.dev/).

## Client libraries

Use the client libraries when your Go application needs to work with data or runtime surfaces inside an already provisioned Azure service. Client libraries perform *data plane* operations, which work with the data stored in or flowing through a service. Typical tasks include:

- Uploading and downloading blobs from a storage account.
- Sending and receiving messages with Service Bus or Event Hubs.
- Reading, writing, or deleting records in a database.
- Retrieving secrets from Key Vault.
- Executing queries or operations against provisioned resources.

Client library packages have names like `azblob`, `azstorage`, `azsecrets`, `azservicebus`, and `azeventhubs`. Client libraries are typically used after you've already provisioned the underlying Azure service using management libraries. For detailed package documentation, search for the package on [pkg.go.dev](https://pkg.go.dev/).

## Using both management and client libraries

A single Go solution can use both management and client libraries across control and data planes. For example, you might use a management library during setup to create a storage account (control plane), and then use a client library in the application to upload and download blobs (data plane). Understanding the distinction helps you choose the right library for each task in your workflow.

If you want the Go-specific patterns and examples for each plane, see these articles:

- [Use the Azure SDK for Go for control plane operations](control-plane.md).
- [Use the Azure SDK for Go for data plane operations](data-plane.md).

## Installing Go packages

In most projects, you install the Go packages for versioning and dependency management.

To install a Go package, run the `go get` command.

For example, to install the `armcompute` package, run the following command:

```azurecli
go get github.com/Azure/azure-sdk-for-go/sdk/resourcemanager/compute/armcompute
```

In most Go apps, you install the following packages for authentication:

- github.com/Azure/azure-sdk-for-go/sdk/azcore/to
- github.com/Azure/azure-sdk-for-go/sdk/azidentity

## Importing packages into your Go code

Once downloaded, the packages are imported into your app via the `import` statement:

```go
import (
    "github.com/Azure/azure-sdk-for-go/sdk/azcore/to"
    "github.com/Azure/azure-sdk-for-go/sdk/azidentity"
    "github.com/Azure/azure-sdk-for-go/sdk/resourcemanager/compute/armcompute"
)
```
## Authenticating to Azure

To run code against an Azure subscription, you need to authenticate to Azure. The [azidentity](https://pkg.go.dev/github.com/Azure/azure-sdk-for-go/sdk/azidentity) package supports multiple options to authenticate to Azure. These options include client/secret, certificate, and managed identity.

The default authentication option is **DefaultAzureCredential**, which uses the environment variables set earlier in this article. In your Go code, you create an `azidentity` object as follows:

```go
cred, err := azidentity.NewDefaultAzureCredential(nil)
if err != nil {
  // handle error
}
```

For more information about authentication, see [Azure SDK for Go authentication](./sdk/authentication/authentication-overview.md).

## Next steps

For more information about authentication, client construction, long-running operation, and service walkthrough patterns, see the plane-specific articles:

- [Use the Azure SDK for Go for control plane operations](control-plane.md) for management-oriented Go workflows.
- [Use the Azure SDK for Go for data plane operations](data-plane.md) for runtime data access patterns that often follow provisioning.

For examples, see [Azure SDK for Go samples on GitHub](https://github.com/Azure-Samples/azure-sdk-for-go-samples).