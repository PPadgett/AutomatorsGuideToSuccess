# Global Variables

Global Variables common automation engineering guideline for managing the scope of variables within script. Here's a breakdown of what it means:

- **Global Variables**: In programming, a global variable is a variable that can be accessed from anywhere in the code, regardless of the scope. In other words, it is visible to every function and method in your program. This can sometimes lead to unexpected behavior because any part of the program can change the value of the variable.

- **Prohibit the use of Global Variables**: The policy states that the use of global variables is prohibited. The main reason for this is that global variables can make the code difficult to understand and debug. Because global variables are accessible from anywhere in the code, any part of the program can change their values, which can lead to unpredictable results and hard-to-find bugs.

- **Use Local Variables**: Instead of global variables, this policy recommends the use of local variables. A local variable is a variable that's declared within a function or a block and can only be used within that function or block. This makes its behavior more predictable because its scope (where it can be accessed and altered) is limited.

- **Pass them as arguments to functions if needed**: If a function needs to use a variable that was declared outside of it, instead of making the variable global, the guideline suggests passing the variable to the function as an argument. This ensures that only functions that need to use the variable have access to it, which again leads to more predictable behavior and makes the code easier to debug.

## Example: Avoiding Global Variables

- ### **Example of using Global Variables in Python**:
    >**Note**: Using Global Variables? It's akin to unleashing a Pan Galactic Gargle Blaster without considering the consequences. Prepare for a universe of unexpected side effects!

    ```python
    # With using Global variable

    # Global variable
    my_variable = "Global variable value"

    def update_variable():
        # Unintentionally overwrite global variable
        global my_variable
        my_variable = "Updated within function"
        print("Inside function:", my_variable)

    print("Before function call:", my_variable)

    # Call function that updates variable
    update_variable()

    print("After function call:", my_variable)
    ```

    In this script, the variable `my_variable` is first set with a value of "Global variable value". Then a function `update_variable` is defined which also uses a variable named `my_variable` and it's unintentionally defined as global using `global` keyword which results in overwriting of the global variable.

    Output:
    ```
    Before function call: Global variable value
    Inside function: Updated within function
    After function call: Updated within function
    ```

    This indicates that the value of `my_variable` has been changed from "Global variable value" to "Updated within function" because the global variable was unintentionally overwritten in the function.


- ### **Example of using Local Variables and Passing Local Variables as arguments into a function in Python**:

    ```python
    # Without using Global Variable

    # Defining a function
    def print_local(local_var):
        # Accessing the local variable
        print(local_var)

    # Defining a local variable
    local_var = "I'm a local variable!"
    # Passing the local variable as an argument to the function
    print_local(local_var)
    ```
    Output: `I'm a local variable!`
    
    Using local variables and passing them as arguments to a function. It promotes encapsulation and modularization by keeping variables local to specific functions, which enhances code readability and reduces potential naming conflicts. 


- **Passing Function output into another function via parameters in Python**:

    ```python
    # Without using Global Variable

    # Defining a function to calculate square
    def square(n):
        return n * n

    # Defining a function to add five
    def add_five(n):
        return n + 5

    # Call square function and pass its output to add_five function
    squareResult = square(3)
    result = add_five(squareResult)
    print(result)
    ```
    Output: `14`

    In the last example, `square(3)` will return `9`, which is then passed as an argument to `add_five`, resulting in `14`. This is a simple demonstration of using the output of one function as an input to another.

- #### **Example of using Global Variables in PowerShell**:
    > **Note**: Global Variables? It's like trusting Vizzini's poisoned goblet without questioning its contents. Beware the pitfalls of global state, for they can lead to a world of tangled dependencies!

    In PowerShell, variables can have different scopes such as global, local, script, etc. Sometimes, when a variable with the same name is used in a function, the global variable might be unintentionally overwritten.

    ```powershell
    # With using Global variable

    # Global variable
    $global:myVariable = "Global variable value"

    function Update-Variable {
        # Unintentional overwrite of global variable
        $global:myVariable = "Updated within function"
        Write-Host "Inside function: $myVariable"
    }

    Write-Host "Before function call: $myVariable"

    # Call function that updates variable
    Update-Variable

    Write-Host "After function call: $myVariable"
    ```

    In this script, the variable `myVariable` is first set with a value of "Global variable value". Then a function `Update-Variable` is defined which also uses a variable named `myVariable` and it's unintentionally defined as global using `$global:` keyword which results in overwriting of the global variable.

    Output:
    ```
    Before function call: Global variable value
    Inside function: Updated within function
    After function call: Updated within function
    ```
 

    This indicates that the value of `myVariable` has been changed from "Global variable value" to "Updated within function" because the global variable was unintentionally overwritten in the function.


