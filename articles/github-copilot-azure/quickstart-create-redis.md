---
title: "Quickstart: Create and deploy an app using Azure Cache for Redis using GitHub Copilot for Azure"
description: "Create a prompt in GitHub Copilot for Azure that creates and deploys an instance of Azure Cache for Redis, and a Python app that writes and reads from it."
author: bobtabor-msft
ms.author: rotabor
ms.service: github-copilot-for-azure
ms.topic: quickstart  #Don't change
ms.date: 2/28/2026

---
  
# Quickstart: Create and deploy an app using Azure Cache for Redis using GitHub Copilot for Azure

This quickstart shows you how to create a simple Python app that:

- Connects to **Azure Cache for Redis**
- Writes the current date and time to Redis
- Reads the value back
- Prints the result to the console

You use **Visual Studio Code**'s **GitHub Copilot** chat to generate most of the code and provisioning steps.

## Prerequisites

For complete setup instructions, see the [Get started](get-started.md) article. Make sure that you have the following items:

[!INCLUDE [ghcpa-prerequisites](includes/prerequisites.md)]

## Building the app

The approach is:

- Creating a user-level `.env` file to store Azure deployment information as environment variables
- Writing a prompt to create an instance of Azure Cache for Redis in your subscription, which includes a local-level `.env` file to store Azure Cache for Redis connection information as environment variables
- Validating that the resource and the `.env` file are created correctly
- Writing a prompt to create a Python app to retrieve, write, and read from the cache by using environment variables
- Validating the app works
- Cleaning up the resources in Azure

### Create local environment variables

A common development practice is to store important keys and other settings as environment variables in a `.env` file. Several methods exist to do this, but many developers choose to put these variables in `.env` files.

Store user-level `.env` files in a folder that only the current user can access. A common location is `%USERPROFILE%.env`. On Windows systems, that location is typically `c:\users\<user name>`. On Linux and macOS systems, that location is typically `~/.env` or some other location.

Create a `.env` file in the appropriate location and copy the following values, replacing them with your specific values:

```dotenv
AZURE_SUBSCRIPTION_ID=<your-azure-subscription-id>
AZURE_TENANT_ID=<your-azure-tenant-id>
AZURE_LOCATION=eastus
AZURE_RESOURCE_GROUP=<resource-group>
AZURE_RESOURCE_PREFIX=<resource-prefix>
```

These values are used by Copilot for Azure to provision resources. If you're unsure what to replace the `<placeholder>` values with, refer to the following table.

| Variable | What to put |
| --- | --- |
| `AZURE_SUBSCRIPTION_ID` | Your subscription ID (find via `az account show`) |
| `AZURE_TENANT_ID` | Your Azure AD tenant ID |
| `AZURE_LOCATION` | Preferred region, such as `eastus` or `westus2` |
| `AZURE_RESOURCE_GROUP` | Default resource group name |
| `AZURE_RESOURCE_PREFIX` | Short prefix to namespace resources |

### Create Azure Cache for Redis

1. Open GitHub Copilot Chat in Visual Studio Code and paste the following prompt:

   ```prompt
   You have access to Azure MCP tools.
  
   Create an Azure Cache for Redis instance using these variables from %USERPROFILE%/.env:
  
   AZURE_SUBSCRIPTION_ID
   AZURE_LOCATION
   AZURE_RESOURCE_GROUP
   AZURE_RESOURCE_PREFIX
   
   Tasks:
   1. Ensure the resource group exists.
   2. Create Azure Cache for Redis:
       - Name: {AZURE_RESOURCE_PREFIX}-redis
       - SKU: Basic C0
       - TLS enabled (port 6380)
   3. Write the following values into the project's `.env`:
       REDIS_HOST
       REDIS_PORT=6380
       REDIS_PASSWORD (primary key)
       REDIS_SSL=true
  
   Important:
   - Use Azure MCP to create resources and fetch keys where possible.
   - Show the Azure CLI commands as well, but prefer MCP actions.
   - Output the final values (host/key) clearly so I can paste them into a .env file.
   ```

   Copilot creates the Redis resource, and then creates a `.env` file containing the hostname, primary key, and the other environment variables.

