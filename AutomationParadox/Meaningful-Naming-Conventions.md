# Meaningful Naming Conventions

Meaningful Naming Conventions is a crucial aspect of good programming practices. This concept can be broken down as follows:

- **Verbose Names**: This refers to using descriptive and informative names for variables, functions, and classes in your code. Verbose names should ideally reflect the purpose or behavior of the variables, functions, or classes they represent, making it much easier for anyone reading the code (including yourself at a later date) to understand what each part of the code is doing without having to delve into the specifics of how it's implemented.

- **Consistency in Naming**: This aspect of meaningful naming conventions refers to the idea that similar entities in your code should be named in a similar manner. Consistency makes it easier to understand and navigate your code. This can involve using a specific style (like camelCase or snake_case), adhering to certain prefixes or suffixes (like "is" for boolean variables or "Handler" for function names), or following other agreed-upon conventions that are in place.

## Example: Meaningful Naming Conventions

- ### **Example without Meaningful Naming Conventions in Python**:

    > **Note**: Skipping Naming Conventions? It's akin to communicating with Vogons using a broken Babelfish translator. Prepare for a universe of confusion and misunderstandings!

    ```python
    # Without Meaningful Naming Conventions

    def f(a):
        b = []
        for c in a:
            if c % 2 == 0:
                b.append(c)
        return b

    d = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    e = f(d)
    print(e)
    ```

    In this code, it's not immediately clear what `f`, `a`, `b`, `c`, `d`, and `e` are representing. You need to read and understand the code in the function to know that it's filtering even numbers from a list.


- ### **Example using Meaningful Naming Conventions in Python**:
    Now, let's see how we could rewrite this example using meaningful naming conventions:

    ```python
    # With Meaningful Naming Conventions

    def filter_even_numbers(number_list):
        even_numbers = []
        for number in number_list:
            if number % 2 == 0:
                even_numbers.append(number)
        return even_numbers

    input_numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    even_numbers = filter_even_numbers(input_numbers)
    print(even_numbers)
    ```

    In this refactored version, it's much easier to understand what each function, variable, and argument is supposed to represent:

    - The function `filter_even_numbers` clearly indicates it filters even numbers from a provided list.
    - The variable `input_numbers` clearly holds some input numbers.
    - The variable `even_numbers` inside the function is clearly used to store the even numbers found.
    - The variable `even_numbers` outside the function clearly is meant to hold the result of the function.

    This example demonstrates how using meaningful naming conventions can make your code easier to read and understand.

- ### **Example without Meaningful Naming Conventions in PowerShell**:

    > **Note**: No time for robust variable! its as puzzling as trying to solve the riddle of the Fire Swamp without a clue. Beware the ambiguity that lurks in poorly named variables!


    ```powershell
    # Without Meaningful Naming Conventions

    function f ($a) {
        $b = @()
        foreach($i in $a){
            if($i % 2 -eq 0){
                $b += $i
            }
        }
        return $b
    }

    $d = 1..10
    $e = f -a $d
    Write-Output $e
    ```

    This code is similar to the Python code in the previous example, but translated to PowerShell. It's not clear what `f`, `a`, `b`, `i`, `d`, and `e` are supposed to represent.

- ### **Example using Meaningful Naming Conventions in PowerShell**:
    Now, let's refactor this code according to PowerShell's meaningful naming conventions:

    ```powershell
    # With Meaningful Naming Conventions

    function Get-EvenNumbers ($numberArray) {
        $evenNumbers = @()
        foreach($number in $numberArray){
            if($number % 2 -eq 0){
                $evenNumbers += $number
            }
        }
        return $evenNumbers
    }

    $inputNumbers = 1..10
    $evenNumbers = Get-EvenNumbers -numberArray $inputNumbers
    Write-Output $evenNumbers
    ```

    In this refactored version:

    - The function `Get-EvenNumbers` clearly indicates it gets even numbers from a provided array.
    - The parameter `$numberArray` and the variable `$number` inside the function both clearly indicate they're related to numbers.
    - The variable `$evenNumbers` is clearly used to store the even numbers found.
    - The variable `$inputNumbers` clearly holds some input numbers.
    - The output variable `$evenNumbers` is meant to hold the result of the function.

    This makes the code more readable and maintainable, which is the aim of following meaningful naming conventions.

- ### **Example without Meaningful Naming Conventions in Bash**:
    > **Note**: I've always done it this way! It's a confusing path filled with the creatures of sloppy code and tangled logic. Stay true to the language of clarity and guide your code through the realm of comprehension!

    ```bash
    #!/bin/bash

    # Without Meaningful Naming Conventions

    f() {
    local a b=()
    for a in "${@}"; do
        if (( a % 2 == 0 )); then
        b+=("$a")
        fi
    done
    echo "${b[@]}"
    }

    d=(1 2 3 4 5 6 7 8 9 10)
    e=$(f "${d[@]}")
    echo "${e[@]}"
    ```

    In this code, `f`, `a`, `b`, `d`, and `e` are not meaningful names. You would need to read and understand the code to know that `f` is a function that filters out even numbers from a list.

- ### **Example using Meaningful Naming Conventions in Bash**:
    Now, let's refactor this code according to meaningful naming conventions:

    ```bash
    #!/bin/bash

    # With Meaningful Naming Conventions

    filter_even_numbers() {
    local number even_numbers=()
    for number in "${@}"; do
        if (( number % 2 == 0 )); then
        even_numbers+=("$number")
        fi
    done
    echo "${even_numbers[@]}"
    }

    input_numbers=(1 2 3 4 5 6 7 8 9 10)
    even_numbers=$(filter_even_numbers "${input_numbers[@]}")
    echo "${even_numbers[@]}"
    ```

    In this refactored version, the code is more readable:

    - The function `filter_even_numbers` makes it clear that it's filtering even numbers from a provided list.
    - The `number` variable inside the function is clearly related to a number from the list.
    - The `even_numbers` variable is used to store the even numbers found.
    - The `input_numbers` variable clearly holds the input numbers.
    - The `even_numbers` variable outside the function is meant to hold the result of the function.

    This improves the readability and maintainability of the code, which is the goal of using meaningful naming conventions.

Adhering to these principles can significantly enhance the readability and maintainability of your code, making it easier to understand, debug, and extend in the future. These principles apply to any scripting and/or programming language, and are a part of general good coding practices.

<br>

___
# [Return to The Automator's Guide](../README.md)
