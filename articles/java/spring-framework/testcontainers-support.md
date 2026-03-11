---
title: Spring Cloud Azure support for Testcontainers
description: Describes how to integrate Spring Cloud Azure with Testcontainers to write effective integration tests for your applications.
ms.date: 08/19/2025
author: KarlErickson
ms.author: karler
ms.reviewer: seal
ms.topic: reference
ms.custom: devx-track-java, devx-track-extended-java
appliesto:
- ✅ Version 5.25.0
- ✅ Version 6.1.0
- ✅ Version 7.1.0
---

# Spring Cloud Azure support for Testcontainers

This article describes how to integrate Spring Cloud Azure with [Testcontainers](https://testcontainers.com/) to write effective integration tests for your applications.

*Testcontainers* is an open-source framework for providing throwaway, lightweight instances of databases, message brokers, web browsers, or just about anything that can run in a Docker container. It integrates with JUnit, enabling you to write a test class that can start up a container before any of the tests run. Testcontainers is especially useful for writing integration tests that talk to a real backend service.

The `spring-cloud-azure-testcontainers` library now supports integration testing for the following Azure services:

- [Azure Cosmos DB](https://azure.microsoft.com/products/cosmos-db/)
- [Azure Blob Storage](https://azure.microsoft.com/products/storage/blobs/)
- [Azure Queue Storage](https://azure.microsoft.com/products/storage/queues/)
- [Azure Event Hubs](https://azure.microsoft.com/products/event-hubs/)
- [Azure Service Bus](https://azure.microsoft.com/products/service-bus/)

## Service connections

A service connection is a connection to any remote service. Spring Boot's autoconfiguration can consume the details of a service connection and use them to establish a connection to a remote service. When doing so, the connection details take precedence over any connection-related configuration properties.

When you use Testcontainers, you can automatically create connection details for a service running in a container by annotating the container field in the test class.

The `@ServiceConnection` annotation is processed by `xxxContainerConnectionDetailsFactory` classes registered with `spring.factories`. These factories create a `ConnectionDetails` bean based on a specific `Container` subclass or the Docker image name.

The following table provides information about the connection details factory classes supported in the `spring-cloud-azure-testcontainers` JAR:

| Connection details factory class                | Connection details bean              |
|-------------------------------------------------|--------------------------------------|
| `CosmosContainerConnectionDetailsFactory`       | `AzureCosmosConnectionDetails`       |
| `StorageBlobContainerConnectionDetailsFactory`  | `AzureStorageBlobConnectionDetails`  |
| `StorageQueueContainerConnectionDetailsFactory` | `AzureStorageQueueConnectionDetails` |
| `EventHubsContainerConnectionDetailsFactory`    | `AzureEventHubsConnectionDetails`    |
| `ServiceBusContainerConnectionDetailsFactory`   | `AzureServiceBusConnectionDetails`   |

## Set up dependencies

The following configuration sets up the required dependencies:

### [Cosmos](#tab/test-for-cosmos)

```xml
<dependency>
  <groupId>org.testcontainers</groupId>
  <artifactId>azure</artifactId>
</dependency>
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-testcontainers</artifactId>
</dependency>
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-starter-cosmos</artifactId>
</dependency>
```

### [Blob Storage](#tab/test-for-storage-blob)

```xml
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-testcontainers</artifactId>
</dependency>
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-starter-storage-blob</artifactId>
</dependency>
```

### [Queue Storage](#tab/test-for-storage-queue)

```xml
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-testcontainers</artifactId>
</dependency>
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-starter-storage-queue</artifactId>
</dependency>
```

### [Event Hubs](#tab/test-for-event-hubs)

```xml
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-testcontainers</artifactId>
</dependency>
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-starter-eventhubs</artifactId>
</dependency>
```

### [Service Bus](#tab/test-for-service-bus)

```xml
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-testcontainers</artifactId>
</dependency>
<dependency>
  <groupId>com.azure.spring</groupId>
  <artifactId>spring-cloud-azure-starter-servicebus</artifactId>
</dependency>
```

---

## Use Testcontainers

The following code example demonstrates the basic usage of Testcontainers:

### [Cosmos](#tab/test-for-cosmos)

```java
@SpringBootTest
@Testcontainers
@ImportAutoConfiguration(classes = { AzureGlobalPropertiesAutoConfiguration.class, AzureCosmosAutoConfiguration.class})
public class CosmosTestcontainersTest {

    @TempDir
    private static File tempFolder;

    @Autowired
    private CosmosClient client;

    @Container
    @ServiceConnection
    static CosmosDBEmulatorContainer cosmos = new CosmosDBEmulatorContainer(
    DockerImageName.parse("mcr.microsoft.com/cosmosdb/linux/azure-cosmos-emulator:latest"));

    @BeforeAll
    static void setup() {
        cosmos.start();
        Path keyStoreFile = new File(tempFolder, "azure-cosmos-emulator.keystore").toPath();
        KeyStore keyStore = cosmos.buildNewKeyStore();
        try {
            keyStore.store(Files.newOutputStream(keyStoreFile.toFile().toPath()), cosmos.getEmulatorKey().toCharArray());
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    
        System.setProperty("javax.net.ssl.trustStore", keyStoreFile.toString());
        System.setProperty("javax.net.ssl.trustStorePassword", cosmos.getEmulatorKey());
        System.setProperty("javax.net.ssl.trustStoreType", "PKCS12");
    }

    @Test
    void test() {
        // ...
    }
}
```

To use `CosmosDBEmulatorContainer`, we need to prepare a `KeyStore` for TLS/SSL. For more information, see [Cosmos DB Azure Module](https://java.testcontainers.org/modules/azure/#cosmosdb) in the Testcontainers documentation. With `@ServiceConnection`, this configuration enables Cosmos DB-related beans in the app to communicate with Cosmos DB running inside the Testcontainers-managed Docker container. This action is done by automatically defining a `AzureCosmosConnectionDetails` bean, which is then used by the Cosmos DB autoconfiguration, overriding any connection-related configuration properties.

### [Blob Storage](#tab/test-for-storage-blob)

```java
@SpringBootTest
@Testcontainers
@ImportAutoConfiguration(classes = { AzureGlobalPropertiesAutoConfiguration.class, AzureStorageBlobAutoConfiguration.class, AzureStorageBlobResourceAutoConfiguration.class})
public class StorageBlobTestcontainersTest {

    @Container
    @ServiceConnection
    private static final GenericContainer<?> AZURITE_CONTAINER = new GenericContainer<>(
        "mcr.microsoft.com/azure-storage/azurite:latest")
        .withExposedPorts(10000);

    @Value("azure-blob://testcontainers/message.txt")
    private Resource blobFile;

    @BeforeAll
    static void setup() {
        AZURITE_CONTAINER.start();
    }

    @Test
    void test() {
        // ...
    }
}
```

With `@ServiceConnection`, this configuration enables blob-related beans in the app to communicate with Blob Storage running inside the Testcontainers-managed Docker container. This action is done by automatically defining a `AzureStorageBlobConnectionDetails` bean, which is then used by the Blob Storage autoconfiguration, overriding any connection-related configuration properties.

### [Queue Storage](#tab/test-for-storage-queue)

```java
@SpringBootTest
@Testcontainers
@TestPropertySource(properties = "spring.cloud.azure.storage.queue.queue-name=devstoreaccount1/tc-queue")
@ImportAutoConfiguration(classes = { AzureGlobalPropertiesAutoConfiguration.class, AzureStorageQueueAutoConfiguration.class})
public class StorageQueueTestcontainersTest {

    @Container
    @ServiceConnection
    private static final GenericContainer<?> AZURITE_CONTAINER = new GenericContainer<>(
        "mcr.microsoft.com/azure-storage/azurite:latest")
        .withExposedPorts(10001);

    @Autowired
    private QueueClient queueClient;

    @BeforeAll
    static void setup() {
        AZURITE_CONTAINER.start();
    }

    @Test
    void test() {
        // ...
    }
}
```

With `@ServiceConnection`, this configuration enables queue-related beans in the app to communicate with Queue Storage running inside the Testcontainers-managed Docker container. This action is done by automatically defining an `AzureStorageQueueConnectionDetails` bean, which is then used by the Queue Storage autoconfiguration, overriding any connection-related configuration properties.

### [Event Hubs](#tab/test-for-event-hubs)

```java
@SpringJUnitConfig
@TestPropertySource(properties = {
    "spring.cloud.azure.eventhubs.event-hub-name=eh1"
})
@Testcontainers
class EventHubsContainerConnectionDetailsFactoryTests {

    private static final Network NETWORK = Network.newNetwork();

    @Container
    private static final AzuriteContainer AZURITE = new AzuriteContainer("mcr.microsoft.com/azure-storage/azurite:latest")
        .withNetwork(NETWORK)
        .withNetworkAliases("azurite");

    @Container
    @ServiceConnection
    private static final EventHubsEmulatorContainer EVENT_HUBS = new EventHubsEmulatorContainer(
        "mcr.microsoft.com/azure-messaging/eventhubs-emulator:latest")
        .acceptLicense()
        .withCopyFileToContainer(MountableFile.forClasspathResource("eventhubs/Config.json"),
            "/Eventhubs_Emulator/ConfigFiles/Config.json")
        .withNetwork(NETWORK)
        .withAzuriteContainer(AZURITE);

    @Autowired
    private AzureEventHubsConnectionDetails connectionDetails;

    @Autowired
    private EventHubProducerClient producerClient;

    @Test
    void connectionDetailsShouldBeProvidedByFactory() {
        assertThat(connectionDetails).isNotNull();
        assertThat(connectionDetails.getConnectionString())
            .isNotBlank()
            .startsWith("Endpoint=sb://");
    }

    @Test
    void producerClientCanSendMessage() {
        // Wait for Event Hubs emulator to be fully ready and event hub entity to be available
        waitAtMost(Duration.ofSeconds(120)).pollInterval(Duration.ofSeconds(2)).untilAsserted(() -> {
            EventData event = new EventData("Hello World!");
            this.producerClient.send(Collections.singletonList(event));
        });
    }

    @Configuration(proxyBeanMethods = false)
    @ImportAutoConfiguration(classes = {AzureGlobalPropertiesAutoConfiguration.class,
        AzureEventHubsAutoConfiguration.class})
    static class Config {
    }
}
```

With `@ServiceConnection`, this configuration enables related beans in the app to communicate with Event Hubs running inside the Testcontainers-managed Docker container. This action is done by automatically defining an `AzureEventHubsConnectionDetails` bean, which is then used by the Event Hubs autoconfiguration, overriding any connection-related configuration properties.

### [Service Bus](#tab/test-for-service-bus)

```java
@SpringJUnitConfig
@TestPropertySource(properties = { "spring.cloud.azure.servicebus.entity-name=queue.1",
    "spring.cloud.azure.servicebus.entity-type=queue" })
@Testcontainers
@SuppressWarnings("deprecation")
class ServiceBusContainerConnectionDetailsFactoryTests {

    private static final Network NETWORK = Network.newNetwork();

    private static final MSSQLServerContainer<?> SQLSERVER = new MSSQLServerContainer<>(
        "mcr.microsoft.com/mssql/server:2022-CU14-ubuntu-22.04")
        .acceptLicense()
        .withNetwork(NETWORK)
        .withNetworkAliases("sqlserver");

    @Container
    @ServiceConnection
    private static final ServiceBusEmulatorContainer SERVICE_BUS = new ServiceBusEmulatorContainer(
        "mcr.microsoft.com/azure-messaging/servicebus-emulator:latest")
        .acceptLicense()
        .withCopyFileToContainer(MountableFile.forClasspathResource("servicebus/Config.json"),
            "/ServiceBus_Emulator/ConfigFiles/Config.json")
        .withNetwork(NETWORK)
        .withMsSqlServerContainer(SQLSERVER);

    @Autowired
    private AzureServiceBusConnectionDetails connectionDetails;

    @Autowired
    private ServiceBusSenderClient senderClient;

    @Autowired
    private ServiceBusTemplate serviceBusTemplate;

    @Test
    void connectionDetailsShouldBeProvidedByFactory() {
        assertThat(connectionDetails).isNotNull();
        assertThat(connectionDetails.getConnectionString())
            .isNotBlank()
            .startsWith("Endpoint=sb://");
    }

    @Test
    void senderClientCanSendMessage() {
        // Wait for Service Bus emulator to be fully ready and queue entity to be available
        waitAtMost(Duration.ofSeconds(120)).pollInterval(Duration.ofSeconds(2)).untilAsserted(() -> {
            this.senderClient.sendMessage(new ServiceBusMessage("Hello World!"));
        });

        waitAtMost(Duration.ofSeconds(30)).untilAsserted(() -> {
            assertThat(Config.MESSAGES).contains("Hello World!");
        });
    }

    @Test
    void serviceBusTemplateCanSendMessage() {
        // Wait for Service Bus emulator to be fully ready and queue entity to be available
        waitAtMost(Duration.ofSeconds(120)).pollInterval(Duration.ofSeconds(2)).untilAsserted(() -> {
            this.serviceBusTemplate.sendAsync("queue.1", MessageBuilder.withPayload("Hello from ServiceBusTemplate!").build()).block();
        });

        waitAtMost(Duration.ofSeconds(30)).untilAsserted(() -> {
            assertThat(Config.MESSAGES).contains("Hello from ServiceBusTemplate!");
        });
    }


    @Configuration(proxyBeanMethods = false)
    @ImportAutoConfiguration(classes = {AzureGlobalPropertiesAutoConfiguration.class,
        AzureServiceBusAutoConfiguration.class,
        AzureServiceBusMessagingAutoConfiguration.class})
    static class Config {

        private static final Set<String> MESSAGES = ConcurrentHashMap.newKeySet();

        @Bean
        ServiceBusRecordMessageListener processMessage() {
            return context -> {
                MESSAGES.add(context.getMessage().getBody().toString());
            };
        }

        @Bean
        ServiceBusErrorHandler errorHandler() {
            // No-op error handler for tests: acknowledge errors without affecting test execution.
            return (context) -> {
            };
        }

    }
}
```

With `@ServiceConnection`, this configuration enables related beans in the app to communicate with Service Bus running inside the Testcontainers-managed Docker container. This action is done by automatically defining an `AzureServiceBusConnectionDetails` bean, which is then used by the Service Bus autoconfiguration, overriding any connection-related configuration properties.

---

## Samples

For more information, see the [azure-spring-boot-samples](https://github.com/Azure-Samples/azure-spring-boot-samples/tree/main/spring-cloud-azure-testcontainers) repository on GitHub.
