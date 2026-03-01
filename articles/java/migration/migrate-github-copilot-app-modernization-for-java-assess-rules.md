---
title: "Understand assessment coverage by GitHub Copilot Modernization"
titleSuffix: Azure
description: Shows you what are the assessment coverage GitHub Copilot Modernization can detect
author: KarlErickson
ms.author: karler
ms.reviewer: xiadingnnnn
ms.topic: quickstart
ms.date: 01/13/2026
ms.custom: devx-track-java
ms.subservice: migration-copilot
ms.collection: ce-skilling-ai-copilot
ms.update-cycle: 18
---

# Understand assessment coverage by GitHub Copilot Modernization

This document intends to introduce what app assessment of GitHub Copilot Modernization can detect. In general, it can assist on two aspects:
- detect issues in below three domains/aspects that your app modernization journey needs to take care:
  - cloud readiness
  - java upgrade
  - security
- understand your applications especially for legacy ones. we reveal dependencies, technologies used in your applications to help you quickly understand the apps.
In next paragraphs, you can understand each domain's issue coverage in detail. 

## Domain: cloud-readiness

| Domain | Category | Detection Summary | Why Matters |
| :--- | :--- | :--- | :--- |
| **cloud-readiness** | **credential-migration** | Detects hardcoded AWS credentials (`aws_access_key_id`, `aws_secret_access_key`), AWS Secrets Manager usage, and embedded secret management libraries like Spring Cloud Vault. | **Security:** Hardcoded credentials and vendor-specific secret stores are highly vulnerable. Cloud-native applications require centralized, identity-based security to prevent credential theft. |
| **cloud-readiness** | **region-configuration** | Identifies hardcoded AWS region identifiers (`aws.region`, `AWS_REGION`) in code or configuration files. | **Portability:** Hardcoding geographies ties the application to a specific vendor's physical infrastructure, hindering global deployment and resilience. |
| **cloud-readiness** | **storage-migration** | Detects AWS S3 SDK usage (buckets, objects, pre-signed URLs), S3 TransferManager, and Google Cloud Storage client libraries. | **Reliability & Alignment:** These represent vendor-locked object storage dependencies that are incompatible with the target platform's native storage services. |
| **cloud-readiness** | **messaging-service-migration** | Flags dependencies and connection strings for Amazon SQS/SNS, Kafka, RabbitMQ (AMQP), ActiveMQ (Artemis), IBM MQ, TIBCO EMS, Solace PubSub+, Amazon Kinesis, Apache Pulsar, and Google Cloud Pub/Sub. | **Scalability & Reliability:** Legacy messaging brokers often rely on fixed endpoints and disk-based persistence that hinder horizontal scaling and high availability in cloud environments. |
| **cloud-readiness** | **database-migration** | Detects connection strings, drivers, and timeout settings for MongoDB, MySQL, PostgreSQL, MSSQL, Cassandra, MariaDB, Oracle, Db2, Sybase ASE, Firebird, SQLite, Google Firestore, and Google Cloud Spanner. | **Reliability:** Self-managed or non-native databases lack automated cloud scaling. Hardcoded timeouts and fixed retry intervals can cause blocking and "retry storms" during partial outages. |
| **cloud-readiness** | **file-system-management** | Identifies use of relative/absolute paths, home paths (`/home/`), `file://` schemes, and standard Java IO/NIO or Apache Commons IO calls for local storage access. | **Statelessness:** Cloud containers are ephemeral. Writing to a local file system leads to data loss upon instance restarts or scaling operations; persistent data must be externalized. |
| **cloud-readiness** | **local-credential** | Flags Java KeyStore (.jks) files, `KeyStore.load` method calls, and clear-text passwords (`password`, `pwd`) in property or XML files. | **Security Risk:** Sensitive material stored in clear text or local files can be easily compromised if the application environment or configuration files are accessed by unauthorized individuals. |
| **cloud-readiness** | **configuration-management** | Detects `System.getenv`, `System.getProperty`, external `.properties`/`.xml`/`.ini` files, and Windows Registry access for application settings. | **Externalization:** OS-specific storage or local files are not manageable at scale and cannot be updated dynamically without code changes across all instances. |
| **cloud-readiness** | **session-management** | Identifies data storage in `HttpSession` objects and the use of the "distributable" tag in web descriptors. | **Scalability:** Standard HTTP sessions are unsuitable for cloud scaling; state must be externalized to a distributed cache to prevent data loss during traffic shifts between instances. |
| **cloud-readiness** | **remote-communication** | Detects tightly coupled protocols (CORBA, RMI, JCA), unsecured HTTP/FTP protocols, Java Mail API, direct Socket/NIO channel usage, and hardcoded URLs. | **Cloud Compatibility & Security:** Tightly coupled interactions hinder scalability. Unsecured protocols and hardcoded URLs are vulnerable and brittle in dynamic cloud network environments. |
| **cloud-readiness** | **jakarta-migration** | Detects usage of Jakarta/Java EE specific APIs for NoSQL, JPA, Data, WebSockets, and JAX-RS, as well as server-specific artifacts from JBoss EAP, WebLogic, or WebSphere. | **Supportability:** Migrating to a cloud-native runtime requires aligning with modern Jakarta namespaces and removing proprietary application server dependencies to ensure portability. |
| **cloud-readiness** | **containerization** | Flags the absence of a Dockerfile or problematic Dockerfile instructions like `apt-get upgrade`, lowercase syntax, and syntax spacing issues. | **Reliability:** Standardization in container builds is required for stable, reproducible deployments and to ensure images behave predictably across different environments. |
| **cloud-readiness** | **scheduled-job-migration** | Identifies AWS Lambda handlers, Google Cloud Functions, Quartz Scheduler dependencies, and Spring Batch processing workflows. | **Cloud Compute Alignment:** Scheduled jobs and serverless functions must be refactored to use the target cloud's event-driven and serverless compute models to reduce infrastructure overhead. |
| **cloud-readiness** | **apm-migration** | Identifies embedded APM agents and libraries for New Relic, Elastic APM, and Dynatrace. | **Observability:** These tools require specific cloud-platform integration to properly capture telemetry, latency, and health data in a managed environment. |
| **cloud-readiness** | **auth-migration** | Detects SAML/OpenSAML, OAuth 2.0, OpenID, Spring Security, LDAP usage, and legacy webform authentication patterns. | **Modern Identity:** Legacy webform and LDAP auth lack the flexibility and security features (MFA, SSO) of modern claims-based cloud identity providers. |
| **cloud-readiness** | **os-compatibility** | Identifies project dependencies on Windows-specific Dynamic-Link Libraries (.dll files). | **Portability:** DLLs are OS-specific and will not run in standard Linux-based cloud container environments, requiring replacement with cross-platform shared libraries. |

