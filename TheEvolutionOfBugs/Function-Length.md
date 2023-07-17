# Function Length

Function Length, guided by the Single Responsibility Principle, asserts that each programming function or method should not exceed a defined length. In otherwords, a function or method should do one thing and do it well.

- **Readability**: Shorter functions are easier to read and understand. If a function is too long, it can become difficult to follow the flow of the program and to understand what the function is intended to do.

- **Maintainability**: Shorter functions are easier to maintain and debug. If a bug is found, it's much quicker and easier to isolate and fix the problem if the function is short and only performs one specific task.

- **Reusability**: Functions that are concise and perform a single task can be reused more easily in different parts of a program, improving the efficiency of the code and reducing redundancy

    #### **Function Lenght Tips**:

  - *Single Responsibility Principle*: One key principle in software engineering is that a function or method should do one thing and do it well. If you find that a function is performing multiple tasks, consider breaking it up into smaller functions.

  - *Refactor Long Functions*: If a function is becoming too long, consider refactoring it. Look for pieces of code that can be logically grouped together and move them into separate functions.

  - *Avoid Deep Nesting*: Deeply nested conditions or loops can make a function longer and harder to understand. Consider using early returns or breaking the function into smaller functions to reduce the depth of nesting.

  - *Reuse Code*: If you see that similar code is being used in multiple places, consider creating a function for that code. This can reduce the overall amount of code and make it easier to maintain.

  - *Leverage Data Structures*: A smart use of appropriate data structures can often help you reduce the length of your functions. Some algorithms can be significantly simplified by using the right data structure.

## Example: Function Lenght

- ### **Example without Function Lenght in Python**:
    > **Note**:

    Let's take a scenario where we have a list of dictionaries, each representing a student and their details, and we want to perform several operations on this list like, find students who have scored above a certain threshold, and calculate their average score.

    ```python
    # Without "Function Length" Guideline

    def process_students(students):
        high_score_students = []
        total_score = 0
        for student in students:
            if student['score'] > 85:
                high_score_students.append(student)
                total_score += student['score']
        average_score = total_score / len(high_score_students) if high_score_students else 0
        return high_score_students, average_score
    ```

    This function does more than one task (filtering high scoring students and calculating average), making it not follow the single responsibility principle. Let's refactor this:

- ### **Example with Function Lenght in Python**:

    ```python
    # With "Function Length" Guideline

    def filter_high_score_students(students, threshold=85):
        return [student for student in students if student['score'] > threshold]

    def calculate_average_score(students):
        if not students:
            return 0
        total_score = sum(student['score'] for student in students)
        return total_score / len(students)

    # Main processing function
    def process_students(students):
        high_score_students = filter_high_score_students(students)
        average_score = calculate_average_score(high_score_students)
        return high_score_students, average_score
    ```

    In the refactored version, we have split the original function into two separate functions, each performing a distinct task. Now, each function is shorter, easier to read and test, and adheres to the single responsibility principle.

- ### **Example without Function Lenght in PowerShell**:
    > **Note**:

    Let's consider a scenario where we need to find large files in a given directory, and then move these files to another directory.

    ```powershell
    # Without "Function Length" Guideline

    function Process-LargeFiles($sourceDir, $destinationDir, $sizeLimit) {
        $largeFiles = Get-ChildItem $sourceDir -File | Where-Object { $_.Length -gt $sizeLimit }
        foreach ($file in $largeFiles) {
            Write-Host ("Moving {0} to {1}" -f $file.FullName, $destinationDir)
            Move-Item -Path $file.FullName -Destination $destinationDir
        }
        $remainingFiles = Get-ChildItem $sourceDir -File
        Write-Host ("{0} files remain in the source directory." -f $remainingFiles.Count)
    }
    ```

    In the above example, the function `Process-LargeFiles` is doing multiple tasks: finding large files, moving them to another directory, and then counting the remaining files in the source directory.