- #### **Example of using Local Variables and Passing into a function in PowerShell**:

    ```powershell
    # Without using Global Variable

    # Defining a function
    function show-local ($Text) {
        # Accessing the local variable
        Write-Output $Text
    }

    # Defining a local variable
    $local_var = "I'm a local variable!"

    # Passing the local variable as an argument to the function
    show-Local -Text $local_var

    ```
    Output: `I'm a local variable!`

    The scope of `$local_var` is restricted to where it's needed. It won't be inadvertently accessed or changed in another part of the script, leading to clearer, less error-prone code.

- #### **Example of Passing Function output into another Function via parameters in PowerShell**:

    ```powershell
    # Without using Global Variable

    # Defining a function to calculate square
    function get-square ($n) {
        return $n * $n
    }

    # Defining a function to add five
    function add-five ($n) {
        return $n + 5
    }

    # Call square function and pass its output to add_five function
    $resultSquare = get-square -n 3
    $result = add-five -n $resultSquare
    Write-Output $result
    ```
    Output: `14`

    In the last example, `get-square -n 3` will return `9`, which is then passed as an argument to `add-five -n $resultSquare`, resulting in `14`. This is a simple demonstration of using the output of one function as an input to another. This method of using function outputs as inputs to other functions enhances code modularity, reusability, and clarity. It is also easier to troubleshoot, as each function performs a well-defined task.

- #### **Example of using Global Variables in Bash**:
    > **Note**: Thats a Global Variable? It's a treacherous path leading to the nightmares arguments. Guard your code's sanity and keep the boundaries of scope intact!

    In Bash, global variables (also known as environment variables) can be unintentionally overwritten within a function. Here's an example:

    ```bash
    #!/bin/bash

    # With using Global variable

    # Global variable
    MY_VARIABLE="Global variable value"

    function update_variable {
        # Unintentionally overwrite global variable
        MY_VARIABLE="Updated within function"
        echo "Inside function: $MY_VARIABLE"
    }

    echo "Before function call: $MY_VARIABLE"

    # Call function that updates variable
    update_variable

    echo "After function call: $MY_VARIABLE"
    ```

    In this script, the variable `MY_VARIABLE` is first set with a value of "Global variable value". Then a function `update_variable` is defined which also uses a variable named `MY_VARIABLE` and unintentionally overwrites the global variable. The output of this script would be:

    ```
    Before function call: Global variable value
    Inside function: Updated within function
    After function call: Updated within function
    ```

    This indicates that the value of `MY_VARIABLE` has been changed from "Global variable value" to "Updated within function" because the global variable was unintentionally overwritten in the function.

- #### **Using Local Variables and Passing Local Variables as arguments into a function**

    ```bash
    #!/bin/bash

    # Without using Global Variable

    # A function that prints a local variable
    print_local() {
        local local_var=$1
        echo $local_var
    }

    # Defining a local variable
    local_var="I'm a local variable!"
    # Passing the local variable as an argument to the function
    print_local $local_var
    ```
    Output: `I'm a local variable!`

    This example represents better practice as the scope of `local_var` is limited to where it's needed - within the `print_local` function. This prevents accidental modifications elsewhere in the script, which could cause unexpected behavior.

- #### **Passing Function output into another function via parameters**

    ```bash
    #!/bin/bash

    # Without using Global Variable

    # Function to square a number
    square() {
        local n=$1
        echo $((n*n))
    }

    # Function to add five
    add_five() {
        local n=$1
        echo $((n+5))
    }

    # Call square function and pass its output to add_five function
    result=$(add_five $(square 3))
    echo $result
    ```
    Output: `14`

    In the last example, `square 3` will return `9`, which is then passed as an argument to `add_five`, resulting in `14`. This demonstration of using the output of one function as an input to another promotes modularity and reusability, which are both key aspects of good programming practice. Additionally, each function has a specific, clearly defined job, making the script easier to understand and debug.

In general, this guideline promotes good automation engineering practices, focusing on code maintainability, predictability, and simplicity of debugging. It's worth mentioning that while this is a common guideline, like all rules in programming, there can be exceptions based on the specific needs of a project. But those exceptions should be handled carefully, with a good understanding of the potential issues that can arise.

<br>

___
# [Return to The Automator's Guide](../README.md#the-evolution-of-bugs-often-ignored-but-critical-aspect-of-scripting)