## Domain: java-upgrade

| Domain | Category | Detection Summary | Why Matters |
| :--- | :--- | :--- | :--- |
| **java-upgrade** | **java-version-upgrade** | Identifies usage of non-LTS Java versions (9, 10, 12-16, 19, 20) and legacy versions (1.x through 8, and 11). | **Security & Support:** Older and non-LTS versions contain known vulnerabilities and lack long-term maintenance updates, leaving the infrastructure exposed to attacks. |
| **java-upgrade** | **framework-upgrade** | Detects Spring Boot, Spring Cloud, Spring Framework, and Jakarta EE versions that have reached end-of-OSS support. | **Supportability:** Out-of-date frameworks stop receiving security fixes, making the application a security risk and incompatible with modern cloud-native tools. |
| **java-upgrade** | **deprecated-apis** | Catalogs hundreds of removed or deprecated APIs, including `sun.misc.BASE64`, `Thread.stop`, `SecurityManager` methods, and proprietary hooks from JBoss, Seam 2, WebLogic, and WebSphere. | **Stability & Portability:** Using removed APIs causes runtime crashes on modern JVMs. Proprietary vendor hooks (like WebLogic/JBoss internals) prevent the application from being portable across standard runtimes. |
| **java-upgrade** | **build-tool** | Identifies legacy build systems like Ant (`build.xml`) or Eclipse-specific project configurations (WTP/JEM natures). | **Automation:** Legacy tools lack the standard conventions and dependency management needed for efficient integration into modern CI/CD pipelines. |

## Security Issues
ISO5055 introduction, and below are the CWE issue list scoped as security category in ISO5055. 

## Next steps
- [Working with assessment](migrate-github-copilot-app-modernization-for-java-working-with-assessment.md)