- ### **Example using Function Lenght in PowerShell**:

    ```powershell
    # With "Function Length" Guideline

    function Get-LargeFiles($sourceDir, $sizeLimit) {
        Get-ChildItem $sourceDir -File | Where-Object { $_.Length -gt $sizeLimit }
    }

    function Move-Files($files, $destinationDir) {
        foreach ($file in $files) {
            Write-Host ("Moving {0} to {1}" -f $file.FullName, $destinationDir)
            Move-Item -Path $file.FullName -Destination $destinationDir
        }
    }

    function Count-Files($sourceDir) {
        $files = Get-ChildItem $sourceDir -File
        Write-Host ("{0} files remain in the source directory." -f $files.Count)
    }

    # Main processing function
    function Process-LargeFiles($sourceDir, $destinationDir, $sizeLimit) {
        $largeFiles = Get-LargeFiles $sourceDir $sizeLimit
        Move-Files $largeFiles $destinationDir
        Count-Files $sourceDir
    }
    ```

    Each function performs a single, well-defined task, which makes the code easier to read, debug, and test.

- ### **Example without Function Lenght in Bash**:
    > **Note**:

    For example, let's consider a script that needs to process a list of files in a directory: count the number of lines in each file, sum them, and finally, print the average number of lines per file.

    ```bash
    # Without "Function Length" Guideline
    function process_files {
        local dir=$1
        local total_lines=0
        local file_count=0
        for file in "$dir"/*; do
            if [ -f "$file" ]; then
                let file_count++
                local lines=$(wc -l < "$file")
                echo "$file has $lines lines"
                let total_lines+=lines
            fi
        done
        local average=0
        if ((file_count > 0)); then
            let average=total_lines/file_count
        fi
        echo "Average lines per file: $average"
    }
    ```

    In the above script, the `process_files` function is doing several things: looping over the files, counting lines in each file, maintaining a total, and calculating an average.

- ### **Example using Function Lenght in Bash**:

    ```bash
    # With "Function Length" Guideline
    function count_file_lines {
        local file=$1
        wc -l < "$file"
    }

    function process_files {
        local dir=$1
        local total_lines=0
        local file_count=0
        for file in "$dir"/*; do
            if [ -f "$file" ]; then
                let file_count++
                local lines=$(count_file_lines "$file")
                echo "$file has $lines lines"
                let total_lines+=lines
            fi
        done
        local average=0
        if ((file_count > 0)); then
            let average=total_lines/file_count
        fi
        echo "Average lines per file: $average"
    }
    ```

    We have split the original function into two separate functions. Each function performs a single, well-defined task. The code is now easier to read and understand. It would also be easier to add error checking or modify behavior for counting lines in a file, without affecting the rest of the script.

- ### **Example without Function Lenght in Terraform** *via Azure*:
    > **Note**:

    Terraform is an infrastructure as code tool that allows you to define and provide data center infrastructure using a declarative configuration language. Although Terraform itself doesn't have the concept of "functions" as in traditional programming languages, it does use modules, which serve a similar purpose in the context of Terraform. 

    Let's look at an example of creating and managing resources in Microsoft Azure with a Terraform module that does not adhere to the "Function Length" guideline:

    ```terraform
    # Without "Function Length" Guideline

    module "resources" {
    source = "./modules/resources"
    
    resource_group_name     = "example-resources"
    location                = "West Europe"

    # Storage Account configuration
    storage_account_name    = "examplestorage"
    account_tier            = "Standard"
    account_replication_type = "GRS"

    # Virtual Network configuration
    vnet_name               = "example-vnet"
    address_space           = ["10.0.0.0/16"]
    subnet_name             = "subnet1"
    subnet_address_range    = ["10.0.1.0/24"]
    }
    ```

    In the above example, the `resources` module is creating multiple Azure resources, including a resource group, a storage account, and a virtual network. This could lead to a very long and complex module file.

