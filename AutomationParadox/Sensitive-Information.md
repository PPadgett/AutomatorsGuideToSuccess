# Sensitive Information:

Sensitive Information best practices in managing Secrets Keys, specifically when developing scripts. Here's a breakdown of what it means:

- **Sensitive Information**: This term refers to any data that, if exposed, could potentially harm or compromise the security of a system, an individual, or an organization. Examples of sensitive information include passwords, API keys, and so on.

- **Should never be hard coded in scripts**: Hard coding refers to the practice of inputting data directly into a program's source code. If sensitive data like passwords or API keys are hard-coded, they're visible to anyone who can see the source code and can be exposed if the code is leaked, inadvertently published, or pushed to a public repository.

- **Developers should use secure ways to manage secrets**: "Secrets" in this context refer to sensitive data used for authentication or securing communication, like passwords, API keys, or encryption keys. The recommendation here is that these should be managed in secure ways that reduce the risk of exposure.

- **Such as environment variables, credential parameters and/or secure vault services**: This list provides examples of more secure ways to handle secrets:

  - **Environment variables**: These are dynamic values that can be set outside the program, typically within the operating system or the specific execution environment. They can be used to store sensitive data so that they aren't included directly in the source code.

  - **Credential parameters**: This generally means passing credentials into a system or a function as parameters or arguments, rather than hard coding them. This can be done at runtime, preventing the sensitive information from being visible in the source code.

  - **Secure vault services**: These are specialized tools or services designed for securely storing sensitive information, often with encryption. Examples include AWS Secrets Manager, Azure Key Vault, or HashiCorp's Vault. These tools often provide additional capabilities, such as managing access control, auditing usage, and automatically rotating secrets.

## Example: Coding Sensitive Information

- ### **Example of hard coding sensitive information in Python**:
    > **Note**: Hard-Coding Secerts? It's akin to broadcasting your secrets to the Vogons on open interstellar channels.

    ```python
    # Without Managing Secrets

    import psycopg2

    def connect():
        conn = psycopg2.connect(
            dbname="mydb", 
            user="myuser", 
            password="mypassword", 
            host="localhost", 
            port="5432"
        )
        # rest of the code
    ```
    This is insecure, as the username and password are directly visible in the source code.

- ### **Example of Environment Variables with function parameters in Python**:

    ```python
    # With Secrets Managment via Enviorment Variables

    import os
    import psycopg2

    def connect(dbname, user, password, host, port):
        conn = psycopg2.connect(
            dbname=dbname, 
            user=user, 
            password=password, 
            host=host, 
            port=port
        )
        # rest of the code

    # Retrieve the values from environment variables
    dbname = os.getenv('DB_NAME')
    user = os.getenv('DB_USER')
    password = os.getenv('DB_PASSWORD')
    host = os.getenv('DB_HOST')
    port = os.getenv('DB_PORT')

    connect(dbname, user, password, host, port)
    ```

    In the second example, we've removed the sensitive data from the code and instead retrieve it from the environment variables. These variables can be set in the operating system or the deployment environment, keeping the sensitive data out of the source code.

- ### **Example of using Credential Parameters in Python**:

    ```python
    # With Secrets Managment via Credential Parameters

    import psycopg2

    def connect_to_database(dbname, user, password, host, port):
        conn = psycopg2.connect(
            dbname=dbname,
            user=user,
            password=password,
            host=host,
            port=port
        )
        # Rest of the code to interact with the database...

    # Credentials to connect to the database
    dbname = "mydb"
    user = "myuser"
    password = "mypassword"
    host = "localhost"
    port = "5432"

    # Call the function with the credentials as parameters
    connect_to_database(dbname, user, password, host, port)
    ```

    In this example, we're passing the database credentials (dbname, user, password, host, port) as parameters to the function `connect_to_database`. By doing this, we can keep the sensitive information (i.e., the credentials) out of the function itself, making the function more secure and reusable. This approach is more secure than hard-coding the credentials within the function, as it allows the credentials to be managed separately from the code. For instance, in a real-world application, you might retrieve these credentials from environment variables, a configuration file, or a secure vault, rather than defining them directly in your code.

    The use of secure vault services varies based on the specific service, but typically involves using a library or SDK provided by the service to retrieve the sensitive data. For instance, if you were using 

