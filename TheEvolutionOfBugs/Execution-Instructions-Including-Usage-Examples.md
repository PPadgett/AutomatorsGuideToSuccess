# Execution Instructions Including Usage Examples

Execution & Usage Examples are a common practices in Automation Development. When a function or script is written, it's often accompanied by comments or documentation that explain what it does, what inputs it expects, what output it returns, and examples of how to use it.

- **Execution Instructions**: This refers to a step-by-step guide on how to run a specific function or script. It tells the user what inputs to provide, how to initiate the execution, and what to expect as a result.

- **Usage Examples**: These are practical instances of how the function or script can be used. This typically includes snippets of code showing the function or script being called with specific inputs and demonstrating the expected output.

- **For each function and/or script, should be provided**: This suggests that such instructions and examples should be given for every function or script in the software, not just a few.

    #### **Execution & Usage Examples Tips**:
    - *Start with a Brief Description*: Before diving into the details, provide a brief overview of what the function, module, or task does. This helps to set the context.

    - *Be Specific*: When describing parameters or steps to execute a function or script, be specific. Describe the type, range, or possible values for each parameter.

    - *Include All Steps*: Don't skip steps when providing execution instructions, even if they seem obvious. Remember, the goal is to make it easy for someone unfamiliar with your code to understand it.

    - *Use Examples*: Include practical examples demonstrating how the function or script should be used. Use a variety of examples to cover different use cases, if possible.

    - *Keep It Simple*: Try to use simple and clear language in your instructions and examples. Avoid jargon and complex language that could confuse readers.

    - *Keep It Updated*: Whenever you update your code, remember to also update your instructions and examples. Out-of-date instructions can lead to confusion and mistakes.

    - *Use Code Comments*: If your language supports it, use code comments for your instructions and examples. This ensures they stay close to the code they're describing.

    - *Follow the Style Guidelines*: If there are style guidelines for your language (like PEP 257 for Python), follow them. This ensures your instructions and examples are consistent with what other developers expect.

    - *Include Error Handling*: Describe what errors or exceptions can be thrown by your function and how to handle them.

    - *Use Tools*: Some Integrated Development Environments (IDEs) or text editors can generate stub comments for you when you define a new function. Use these to help structure your instructions and examples.

## Example Execution Instructions including Usage Examples:

- ### **Example without Execution Instructions or Usage Examples in Python**:

    ```python
    def rectangle_area(length, width):
        return length * width
    ```

    In the above example, there's no documentation. If someone who wasn't familiar with the function's purpose or how it's used were to see this, they may not understand what it does or how to use it.

- ### **Example with Execution Instructions and Usage Examples in Python**:

    ```python
    def rectangle_area(length, width):
        """
        Calculate the area of a rectangle.

        Execution Instructions:
        Call this function with two arguments, both of which should be numbers (either integers or floats).
        - length: The length of the rectangle.
        - width: The width of the rectangle.
        This function returns a number (float or integer) representing the area of the rectangle.

        Usage Examples:
        >>> rectangle_area(5, 4)
        20
        >>> rectangle_area(5.5, 4.3)
        23.65
        """

        return length * width
    ```

    In the second example, we've added a docstring (triple quoted string at the start of the function). This docstring provides execution instructions and usage examples for the function. Anyone who reads this will understand what the function does, what parameters it requires, what it returns, and how it can be used.

- ### **Example without Execution Instructions or Usage Examples in PowerShell**:

    ```powershell
    function Get-TextFiles($directory) {
        Get-ChildItem -Path $directory -Filter "*.txt"
    }
    ```

    In this example, the function is defined without any comments or instructions. While it might be clear for the one who wrote it, it may not be as clear for other developers.

- ### **Example with Execution Instructions and Usage Examples in PowerShell**:

    ```powershell
    <#
    .SYNOPSIS
        A function to get all the text files in a directory.

    .DESCRIPTION
        This function takes a directory path as a parameter and retrieves all text files present in the directory.

    .PARAMETER directory
        The path of the directory in which to look for text files.

    .EXAMPLE
        PS C:\> Get-TextFiles -directory "C:\Users\Username\Documents"
        This command gets all text files in the Documents directory of the current user.

    .EXAMPLE
        PS C:\> Get-TextFiles -directory "C:\Temp"
        This command gets all text files in the Temp directory.
    #>
    function Get-TextFiles {
        param (
            [Parameter(Mandatory=$true)]
            [string]$directory
        )

        Get-ChildItem -Path $directory -Filter "*.txt"
    }
    ```

    In this second example, I've added a comment block above the function definition following the PowerShell comment-based help guidelines. This comment block includes execution instructions and usage examples for the function. Now, anyone reading the code can understand its purpose, the input it requires, and how to use it.