- ### **Example using Function Lenght in Terraform** *via Azure*:

    Now, let's refactor this to adhere to the "Single Responsibility Principle" guideline, by splitting it into smaller, more manageable modules:

    ```terraform
    # With "Function Length" Guideline
    module "resource_group" {
    source = "./modules/resource_group"
    
    name     = "example-resources"
    location = "West Europe"
    }

    module "storage_account" {
    source = "./modules/storage_account"
    
    name                    = "examplestorage"
    resource_group_name     = module.resource_group.name
    account_tier            = "Standard"
    account_replication_type = "GRS"
    }

    module "virtual_network" {
    source = "./modules/virtual_network"
    
    name                 = "example-vnet"
    resource_group_name  = module.resource_group.name
    address_space        = ["10.0.0.0/16"]
    subnet_name          = "subnet1"
    subnet_address_range = ["10.0.1.0/24"]
    }
    ```

    In this refactored version, we have split the original module into three separate modules, each creating a different type of Azure resource. Now, each module is shorter, easier to understand and manage, and adheres to the single responsibility principle. 

- ### **Example without Function Lenght in Ansible**:
    > **Note**:

    Ansible Playbooks are simple configuration management and multi-machine deployment system. It uses YAML, which is easy to read and write. Ansible itself doesn't have the concept of "functions", it does use feature called "*Ansible Roles*"

    ```yaml
    # Without "Function Length" Guideline

    - name: Install and start apache
    hosts: webservers
    become: yes
    tasks:
        - name: Install apache
        apt: 
            name: apache2
            state: present
            update_cache: yes
        - name: Start apache service
        systemd:
            name: apache2
            state: started
        - name: Add user
        user: 
            name: webadmin
            state: present
            shell: /bin/bash
        - name: Allow webadmin sudo
        lineinfile:
            dest: /etc/sudoers
            line: 'webadmin ALL=(ALL) NOPASSWD: ALL'
            validate: 'visudo -cf %s'
    ```

    In the above example, the playbook is doing several things: Installing and starting apache, creating a user and adding it to the sudoers file.

- ### **Example using Function Lenght in Ansible**:

    Let's refactor this playbook to adhere to the "Single Responsibility Principle" guideline:

    ```yaml
    # With "Function Length" Guideline
    - name: Install and start apache
    hosts: webservers
    become: yes
    roles:
        - apache
        - users
    ```

    Where `apache` and `users` are separate roles. Each role can be defined in a separate directory with its own tasks, handlers, files, templates, and variables. For example:

    ```bash
    ansible/
        roles/
            apache/
                tasks/
                    main.yml
            users/
                tasks/
                    main.yml
    ```

    And the tasks for each role might look like:

    ```yaml
    # roles/apache/tasks/main.yml
    - name: Install apache
    apt: 
        name: apache2
        state: present
        update_cache: yes

    - name: Start apache service
    systemd:
        name: apache2
        state: started
    ```


    ```yaml
    # roles/users/tasks/main.yml
    - name: Add user
    user: 
        name: webadmin
        state: present
        shell: /bin/bash

    - name: Allow webadmin sudo
    lineinfile:
        dest: /etc/sudoers
        line: 'webadmin ALL=(ALL) NOPASSWD: ALL'
        validate: 'visudo -cf %s'
    ```

    Spliting the original playbook into two separate roles, each doing a specific task. Each role is shorter, easier to manage, and adheres to the single responsibility principle.

Remember, this is a guideline rather than a strict rule. Sometimes it might be necessary for a function to be slightly longer than this. However, in most cases, if a function is exceeding this length, it's an indication that the function might need to be refactored or broken down into smaller, more manageable pieces. Sometimes, a slightly longer function may be more understandable than several shorter functions, depending on the context. It's important to find a balance that works for your specific situation.

<br>

___
# [Return to The Automator's Guide](../README.md#the-evolution-of-bugs-often-ignored-but-critical-aspect-of-scripting)
