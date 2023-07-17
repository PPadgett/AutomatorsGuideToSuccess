# Strong Typing

Strong typing refers to a property of a programming/scripting language that emphasizes strict data type checks and enforcement at compile and/or run-time.

- **Type Enforcement**: Once a variable is declared with a certain data type in a strongly-typed language, it cannot hold values of any other data type. For example, if you declare a variable as an integer, you can't assign a string to it.

- **Compile and/or Run-time Checks**: In strongly-typed languages, type errors can often be caught at compile time or script parsing time. This means that for compiled languages, the program won't even compile if you try to perform an operation that's not appropriate for the data type of the variable, such as trying to concatenate a string with an integer. For scripting languages like PowerShell, these checks may occur when the script is parsed or a function is invoked. 

- **Preventing Runtime Errors and Ensuring Correctness**: By catching type-related errors prior to the actual execution of the program or a specific operation, both developers and system engineers are enabled to rectify their mistakes more promptly. This practice enhances code reliability and reduces the chances of unanticipated behavior or system crashes due to type inconsistencies at runtime.

- **Code Readability and Maintainability**: When reading the code, you know exactly what type each variable is, which can make the code easier to understand and maintain. This is particularly valuable in large code bases or when working on a team.

    #### **Strong Type Tips**:
    - *Leverage Type Checking Tools*: In languages that support type hints or annotations, such as Python or TypeScript, use tools like Mypy or the TypeScript compiler to catch type errors before the code is executed.

    - *Avoid Using Magic Numbers or Strings*: Use typed constants or enum types instead. This improves code readability and ensures type safety.

    - *Utilize IDE Features*: Modern IDEs and text editors can infer types in certain situations, and can warn you about potential type mismatches. This can be particularly helpful in languages with static, strong typing.

    - *Write Tests for Type-Related Bugs*: When fixing a bug related to types, write a test that catches the bug. This will help you catch if the same type error is introduced in the future.

    - *Prefer Interfaces/Protocols Over Concrete Types*: When designing functions or classes, consider accepting interfaces/protocols instead of concrete types. This makes your code more flexible and modular.

## Example: Strong Typing

- #### **Example Without Strong Typing (Type Hints) in Python** *:
    > **Note**:

    While Python is a dynamically-typed language, meaning that types are checked at runtime rather than compile-time, it is still a strongly-typed language, as it doesn't implicitly convert one data type into another unless such a conversion is explicitly defined. Python 3.5 introduced optional type hints that can be used to signify the expected types of a function's arguments and return value. 

    ```python
    # Without Strong Typing
    def add(a, b):
        return a + b
    ```

    In this function, we don't specify what `a` and `b` should be. They could be numbers, strings, lists, etc. While Python is still strongly typed and will raise an error if you try to add incompatible types (like a string and an integer), there's no indication to the user what types `a` and `b` should be, and the error will only occur at runtime.

- #### **Example Using Strong Typing (Type Hints) in Python**:
  
    ```python
    # With Strong Typing

    def add(a: int, b: int) -> int:
        return a + b
    ```
    In this function, we specify that `a` and `b` should both be integers, and the function will return an integer. This can help catch potential bugs at an earlier stage of development, as many Integrated Development Environments (IDEs) and linters will highlight if you try to pass the wrong type to the function. It also makes the function easier to understand for other developers.

    > Note: *Python's type hints are still hints and don't enforce the type at runtime. To have compile-time type checks like in statically-typed languages, you would need to use a static type checker like Mypy.* 


- #### **Example Without Strong Typing in PowerShell**:
    > **Note**:

    PowerShell is a dynamically typed language, but you can leverage strong typing by specifying data types for your function parameters.

    ```powershell
    # Without Strong Typing

    function Add($a, $b) {
        return $a + $b
    }
    ```
    In this function, there is no data type specified for `a` and `b`. They could be any type of data, such as integers, strings, or arrays. The operator `+` behaves differently depending on the data type, so the result of `Add` will vary based on the input, and potential errors won't be caught until runtime.

