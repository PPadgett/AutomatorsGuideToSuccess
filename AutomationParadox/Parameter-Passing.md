# Parameter Passing

Prameters Passing: The ability to pass parameters or arguments to a script and/or Function is a fundamental aspect of scripting and programming, as it allows for reusability and flexibility in your code.

- **Parameters or Arguments**: These are the values that a function, method, or script takes as input to perform its task. For instance, if you have a function that adds two numbers, the numbers to be added would be the parameters or arguments.
  
- **Customizing Script's Behavior**: By passing different parameters or arguments to a function or script, you can alter its behavior. In the above example, by changing the numbers passed to the addition function, you can control what numbers are added together.

- **Input Redirection, Configuration Files, Environment Variables**: Besides directly passing parameters or arguments, there are other ways to provide input to scripts. Input redirection is a technique in shell programming where the input to a script is read from a file instead of the keyboard. Configuration files can be read by a script to determine its behavior. Environment variables are a type of variable that is available system-wide and can be used to affect a script's behavior. These methods can be used alone or in combination with direct parameter passing to provide inputs to a script.


    #### **Parameter Tips**:
  - *Avoid Boolean Parameters*: Boolean parameters suggest the function does more than one thing based on the flag. It might indicate that the function needs to be split into two.

  - *Variable Shadowing*: Avoid creating parameter with the same name as an environment variable, it can lead to confusion and potentially unexpected behavior in your program. This is due to the way scoping works in most scripting and programming languages.

  - *Parameter Count*: The fewer parameters, the better. Try to limit the number of parameters to three or less for functions.

  - *Default Values*: Whenever possible, provide sensible default values for parameters.

  - *Consistency*: Keep consistency in the way parameters are used. This applies both to scripts and functions.    

  - *Validation*: Validate parameters before using them. Check for null values, correct data type, and range (if applicable).

  - *Explicit Over Implicit*: Parameters should be explicit in what they do. Users should not have to guess the purpose or effect of a parameter.

  - *Group Related Parameters*: Group related parameters together for better readability and maintainability.

  - *Order of Parameters*: Arrange parameters in a logical order. Commonly used parameters should appear early in the list. However, it might be beneficial to keep certain parameters together for clarity.

  - *Strongly Typed Parameters*: Prefer strongly typed parameters where applicable.

  - *Varargs (Variable Argument Lists)*: Use varargs sparingly if a function needs to support an arbitrary number of parameters.

  - *Flags and Switches*: For scripts, support flags or switches to make scripts easier to use and more powerful.

  - *Built-in Handling Parameters*: Many scirpting and/or programming languages have libraries, code snippets or built-in ways to handle parameters.

  - *Non-interactive Scripts*: If your script is likely to be used in a non-interactive manner, make sure it fails gracefully if required parameters are missing.

  - *Environment Variables*: Consider allowing parameters to be set via environment variables, which can be useful for scripts that need to be run in different environments.

<br>

## Example: Parameter Passing

- ### **Example without Parameter Passing in Python**:
    > **Note**: Truly, it's the Pan Galactic Gargle Blaster of bad form, a devastating mix that leaves your head spinning and your program staggering.

    ```python
    # Without Parameter Passing
    def main():
        # Get user input
        name = input("Please enter your name: ")
        age = int(input("Please enter your age: "))

        # Use the input values
        print(f"Hello, {name}! You are {age} years old.")

    if __name__ == "__main__":
        main()
    ```

    In this script, instead of getting parameters from the command line, the script asks the user for input and then uses these inputs within the script. When you run the script, it will wait for the user to enter their name and age before it continues.

    This approach is more interactive and is best suited for scripts that will be run manually by a user. For scripts that need to be automated or run in the background, command-line arguments, configuration files, or environment variables are usually more appropriate.
