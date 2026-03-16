---
title: Overview of the Azure SDK for Go management and client libraries
description: In this article, you learn the basic tasks of working with the Azure SDK for Go management and client libraries.
ms.date: 03/13/2026
ms.topic: overview
ms.custom: devx-track-go
ms.devlang: golang
---

# Overview of the Azure SDK for Go management libraries

As explained in [What is the Azure SDK for Go?](overview.md), the Azure SDK for Go includes both management libraries and data plane client libraries. This article stays at the overview level so you can understand what the management libraries are, how they fit into Azure workflows, and where to go next for Go-specific patterns.

Management libraries are the packages you use to provision, configure, and govern Azure resources. In Azure documentation, these operations are also called **control plane** operations. For the full list of management libraries, see the [Azure SDK for Go management modules](https://azure.github.io/azure-sdk/releases/latest/mgmt/go.html).

## What management libraries are used for

Use the management libraries when your Go code needs to work with Azure resources themselves rather than the data stored inside them. Typical tasks include:

- Creating or updating resource groups, virtual networks, or virtual machines.
- Configuring security settings, identities, access policies, and diagnostics.
- Listing, tagging, and deleting Azure resources across a subscription.
- Automating deployment, cleanup, compliance, and platform operations.

Most Go management packages live under `github.com/Azure/azure-sdk-for-go/sdk/resourcemanager/<service>/arm<service>`. They share common SDK building blocks such as Azure Identity credentials, the Azure Core HTTP pipeline, structured errors, and `Begin*` methods for long-running operations.

## Control plane and data plane

Azure SDK documentation often uses two related terms:

- **Control plane** operations manage Azure resources and service configuration. For example, creating a storage account, updating a Key Vault access policy, or deleting a resource group.
- **Data plane** operations work with the data or runtime surface inside an already provisioned service. For example, uploading blobs, sending Service Bus messages, or reading Key Vault secrets.

A single Go solution often uses both planes. You might use a management library once during setup to create a storage account, and then use a data plane client in the application path to upload and download blobs.

If you want the Go-specific patterns and examples for each plane, continue with these articles:

- [Use the Azure SDK for Go for control plane operations](control-plane.md)
- [Use the Azure SDK for Go for data plane operations](data-plane.md)

## Installing packages

In most Go projects, you install only the packages you need for the services your application manages. Management packages are versioned Go modules, so you add them with `go get`.

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

- `armresources` for resource groups and generic resource operations
- `armcompute` for virtual machines and related compute resources
- `armnetwork` for virtual networks, subnets, and network security resources
- `armkeyvault` for vault provisioning and configuration

## Next steps

- [Use the Azure SDK for Go for control plane operations](control-plane.md)
- [Use the Azure SDK for Go for data plane operations](data-plane.md)
- [Azure SDK for Go authentication](./sdk/authentication/authentication-overview.md)
- [Azure SDK for Go samples on GitHub](https://github.com/Azure-Samples/azure-sdk-for-go-samples)