- ###  **Example of Azure Key Vault services in Python**:

    ```python
    # With Secrets Managment via Azure Key Valut

    from azure.keyvault.secrets import SecretClient
    from azure.identity import DefaultAzureCredential
    import psycopg2
    import json

    def get_secret():
        key_vault_name = "myKeyVaultName"
        secret_name = "mySecretName"
        KVUri = f"https://{key_vault_name}.vault.azure.net"

        credential = DefaultAzureCredential()
        client = SecretClient(vault_url=KVUri, credential=credential)

        try:
            retrieved_secret = client.get_secret(secret_name)
        except Exception as e:
            raise Exception("Couldn't retrieve the secret") from e
        else:
            return retrieved_secret.value

    def connect(dbname, user, password, host, port):
        conn = psycopg2.connect(
            dbname=dbname, 
            user=user, 
            password=password, 
            host=host, 
            port=port
        )
        # rest of the code

    # Retrieve the secret (in this case, a JSON string) from Azure Key Vault
    secret = get_secret()

    # Parse the secret to get your credentials
    creds = json.loads(secret)

    dbname = creds['dbname']
    user = creds['user']
    password = creds['password']
    host = creds['host']
    port = creds['port']

    connect(dbname, user, password, host, port)
    ```

    In this example, `DefaultAzureCredential` is used for authenticating to the Azure Key Vault. This could be replaced with other credentials based on the specific application's requirements. Also, the secret stored in Azure Key Vault is assumed to be a JSON string containing the database credentials. The `json.loads(secret)` call is used to parse this JSON string into a Python dictionary.

    Remember to install the Azure SDK for Python (`azure-identity` and `azure-keyvault-secrets`) before running this code:

- ### **Example of hard-coding sensitive information in PowerShell**:
    > **Note**: Hard-coding sensitive secerts? That's a major Heart of Gold security breach—about as wise as leaving your spaceship's airlock wide open in deep space."

    ```powershell
    # Without Managing Secrets

    $server = "localhost"
    $database = "mydb"
    $user = "myuser"
    $password = "mypassword"

    $connectionString = "Server=$server;Database=$database;User Id=$user;Password=$password;"

    # Use the connection string to connect to the database
    # ...rest of the code
    ```

    This is insecure, as the username and password are directly visible in the script.

- ### **Example of Environment Variables in PowerShell:**:

    ```powershell
    # With Secrets Managment via Environment Variables

    $server = $env:DB_HOST
    $database = $env:DB_NAME
    $user = $env:DB_USER
    $password = $env:DB_PASSWORD

    $connectionString = "Server=$server;Database=$database;User Id=$user;Password=$password;"

    # Use the connection string to connect to the database
    # ...rest of the code
    ```
- ### **Exampple of Credential Parameters in PowerShell**:

    ```powershell
     # With Secrets Managment via Credential Parameters

    param(
        [Parameter(Mandatory=$true)]
        [string]$server,
        [Parameter(Mandatory=$true)]
        [string]$database,
        [Parameter(Mandatory=$true)]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.CredentialAttribute()]
        $credential
    )

    #Set Connection String with Given Credentails
        $connectionstring = "Server=$($server);Database=$database;User Id=$($Credential.UserName);Password=$($Credential.GetNetworkCredential().Password);"

    # Use the connection string to connect to the database
    # ...rest of the code
    ```

    In this example, the script is expecting three parameters: `server`, `database`, `credential`, which are used to set the values for constructing the connection string. 

    Running the script, you would call this script from the command line like so:

    ```powershell
    .\myscript.ps1 -server "localhost" -database "mydb" -credential "myuser"
    ```