- ### **Example with Parameter Passing in Python**:
  
    In Python, you can accept command line arguments using the `sys` module.
    ```python
    # With Parameter Passing

    import sys

    def main():
        # sys.argv[0] is always the name of the script itself
        # Arguments start from index 1
        for i in range(1, len(sys.argv)):
            print(f"Argument {i} is: {sys.argv[i]}")

    if __name__ == "__main__":
        main()
    ```

    If you save this script as `script.py` and run it from the command line with some arguments, like so:

    ```shell
    python script.py arg1 arg2 arg3
    ```

    The output will be:

    ```shell
    Argument 1 is: arg1
    Argument 2 is: arg2
    Argument 3 is: arg3
    ```

    In this example, `arg1`, `arg2`, and `arg3` are the arguments passed to the script, and `sys.argv` is a list that Python automatically creates that contains these command line arguments.

    >**Note**: for complex command line argument parsing, you might want to use libraries like `argparse` which provide a more sophisticated way to handle command line arguments, including handling different types of arguments, providing help messages, and handling errors.

- ### **Example without Parameter Passing in PowerShell**:
    > **Note**: It might work, but it's hardly a sound strategy. It's like trying to fence left-handed when you're really right-handed, a needless complication that just leaves you vulnerable. 

    ```powershell
    Write-Output "The value of first argument is: $($args[0])"
    Write-Output "The value of second argument is: $($args[1])"
    ```

    In this script, `$args[0]` corresponds to the first argument passed to the script and `$args[1]` corresponds to the second argument.

    You can call this script with arguments like so:

    ```powershell
    PS> .\myscript.ps1 Hello World
    The value of first argument is: Hello
    The value of second argument is: World
    ```

    Note: This method does not support named parameters, so the order of arguments matters. Additionally, it does not support setting parameters as mandatory or optional, nor does it support providing default values for parameters. It's also considered less readable and less self-documenting than using `param`, so it's generally recommended to use `param` when possible.

- ### **Example using Parameter Passing in PowerShell**:

    In PowerShell, you can create scripts that accept parameters using the `param` keyword.

    ```powershell
    # With Parameter Passing

    param(
        [Parameter(Mandatory=$true)]
        [string]$param1,

        [Parameter(Mandatory=$false)]
        [string]$param2 = "default"
    )

    Write-Output "The value of param1 is: $param1"
    if ($param2) {
        Write-Output "The value of param2 is: $param2"
    }
    ```

    In this script:

    - `$param1` is a mandatory parameter, so you have to provide a value for it when you call the script.
    - `$param2` is not mandatory, and if you don't provide a value for it, the script will use the default value "default".

    You can save this script to a file (let's call it `myscript.ps1`), and then you can run it with different parameters like this:

    ```powershell
    PS> .\myscript.ps1 -param1 "Hello" -param2 "World"
    The value of param1 is: Hello
    The value of param2 is: World

    PS> .\myscript.ps1 -param1 "Hello"
    The value of param1 is: Hello
    The value of param2 is: default
    ```

    In the first command, we're passing both `param1` and `param2`. In the second command, we're only passing `param1`, so `param2` uses its default value.

- ### **Example without Parameter Passing in Bash**:
    > **Note**:  It's the Flip Flap Flop of bad practices, taking your code for a wild and unpredictable ride, only to drop it into the abyss of runtime errors.

    ```bash
    #!/bin/bash

    # Without Parameter Passing

    # A simple bash script without parameters

    echo "Hello, World!"
    ```

    This script simply prints "Hello, World!" to the console when run. You don't need to pass any arguments to it. You can run it using the following command (assuming the script is named `hello.sh` and has the necessary execute permissions):

    ```bash
    ./hello.sh
    ```

    The script will output:

    ```
    Hello, World!
    ```

    This is a simple script with no parameters, but even without parameters, Bash scripts can still do a lot. They can interact with the file system, execute other programs, and so on. However, using parameters can make your scripts more flexible and powerful by allowing them to behave differently based on the input they receive.

- ### **Example using Parameter Passing in Bash**:

    ```bash
    #!/bin/bash

    # With Parameter Passing

    # This script takes two command line arguments

    echo "The first argument is: $1"
    echo "The second argument is: $2"
    ```

    In this script, `$1` and `$2` represent the first and second command-line arguments respectively. 

    You can run this script from the command line and pass in two arguments like this:

    ```bash
    ./myscript.sh Hello World
    ```

    When you run the script in this way, it will output:

    ```
    The first argument is: Hello
    The second argument is: World
    ```

    In Bash scripts, the special variable `$0` contains the name of the script itself, `$1` to `$9` are the first 9 additional parameters the script was run with. If you have more than 9 parameters, you can use the `shift` command to access them.


<br>

___
# [Return to The Automator's Guide](../README.md)