### Validate that the .env file has the Redis settings

1. Open the `.env` file in your project folder and validate that it has values:

   ```dotenv
   REDIS_HOST=<your-cache-name>.redis.cache.windows.net
   REDIS_PORT=6380
   REDIS_PASSWORD=<primary-key>
   REDIS_SSL=true
   ```

1. Copy and submit the following prompt.

   ```prompt
   Use the values in the `.env` file in this workspace to validate that an instance of Azure Cache for Redis is running and ready to be used.
   ```

### Prompt to write the Python app

Use the following prompt to create the Python app that writes and reads from the new instance of Azure Cache for Redis.

```prompt
Create a minimal Python console app in this workspace.

Important:
- Do ALL work directly by editing files.
- Do NOT ask me to copy/paste code.
- Create files if they do not exist.

Goal:
Build a simple app that writes the current date/time to Azure Cache for Redis, reads it back, and prints results to the console.

Project requirements:

1. Create or update these files:

- main.py
- requirements.txt
- .gitignore

2. requirements.txt must include:
- redis
- python-dotenv

3. .gitignore must include:
- .venv/
- __pycache__/
- .env

4. main.py must:

- Load environment variables using python-dotenv
- Read:
    REDIS_HOST
    REDIS_PORT
    REDIS_PASSWORD
    REDIS_SSL
- Connect to Azure Cache for Redis using TLS (ssl=True when REDIS_SSL=true)
- Use decode_responses=True
- Test connection with PING and print:
    Connected to Redis
- Write current datetime (ISO format) to key:
    demo:timestamp
- Read the value back
- Print exactly:

    WROTE: <value>
    READ : <value>

- Wrap connection logic in a try/except and print a helpful error message.

5. Keep the code simple and beginner-friendly:
- Single file
- No classes
- About 40–60 lines

After editing the files:
- Show a summary of what you changed.
- Do NOT print the full file contents unless I ask.
```

### Validate the Python app

1. In Visual Studio Code's Explorer view, make sure the files you requested in the prompt exist. Visually inspect the files to see if they have values that seem reasonable.

1. Inspect the `main.py` file to ensure that it retrieves values from the `.env` file, imports the `redis` package, and connects to Azure Cache for Redis. Check that it writes and reads the cache. You might see code that resembles the following:

   ```python
   
   import os
   from datetime import datetime
   from dotenv import load_dotenv
   import redis
   
   # Load local environment variables
   load_dotenv()
   
   host = os.getenv("REDIS_HOST")
   port = int(os.getenv("REDIS_PORT", "6380"))
   password = os.getenv("REDIS_PASSWORD")
   ssl_enabled = os.getenv("REDIS_SSL", "true").lower() == "true"
   
   try:
       client = redis.Redis(
           host=host,
           port=port,
           password=password,
           ssl=ssl_enabled,
           decode_responses=True
       ) 
   
       # Verify connection
       client.ping()
       print("Connected to Redis")
   
       # Write current time
       now = datetime.now().isoformat()
       client.set("demo:timestamp", now)
       print(f"WROTE: {now}")
   
       # Read value back
       value = client.get("demo:timestamp")
       print(f"READ : {value}")
   
   except Exception as ex:
       print("Connection failed.")
       print(ex)
   ```

### Run the app

1. In the terminal, run the app:

   ```bash
   python main.py
   ```
  
   You should see output similar to this:

   ```output
   Connected to Redis
   WROTE: 2026-03-01T10:22:11.452331
   READ : 2026-03-01T10:22:11.452331
   ```

## Clean up resources

Use the following prompt:

```prompt
I am finished with this instance. Please remove the Azure Cache for Redis that you created earlier by using the values in the `.env` file. ONLY remove this resource and nothing else.
```