- ### **Example of Azure Key Vault in PowerShell**:
    In this case, we'll assume you have a secret named `dbConnectionString` stored in Azure Key Vault that contains the entire connection string for the database:

    ```powershell
    # With Secrets Managment via Azure Key Vault

    # Import the necessary module
    Import-Module Az.KeyVault

    # Connect to Azure
    Connect-AzAccount

    # Get the secret from Azure Key Vault
    $connectionString = (Get-AzKeyVaultSecret -VaultName "myKeyVaultName" -Name "dbConnectionString").SecretValueText

    # Use the connection string to connect to the database
    # ...rest of the code
    ```

    In this example, the sensitive data is securely stored in Azure Key Vault and retrieved using the Az module for PowerShell. Please replace `"myKeyVaultName"` and `"dbConnectionString"` with your Azure Key Vault name and the name of your secret respectively.

    Before running this script, make sure you have installed the Azure PowerShell module (`Az`) and you have necessary permissions to access the secrets in Azure Key Vault.

- ### **Example of hard-coding sensitive information in Bash**:
    > **Note**: Hard-coding Secerts? It's a perilous choice that can lead to a never-ending maze of security breaches and data nightmares. Guard your secrets like the keys to the Dream Castle!

    ```bash
    #!/bin/bash

    # Without Managing Secrets

    USER='myuser'
    PASSWORD='mypassword'
    DATABASE='mydatabase'
    HOST='localhost'

    mysql -u $USER -p$PASSWORD -h $HOST -D $DATABASE
    ```

    This is insecure, as the username and password are directly visible in the script.

- ### **Example of Environment Variables in Bash**:

    ```bash
    #!/bin/bash

    # With Secrets Managment via Environment Variables

    USER=$DB_USER
    PASSWORD=$DB_PASSWORD
    DATABASE=$DB_NAME
    HOST=$DB_HOST

    mysql -u $USER -p$PASSWORD -h $HOST -D $DATABASE
    ```

    In this case, the credentials are not hard-coded in the script but are retrieved from environment variables.

- ### **Example of Credential Paramaters in Bash**:

    ```bash
    #!/bin/bash

    # With Secrets Managment via Credential Paramaters

    # Retrieve the values from the command line arguments
    USER=$1
    PASSWORD=$2
    DATABASE=$3
    HOST=$4

    mysql -u $USER -p$PASSWORD -h $HOST -D $DATABASE
    ```

    In this example, the script is expecting four command-line arguments, which are used to set the values of the `USER`, `PASSWORD`, `DATABASE`, and `HOST` variables. 

    Running the script, you would call this script from the command line like so:

    ```bash
    ./myscript.sh myuser mypassword mydatabase localhost
    ```
    

- ### **Example of Azure Key Vault in Bash**
    Now, let's use Azure Key Vault to securely store and retrieve the credentials. In this case, we'll use the Azure CLI (`az` command). Note that this assumes that you have Azure CLI installed and configured correctly:

    ```bash
    #!/bin/bash
    # With Secrets Managment via EAzure Key Vault 

    # Get the secret (i.e., password) from Azure Key Vault
    PASSWORD=$(az keyvault secret show --name mySecretName --vault-name myKeyVaultName --query value -o tsv)

    USER=$DB_USER
    DATABASE=$DB_NAME
    HOST=$DB_HOST

    mysql -u $USER -p$PASSWORD -h $HOST -D $DATABASE
    ```

    In this script, the `PASSWORD` variable is set to the value of a secret retrieved from Azure Key Vault using the `az` command. Replace `'mySecretName'` and `'myKeyVaultName'` with the name of your secret and your Azure Key Vault name, respectively. Also, make sure that you have necessary permissions to retrieve the secret from Azure Key Vault.

In essence, it's crucial to handle sensitive information securely in automation development to prevent data breaches and other security issues.

<br>

___
# [Return to The Automator's Guide](../README.md)
