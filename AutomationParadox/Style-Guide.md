# Style Guide

Style Guide is a best practice for developers to follow a specific set of guidelines or standards when writing code in a certain language. These guidelines are known as a style guide.

- **Style Guide**: Programming is essentially a set of prescribed standards that dictate how the code should be written and structured. These standards can include conventions on things like indentation, variable naming, the use of white spaces, the placement of braces, commenting, and more. The specific rules can vary greatly depending on the language, organization, or even individual project.

- **Primary Goal**: Following a style guide is to ensure consistency across the codebase. When all developers working on a project adhere to the same style guide, it makes the codebase much easier to read, understand, and maintain, as you don't have to adjust to different coding styles when moving from one part of the project to another.

- **Uniform Coding Style**: Coding Style can prevent some types of bugs and errors, simplify debugging, and make the code more predictable and safer. It can also foster better collaboration and communication within a development team, as everyone understands the 'language' in which the code is written.

    #### **Sytle Guide Tips**:
  - *Indentation and Spacing*: Use a consistent indentation level to represent the structure of your code. Spaces around operators can improve readability.

  - *Code Grouping*: Group related code together. For instance, functions that perform similar tasks can be grouped together, or variables that are used together can be defined together.

  - *Consistent Use of Quotes*: Some languages allow different types of quotes (like single or double quotes) interchangeably. Choose one and stick with it, unless the language style guide specifies a use case for each.

  - *Follow Language-Specific Best Practices*: Each programming language has its own set of best practices. These include language-specific naming conventions, recommended ways of doing certain tasks, etc. It's a good idea to familiarize yourself with these and follow them.

  - *File and Directory Structure*: Having a consistent file and directory structure can make it easier to locate specific pieces of code.

## Example: Style Guide

- ### **Example without Style in Python**:
    > **Note**: No Time for Style? It's as if you're navigating the vastness of the universe without a towel or a babel fish. 

    ```python
    # Without Style Guide

    def calculate(a,b):return a+b
    def say_hello_to(name):
    print('Hello, '+name)
    say_hello_to('Alice')
    print('Sum of 5 and 7 is: ',calculate(5,7))
    ```
    This script does work, but it's not very readable. The style is inconsistent (there's no space between parameters in the first function, but there is in the second) and the layout is not easy to read.
- ### **Example using Style in Python**
    Now, let's rewrite the above script in compliance with PEP 8, which is the style guide for Python code.

    ```python
    # With Style Guide

    def calculate(a, b):
        """Return the sum of a and b."""
        return a + b

    def say_hello_to(name):
        """Print a greeting to 'name'."""
        print(f'Hello, {name}')

    say_hello_to('Alice')
    print('Sum of 5 and 7 is: ', calculate(5, 7))
    ```
    This code is functionally identical to the previous one, but it's much more readable. We have made the following changes to make it comply with PEP 8:

    1. We have put a space after the comma in the parameter list of `calculate`.
    2. We have added docstrings (those lines with triple quotes) to explain what each function does.
    3. We have put the `return` statement in `calculate` on a new line.
    4. We have used an f-string in `say_hello_to`, which is a more readable way to format strings in Python.

    Using a style guide like PEP 8 helps ensure that your code is easy to read and understand, which is especially important when you're working with other people.

- ### **Example without Style in PowerShell**:
    > **Note**: Skipping Style? It's like engaging in a battle of wits without a sharp mind or a sword. Beware the pitfalls of inconsistency and ambiguity, for they can lead to codebase chaos!

    ```powershell
    # Without Style Guide

    function GetSum {param($a,$b)
    $a+$b}
    function SayHello($name){Write-Host "Hello, $name"}
    SayHello -name "Alice"
    Write-Host "Sum of 5 and 7 is: " (GetSum -a 5 -b 7)
    ```
    As with the Python example, this script works but isn't particularly easy to read. The style is inconsistent, and the layout makes the code hard to follow.

- ### **Example using Style in PowerShell**:
    Now, let's rewrite this script in line with the best practices from the PowerShell Practice and Style Guide.

    ```powershell
    # With Style Guide

    function Get-Sum {
        [CmdletBinding()]
        param(
            [Parameter(Mandatory = $true)]
            [int]$a,

            [Parameter(Mandatory = $true)]
            [int]$b
        )

        return $a + $b
    }

    function Say-Hello {
        [CmdletBinding()]
        param(
            [Parameter(Mandatory = $true)]
            [string]$Name
        )

        Write-Host "Hello, $Name"
    }

    Say-Hello -Name "Alice"
    Write-Host "Sum of 5 and 7 is: " (Get-Sum -a 5 -b 7)
    ```
    This code is functionally identical to the previous one, but it's much more readable. We've made the following changes to make it comply with the PowerShell Practice and Style Guide:

    1. Changed function names to Verb-Noun format (a PowerShell best practice).
    2. Added `[CmdletBinding()]` to each function to allow for advanced function capabilities.
    3. Added a `param` block to each function, and gave each parameter a type and a `Mandatory` attribute.
    4. Formatted the layout to make the script easier to read and understand.

    This formatted and cleaner version of the script is easier to read, understand, and maintain. The use of the Verb-Noun naming convention is a common PowerShell best practice and helps improve code readability.

    - ### **Example without Style in Bash**:
    > **Note**: What, no need for Style? is like entering Slumberland without the guidance of King Morpheus. It's a perilous journey where code conventions become vague and dreams of maintainability turn into nightmares. Embrace the structure and clarity of style guides to protect your code's sanity!

    ```bash
    #!/bin/bash

    # Without Style Guide

    function say_hello() {echo "Hello, $1";}
    function calculate() {echo $(($1+$2));}
    say_hello Alice
    echo "Sum of 5 and 7 is: "`calculate 5 7`
    ```

    The script does function, but lacks readability and does not adhere to standard Bash scripting conventions. The style is inconsistent and the structure makes the code more difficult to follow.

    - ### **Example using Style in Bash**:

    Let's refactor this script following the Google's Shell Style Guide for Bash:

    ```bash
    #!/bin/bash

    # With Style Guide

    # This script greets and performs a sum operation.

    # Function to say hello.
    say_hello() {
    local name="$1"
    echo "Hello, ${name}"
    }

    # Function to calculate sum of two numbers.
    calculate() {
    local num1="$1"
    local num2="$2"
    echo $((num1+num2))
    }

    # Main
    main() {
    say_hello "Alice"
    echo "Sum of 5 and 7 is: $(calculate 5 7)"
    }

    main "$@"
    ```

    In this version:

    1. We added comments to describe the script and its functions.
    2. We used the `local` keyword in functions to limit the scope of variables.
    3. We used the `${variable}` notation to be explicit about variable names.
    4. We used the `$(command)` syntax instead of backticks, which is easier to spot and can be nested.
    5. We created a `main` function to encapsulate the high-level logic of the script, improving readability and structure.
    6. We passed the script's arguments to `main` with `"$@"`.

    By following a style guide, the script became more consistent, readable, and easier to maintain. It's crucial, especially in a team environment, where the code needs to be understood by different developers.

So, in summary, the statement is emphasizing the importance of adhering to a common coding style to improve readability and maintainability in the project.


<br>

___
# [Return to The Automator's Guide](../README.md)
