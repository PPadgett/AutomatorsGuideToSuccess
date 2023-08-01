# Bootstrapping

Bootstrapping refers to the process of using a simple system to initiate a more complicated system.

- **Bootstrap Script**: This is an automated script that is used to prepare a server for operation. This script might include various tasks like installing necessary software, setting up users, setting file permissions, and more.

- **Initial Server Setup or Provisioning**: Provisioning refers to the set of actions that prepare a server for operation, making it ready to perform its intended functions. This may include tasks like installing the operating system, configuring the network settings, setting up database systems, etc.

- **Configures the OS for Operational and Security Compliance**: This suggests that the bootstrap script also configures the server's operating system in such a way that it complies with operational and security standards. This could involve setting up monitoring agents to track system performance, antivirus software to protect against malware, and other security measures.

- **Monitoring Agents, Antivirus Agent**: These are specific examples of software that may be set up by the bootstrap script. Monitoring agents help in tracking the performance and activity of the server, and antivirus agents protect the server from malware threats.

- **Best Practices**: Most effective and safest way to use bootstrap scripts and commandlets is through a trusted package manager or secure source, reducing the likelihood of security breaches or failed installations.

    #### **Bootstrapping Tips**:
    - *Automate As Much As Possible*: The main goal of bootstrapping is to reduce manual work and potential errors, and to ensure consistency across multiple deployments. Take the time to identify and automate as many tasks as possible, from system configuration to software installation.

  - *Use Version Control*: Keep your bootstrap scripts in a version control system like Git. This ensures that you can track changes over time, revert back to a previous version if something goes wrong, and collaborate more effectively with your team.

  - *Test Your Scripts*: Test your bootstrap scripts on a regular basis to make sure they still function as expected, especially after making changes. If possible, use automated testing tools to verify your scripts.

  - *Idempotence*: Ensure your scripts are idempotent - meaning they can be run multiple times without changing the result beyond the initial application. This makes your scripts more reliable and less likely to result in unintended side effects.

  - *Use Trusted Sources*: Always use trusted sources for downloading software, packages, or scripts. This reduces the risk of introducing malware or other security threats into your system.

  - *Include a Verification Process*: Also know as a Go-Live Check, After the bootstrap process, include steps to verify that the system was set up correctly. This might include checking that certain software was installed, that services are running, or that files are in the right place.

  - *Keep Up-to-Date:* Make sure your bootstrap scripts are kept up-to-date with the latest versions of software, latest security patches, and changes in system configuration.

  - *Use Existing Tools When Possible*: There are several tools available for bootstrapping (like Chef, Puppet, Ansible, and more). Rather than writing everything from scratch, consider using these tools, which provide robust, tested functionality.

## Example: Bootstrapping

- ### **Example without bootstraping in Python** *via OnPrem CentOS Package Manager*:
    > **Note**: Bypassing bootstrap is much like pushing the Improbability Drive button without calculations. You're tempting fate, and you might end up as a potted petunia or worse, a whale plummeting towards an unsuspecting planet.

    bootstrap script to utilize the local on-prem CentOS package manager (`yum` or `dnf`):

    In this example, you manually update Python using the package manager and execute the required script file.

1. Upgrade Python using the local package manager.

    ```bash
    sudo yum upgrade python3
    ```
2. Install the required packages using pip
Python packages can be installed using pip, which is a package manager for Python. You can install packages one by one using pip. For example:

    ```bash
    pip install numpy
    pip install pandas
    pip install scikit-learn
    ```
2. Set the PYTHONPATH environment variable

    ```bash
    export PYTHONPATH=/path/to/your/python/modules
    ```
    This will set the PYTHONPATH environment variable to the path you specify, allowing Python to find any modules you have in that directory.

- ### **Example using Bootstrapping in Python** *via OnPrem CentOS Package Manager*:

    In this case, we use a bootstrap script to automatically update Python and download & execute the script file.


    ```bash
    #!/bin/bash

    # Define the URL of the script file
    SCRIPT_URL="http://your_local_centos_package_manager_url/script.py"

    # Check if Python is installed and if not, install it
    if ! command -v python3 &> /dev/null
    then
        sudo yum install python3
    fi

    # Upgrade Python
    sudo yum upgrade python3

    # Download the script file
    wget ${SCRIPT_URL} -O script.py

    # Run the Python script
    python3 script.py
    ```

    curl `bootstrap.sh` and run it:

    ```bash
    curl -sS http://your_local_centos_package_manager_url/script.sh | bash
    ```
    Remember to replace `"http://your_local_centos_package_manager_url/script.py"` with the actual URL of your script file.
    
    This will automatically perform all the steps mentioned in the manual process.

- ### **Example Without Bootstrapping in PowerShell** *via gist*
    > **Note**: Much like trying to storm the castle without Westley's plan, skipping bootstrapping your server is a practice most foul. In both cases, the outcome can be disastrous and chaotic, leaving one wishing for a miracle from Miracle Max.

    In this example, you will manually download and run the script file.

1. Set Path and URL
    ```powershell    
    $gitInstallerPath = "$env:TEMP\git-installer.exe"
    $gitDownloadUrl = "https://github.com/git-for-windows/git/releases/download/v2.33.0.windows.2/Git-2.33.0.2-64-bit.exe"
    ```
    
2. Download Git installer
    ```powershell
    Invoke-WebRequest -Uri $gitDownloadUrl -OutFile $gitInstallerPath
    ```