- #### **Example Using Strong Typing in PowerShell**:


    ```powershell
    # With Strong Typing

    function Add([int]$a, [int]$b) {
        return $a + $b
    }
    ```
    In this function, `a` and `b` are strongly typed as integers. This means that if you try to pass a non-integer value to the function, PowerShell will attempt to convert it to an integer. If it cannot, it will throw an error. This can help catch potential errors earlier and makes the expected use of the function more clear to other developers.

- #### **Example Without Strong Typing (Simulated) in Bash**:
    > **Note**:

    Bash, like other shell scripting languages, is weakly typed and does not support strong typing directly. However, there are ways to enforce a semblance of strong typing by manually checking the data types within the function.

    ```bash
    # Without Strong Typing

    add() {
        echo $(($1 + $2))
    }
    ```

    This function will attempt to add the two parameters passed to it regardless of their types. If non-numeric strings are passed, this function will cause an error.

- #### **Example using Strong Typing (Simulated) in Bash**:

    ```bash
    # With Strong Typing

    add() {
        if [[ $1 =~ ^[0-9]+$ ]] && [[ $2 =~ ^[0-9]+$ ]]; then
            echo $(($1 + $2))
        else
            echo "Error: Both arguments must be integers."
        fi
    }
    ```
    In this function, we add a preliminary check to ensure that both arguments are integers. The `=~` operator in Bash is a regular expression match operator, and `^[0-9]+$` will match any string that entirely consists of one or more digits. This means that if non-integer values are passed to the function, the function will print an error message rather than attempting to perform arithmetic on non-integer values.

    This is not strong typing in the traditional sense, as it is a manual check performed at runtime rather than automatic enforcement by the language at compile time, but it can provide some of the benefits of strong typing in terms of preventing type-related errors.

    >Note: *Bash, due to its nature as a shell scripting language, doesn't have built-in support for strong typing, and such tricks are more of a workaround than a best practice. For larger, more complex programs, a more fully-featured scripting or programming language might be more appropriate.*


- #### **Example Without Strong Typing (Context) in Terraform**:
    > **Note**:

    Terraform is an Infrastructure as Code (IaC) tool that allows you to build, change, and version infrastructure safely and efficiently. It uses HashiCorp Configuration Language (HCL) for its configuration files, which supports strong typing for variables.

    However, the context of strong typing in Terraform is slightly different from traditional programming languages, since Terraform configuration files do not contain typical functions. Instead, they consist of resources, data sources, providers, variables, and outputs. The primary context in which you would consider typing in Terraform is when defining variables and the values you pass to resources, data sources, etc.

    ```terraform
    # Without Strong Typing

    variable "instance_count" {
    description = "Number of instances to create"
    }

    resource "aws_instance" "example" {
    count = var.instance_count
    // other configurations...
    }
    ```

    In this example, `instance_count` is a variable with no type specified, so it can be any type that Terraform supports. If a non-numeric value is provided, Terraform will throw an error at runtime when trying to assign it to the `count` parameter, which expects a number.

- #### **Example Using Strong Typing (Context) in Terraform**:

    ```terrafrom
    # With Strong Typing

    variable "instance_count" {
    description = "Number of instances to create"
    type        = number
    }

    resource "aws_instance" "example" {
    count = var.instance_count
    // other configurations...
    }
    ```

    In this example, `instance_count` is strongly typed as a number. If a non-numeric value is provided, Terraform will throw an error when processing the variables, before it even begins to create or modify resources. This can help catch errors earlier in the process.

    Please note that the enforcement of strong typing in Terraform happens at runtime (when `terraform apply` or `terraform plan` is run).

<br>

Remember, the goal of using strong typing is to prevent bugs and make your code easier to understand and maintain. Each language has different features, so it's important to understand how strong typing works in the particular language you're using.

<br>

___
# [Return to The Automator's Guide](../README.md#the-evolution-of-bugs-often-ignored-but-critical-aspect-of-scripting)
