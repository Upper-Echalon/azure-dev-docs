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

Use the management libraries libraries to provision, configure, and govern Azure resources. They focus on managing the resources themselves rather than the data stored inside them. Management libraries perform **control plane** operations, which manage Azure resources and service configuration. Typical tasks include:

- Creating or updating resource groups, virtual networks, or virtual machines.
- Configuring security settings, identities, access policies, and diagnostics.
- Listing, tagging, and deleting Azure resources across a subscription.
- Automating deployment, cleanup, compliance, and platform operations.

Most Go management packages live under `github.com/Azure/azure-sdk-for-go/sdk/resourcemanager/<service>/arm<service>`. They share common SDK building blocks such as Azure Identity credentials, the Azure Core HTTP pipeline, structured errors, and `Begin*` methods for long-running operations.

## Client libraries

Use the client libraries when your Go application needs to work with data or runtime surfaces inside an already provisioned Azure service. Client libraries perform **data plane** operations, which work with the data stored in or flowing through a service. Typical tasks include:

- Uploading and downloading blobs from a storage account.
- Sending and receiving messages with Service Bus or Event Hubs.
- Reading, writing, or deleting records in a database.
- Retrieving secrets from Key Vault.
- Executing queries or operations against provisioned resources.

Client library packages have names like `azblob`, `azstorage`, `azkeyvault/azsecrets`, and `azservicebus`. Like management libraries, they share common SDK building blocks including Azure Identity credentials, the Azure Core HTTP pipeline, and structured error handling. Client libraries are typically used after you've already provisioned the underlying Azure service using management libraries.

## Using both management and client libraries

A single Go solution can use both management and client libraries across control and data planes. For example, you might use a management library during setup to create a storage account (control plane), and then use a client library in the application to upload and download blobs (data plane). Understanding the distinction helps you choose the right library for each task in your workflow.

If you want the Go-specific patterns and examples for each plane, see these articles:

- [Use the Azure SDK for Go for control plane operations](control-plane.md).
- [Use the Azure SDK for Go for data plane operations](data-plane.md).

## Installing packages

In most Go projects, install only the packages you need for the services your application manages. Management packages are versioned Go modules, so add them by using `go get`.

For example, to install a management package plus the common identity dependency:

```azurecli
go get github.com/Azure/azure-sdk-for-go/sdk/azidentity
go get github.com/Azure/azure-sdk-for-go/sdk/resourcemanager/compute/armcompute
```

Many samples also use `github.com/Azure/azure-sdk-for-go/sdk/azcore/to` to populate optional pointer fields in request models.

## General usage pattern

Most management libraries follow the same high-level flow:

1. Create a credential by using the `azidentity` package.
1. Create a typed client for the Azure resource you want to manage.
1. Call create, read, update, delete, or list operations on that client.
1. Use pollers for operations that begin asynchronously.

For example:

```go
cred, err := azidentity.NewDefaultAzureCredential(nil)
if err != nil {
	return err
}

client, err := armcompute.NewVirtualMachinesClient("<subscription ID>", cred, nil)
if err != nil {
	return err
}
```

For more information about authentication, client construction, long-running operation, and service walkthrough patterns, see the plane-specific articles:

- [Use the Azure SDK for Go for control plane operations](control-plane.md) for management-oriented Go workflows.
- [Use the Azure SDK for Go for data plane operations](data-plane.md) for runtime data access patterns that often follow provisioning.

## Finding the right package

When you know the Azure service you want to automate, start with the management module list and then open the corresponding `arm*` package on [pkg.go.dev](https://pkg.go.dev/). Package documentation is the best place to inspect the exact client names, request models, and operation signatures for a specific resource provider.

For example:

- `armresources` for resource groups and generic resource operations.
- `armcompute` for virtual machines and related compute resources.
- `armnetwork` for virtual networks, subnets, and network security resources.
- `armkeyvault` for vault provisioning and configuration.

## Next steps

- [Use the Azure SDK for Go for control plane operations](control-plane.md).
- [Use the Azure SDK for Go for data plane operations](data-plane.md).
- [Azure SDK for Go authentication](./sdk/authentication/authentication-overview.md).
- [Azure SDK for Go samples on GitHub](https://github.com/Azure-Samples/azure-sdk-for-go-samples).