3. Install Git silently
   ```powershell
    Start-Process -FilePath $gitInstallerPath -ArgumentList "/SILENT" -Wait
    ```

4. Remove the Git installer
    ```powershell
    Remove-Item -Path $gitInstallerPath -Force
    ```

- Git is installed by downloading the installer from the official Git for Windows repository and running it silently.


- ### **Example using Bootstrapping in PowerShell** *via gist*

    In this case, we use a bootstrap script to automatically download and execute the script file.

    Here's a simple bootstrap script:

    ```powershell
    # Install Git
    Write-Host "Installing Git..."
    $gitInstallerPath = "$env:TEMP\git-installer.exe"
    $gitDownloadUrl = "https://github.com/git-for-windows/git/releases/download/v2.33.0.windows.2/Git-2.33.0.2-64-bit.exe"

    # Download Git installer
    Invoke-WebRequest -Uri $gitDownloadUrl -OutFile $gitInstallerPath

    # Install Git silently
    Start-Process -FilePath $gitInstallerPath -ArgumentList "/SILENT" -Wait

    # Remove the Git installer
    Remove-Item -Path $gitInstallerPath -Force
    ```


    You can run this bootstrap script by executing it in PowerShell:

    ```powershell
    (Invoke-WebRequest -Uri "https://gist.github.com/user/gist_id/raw").Content | Set-Content -Path "bootstrap.ps1"; & "bootstrap.ps1"

    ```
    In this command:

    - `"Invoke-WebRequest"`   `".Content"` retrieves the content of the downloaded script.

    - `"Set-Content"`  saves the content to a file named bootstrap.ps1.

    - `"bootstrap.ps1"` executes the downloaded script using the & operator.

    Remember to replace `"https://gist.github.com/user/gist_id/raw"` with the actual URL of your script file.

    This approach downloads the script, saves it to a file, and then executes it, all in a single line.

- ### **Example Without Bootstrapping in Bash** *via Ansible*
    > **Note**: Choosing not to bootstrap your server can feel like being in Befuddle Hall, where rooms shift and staircases lead nowhere. You'll be stuck in a befuddling mess of configurations and environments, wishing you'd taken the guidance of the Princess' chariot when you had the chance.

    In this example, you manually download the Ansible playbook and execute it to join the server to a specific Ansible role.

1. Update the system
    ```bash    
    sudo apt update
    sudo apt upgrade -y
    ```

2. Install Ansible
    ```bash
    sudo apt install ansible -y
    ```
3. Create a temporary directory
    ```bash
    mkdir ~/ansible_bootstrap
    cd ~/ansible_bootstrap
    ```

4. Create the inventory file
    ```bash
    echo "[servers]" > inventory
    echo "newly_built_server ansible_host=<IP_ADDRESS> ansible_user=<SSH_USERNAME> ansible_ssh_private_key_file=<PRIVATE_KEY_PATH>" >> inventory
    ```

5.  Create the playbook
    ```bash
    cat <<EOF > playbook.yml
    ---
    - name: Apply Ansible role to the server
    hosts: servers
    become: true
    roles:
        - your_role_name
    EOF
    ```

6. Run the playbook
    ```bash
    ansible-playbook -i inventory playbook.yml
    ```

7. Cleanup
    ```bash
    cd ~
    rm -rf ~/ansible_bootstrap
    ```

    In the above command, replace `inventory` with the path to your inventory file.

- ### **Example With Bootstrapping** *via Aansible*:

    In this case, you use a bootstrap script to automatically download the Ansible playbook and execute it.

    Here's a simple bash bootstrap script:

    ```bash
    #!/bin/bash

    # Variables
    CONTROL_NODE_USER="ansible"
    CONTROL_NODE_IP="control_node_ip"
    SERVER_USER="ubuntu"
    SERVER_IP="new_server_ip"
    INVENTORY_FILE="/home/$CONTROL_NODE_USER/inventory.ini"
    PLAYBOOK_URL="http://fileserver.com/path/to/your/playbook.yml"

    # Update the system
    sudo apt update
    sudo apt upgrade -y

    # Install Python
    sudo apt install python3 -y

    # Add the control node's public SSH key to the authorized keys
    echo "ssh_public_key" >> ~/.ssh/authorized_keys

    # SSH into the control node and add the new server to the Ansible inventory
    ssh -o StrictHostKeyChecking=no $CONTROL_NODE_USER@$CONTROL_NODE_IP "echo -e '[servers]\nnew_server ansible_host=$SERVER_IP ansible_user=$SERVER_USER' >> $INVENTORY_FILE"

    # SSH into the control node and run the Ansible playbook
    ssh -o StrictHostKeyChecking=no $CONTROL_NODE_USER@$CONTROL_NODE_IP "ansible-playbook -i $INVENTORY_FILE $PLAYBOOK_URL"
    ```

    In this script, replace `control_node_ip`, `new_server_ip`, and `ssh_public_key` with the actual IP address of the control node, the new server, and the public SSH key from the control node, respectively.

    You can run this bootstrap script by `curl` to `bootstrap.sh` and executing it in bash:

    ```bash
    curl -sS http://your_local_centos_package_manager_url/bootstrap.sh | bash
    ```

    This script will automatically perform all the necessary steps to set up the new server to be managed by the Ansible control node.

    Remember to replace `"http://fileserver.com/path/to/your/playbook.yml"` with the actual URL of your playbook file.

<br>

___
# [Return to The Automator's Guide](../README.md)
