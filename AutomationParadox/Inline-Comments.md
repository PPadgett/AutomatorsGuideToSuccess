# Inline Comments

Inline Comments is a best practices in Automation, specifically about the use of explaining complex commandlet arguments and/or complix code. Let's break it down:

- **Inline Comments**: These are notes or explanations inserted directly into the code. They're typically meant to explain the purpose, functionality, or any intricacies of the code immediately following or preceding the comment. Inline comments usually occur on the same line as the code they describe, but can also refer to sections of code in their proximity. 

- **Developers should add inline comments to complex code sections**: This statement recommends that whenever code is complex or potentially difficult to understand, developers should include an explanation in the form of an inline comment. Complex code sections can be those that include intricate logic, rely on less-known features of the language, or have some specific behavior that is not obvious from a quick read.

- **This best practice makes the code easier to understand for others**: By including inline comments, developers make their code more accessible and easier to understand for other developers who might work on the code. This could include team members, future maintainers of the code, or even the wider community if the code is open source.

- **Future Proofing**: This refers to the fact that often, even the original developer might forget the details of their own code after some time. By commenting their code, they help their future selves understand their past reasoning, making future modifications or debugging easier.


    #### **Commenting Tips**:
    - *Be Concise*: Your comments should be as short and concise as possible while still effectively communicating what the code does. A good rule of thumb is to keep your comments shorter than the code they explain.

    - *Explain the 'Why', not the 'What'*: Good comments usually explain why something is done a certain way, not what is being done. The code itself should be clear enough to show what it does. If it's not, you might need to refactor the code to make it more readable.

    - *Keep it Relevant*: Only comment where necessary. Overuse of comments can lead to clutter and can make code harder to read. Code that is straightforward or self-explanatory doesn't need to be commented.

    - *Avoid Redundancy*: Comments should not repeat what the code is clearly expressing. They should provide additional insight, not just reiterate what's already apparent from the code.

    - *Keep it Current*: Ensure your comments stay updated with your code. Outdated comments that don't match the code are worse than no comments at all, as they can lead to confusion.

    - *Don't Rely Solely on Comments for Readability*: Your code should be as readable as possible on its own. If your code requires a lot of comments to be understood, it may need refactoring for clarity and simplicity.

    - *Explain Your Assumptions and Decisions*: If you made a specific coding decision based on certain conditions or assumptions, document them in the comments. This can be helpful for understanding the code's context.

    - *Use a Consistent Style*: Follow a consistent style for your comments, like starting each comment with a capital letter and ending it with a period. This makes them easier to read.

    - *Avoid Commenting Out Code*: It can be tempting to comment out code instead of deleting it, but it's better to use version control for this purpose. Commented-out code can lead to confusion.

    - *Use Tools for Generating Documentation*: If your language supports it (like Java, Python, or JavaScript), use tools like Javadoc, Pydoc, or JSDoc to generate documentation from your inline comments.

## Example: Inline Comments

- ### **Example without Comments in Python**:
    > **Note**: 


    ```python
    # Without Comments

    def factorial(n):
        if n == 0:
            return 1
        else:
            return n * factorial(n-1)

    print(factorial(5))
    ```

    The code above might be confusing for someone who doesn't understand recursion or the logic of factorial calculations.

- ### **Example using Comments in Python**:
    Now, let's take the same script, but add some verbose inline comments to explain what each part does:

    ```python
    # With Comments

    def factorial(n):
        # Base case: if n is zero, 
        # the factorial is 1 by definition
        if n == 0:
            return 1
        else:
            # Recursive case: The factorial of n is n times 
            # the factorial of (n-1). Recurse until n is 0.
            return n * factorial(n-1)

    print(factorial(5))  # Calculate and print the factorial of 5
    ```

    The above version of the script includes inline comments to explain what the function does and how it works. It's much easier to understand for someone new to the code or for the original developer who might return to it after a long time. These comments follow Python's PEP 8 style guide, where inline comments start with a '#' and are separated by at least two spaces from the code statement when on the same line.

- ### **Example without Comments in PowerShell**:
    > **Note**: 

    ```powershell
    # Without Comments

    $services = Get-Service
    $services | Export-Csv -Path C:\services.csv -NoTypeInformation
    ```

    This code might be clear for someone who is familiar with PowerShell cmdlets, but someone who is not familiar with them might have difficulty understanding what each line does.

    Now, let's add some verbose inline comments to explain what each part does:

- ### **Example using Comments in PowerShell:**

    ```powershell
    # With Comments

    # Get a list of all services on the system
    $services = Get-Service

    # Export the services list to a CSV file without type information
    # The -NoTypeInformation flag is used to exclude the .NET type 
    # information that is usually included in the CSV file
    $services | Export-Csv -Path C:\services.csv -NoTypeInformation
    ```

    In this commented version of the script, it's explained what each cmdlet does and why the `-NoTypeInformation` flag is used with `Export-Csv`. This can make it easier for someone new to the code (or for the original author revisiting it after a while) to understand its functionality. 

    These comments follow the style guidelines for PowerShell, where inline comments start with a '#' and are typically placed on the line immediately preceding the code that they describe.

- ### **Example without Comments in Bash**:
    > **Note**:

    ```bash
    #!/bin/bash

    # Without Comments

    tar -czf /path/to/destination/backup.tar.gz /path/to/source
    ```

    The code above might be clear for someone who is familiar with the `tar` command, but it might not be clear to others.

    Now, let's add some verbose inline comments to explain what each part does:

- ### **Example using Comments in Bash:**

    ```bash
    #!/bin/bash

    # With Comments

    # Using the 'tar' command to create a gzipped tarball for backup

    # '-c' creates a new archive
    # '-z' compresses the archive with gzip
    # '-f' allows to specify the name of the archive

    # '/path/to/destination/backup.tar.gz' is the destination of our backup
    # '/path/to/source' is the directory we want to back up

    tar -czf /path/to/destination/backup.tar.gz /path/to/source
    ```

    In this commented version of the script, it's explained what each option (`-c`, `-z`, `-f`) does for the `tar` command and what the paths are for. This can make it easier for someone new to the code (or for the original author revisiting it after a while) to understand what it does.

    These comments follow the style guidelines for Bash, where inline comments start with a '#' and are typically placed on the line immediately preceding the code they describe.

In sum, this statement encourages developers to use inline comments in complex parts of their code, as a means to make the code more understandable for themselves in the future and for others who might work on it.

<br>

___
# [Return to The Automator's Guide](../README.md)