- ### **Example without Execution Instructions or Usage Examples in Bash**:

    ```bash
    list_files() {
        directory=$1
        ls -l $directory
    }
    ```

    This is a simple function, but without comments or instructions, its usage may not be entirely clear to someone new to the code.

- ### **Example with Execution Instructions and Usage Examples in Bash**:

    ```bash
    # list_files
    # This function lists all the files in a directory.
    # 
    # Execution Instructions:
    # Call this function with the directory path as the argument.
    # 
    # Usage Examples:
    # list_files /home/user/documents
    # list_files /etc/
    #
    # Here, '/home/user/documents' and '/etc/' are the directory paths.
    #
    list_files() {
        # The directory path is the first argument to the function
        directory=$1

        # List all files in the provided directory
        ls -l $directory
    }
    ```

    In this second example, we have added comments that describe the purpose of the function, how to execute it, and also provided usage examples. These comments greatly improve the readability and maintainability of the code. 

    > *Note*: Bash does not have a formal style guide for comments like Python or PowerShell do, but it's still good practice to include useful comments and examples.

- ### **Example without Execution Instructions or Usage Examples in Terraform**:

    Terraform itself doesn't have functions in the same way that programming languages like Python or Bash do. In Terraform, you typically define resources or modules. For the sake of this exercise, let's use an example of a module.



    ```terraform
    module "s3_bucket" {
    source  = "terraform-aws-modules/s3-bucket/aws"
    version = "~> 2.0"

    bucket = "my-s3-bucket"
    acl    = "private"

    versioning = {
        enabled = true
    }
    }
    ```

    This example module is relatively straightforward, but without comments or instructions, it might not be immediately clear what each parameter does.

- ### **Example with Execution Instructions and Usage Examples in Terraform**:

    ```terraform
    /*
    Module: s3_bucket

    Description:
    Creates an Amazon S3 bucket with specified settings. 

    Execution Instructions:
    1. Update the "bucket" parameter with your desired bucket name.
    2. Adjust the "acl" parameter for the appropriate access control list setting.
    3. Set the "versioning" parameter as desired to enable or disable versioning.

    Usage Examples:
    # To create a bucket with the name 'my-s3-bucket', with 'private' acl, and versioning enabled
    module "s3_bucket" {
    source  = "terraform-aws-modules/s3-bucket/aws"
    version = "~> 2.0"

    bucket = "my-s3-bucket" # replace with your desired bucket name
    acl    = "private"      # can be 'private', 'public-read', etc.

    versioning = {
        enabled = true  # set to 'false' to disable versioning
    }
    }
    */
    module "s3_bucket" {
    source  = "terraform-aws-modules/s3-bucket/aws"
    version = "~> 2.0"

    bucket = "my-s3-bucket"
    acl    = "private"

    versioning = {
        enabled = true
    }
    }
    ```

    In this example with comments, we explain the purpose of the module, provide execution instructions, and give a usage example with explanation on how to adapt the settings. This helps to clarify the code's function and usage for future developers or maintainers.

- ### **Example without Execution Instructions or Usage Examples in Ansible**

    Ansible doesn't have "functions" in the same way a programming language would, but it does have tasks and roles that are somewhat analogous.    

    ```yaml
    ---
    - name: Install packages
    apt:
        name: "{{ packages }}"
        state: present
    vars:
        packages:
        - 'nginx'
        - 'git'
    ```

    This example is relatively straightforward, but without comments or instructions, its purpose and usage might not be immediately clear.

- ### **Example with Execution Instructions and Usage Examples in Ansible**:

    ```yaml
    ---
    # Task: Install packages
    #
    # Description:
    # This task installs specified packages using the apt package manager.
    #
    # Execution Instructions:
    # Specify the packages to be installed under the 'packages' variable as a list. 
    # The 'state' is set to 'present' to ensure the packages are installed.
    #
    # Usage Examples:
    # - To install 'nginx' and 'git', use the following configuration:
    #   vars:
    #     packages:
    #     - 'nginx'
    #     - 'git'
    #
    - name: Install packages
    apt:
        name: "{{ packages }}"
        state: present
    vars:
        packages:
        - 'nginx' # replace or add more packages as needed
        - 'git'
    ```

    In this example, we've added comments to provide execution instructions and usage examples for this task. The instructions explain how to specify the packages to be installed, and the usage example shows how to install 'nginx' and 'git'. This makes the playbook much easier to understand and modify.

The goal of these practices is to aid new developers or anyone who might be using or maintaining the code in the future. Having this information readily available helps developers understand how they can utilize the existing functions or scripts, saving them time and reducing the potential for mistakes.

<br>

___
# [Return to The Automator's Guide](../README.md#the-evolution-of-bugs-often-ignored-but-critical-aspect-of-scripting)
