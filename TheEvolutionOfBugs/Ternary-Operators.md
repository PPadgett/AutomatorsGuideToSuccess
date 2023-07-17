# Ternary Operators

Ternary Operators as a substitute for simple if-else conditions in programming to increase the readability of the code.

- **Ternary Operators**: A ternary operator is a kind of operator used in most programming languages. It's called "ternary" because it takes three operands: a condition, a result for when the condition is true, and a result for when the condition is false.

- **Use ternary operators instead of if-else statements**: This is a recommendation to use ternary operators as a substitute for if-else statements in your code. If-else statements can get lengthy and complex, and replacing them with ternary operators can help reduce the amount of code you write.

- **For simpler conditions**: This is an important qualifier. While ternary operators can help simplify code, they're not always the best tool for the job. If your condition is very complex, using a ternary operator could actually make your code more difficult to understand.

    #### **Ternary Operators Tips**:
    - *Keep it Simple*: Ternary operators work best with simple, straightforward conditions. If your condition or the results are complex, consider using an if-else statement instead.

    - *Nested Ternary Operators*: While it's possible to nest ternary operators (i.e., use a ternary operator as part of the result of another ternary operator), this can quickly become confusing and should generally be avoided.

    - *Understand the Order of Operations*: Make sure you understand how your language handles order of operations with ternary operators, especially when they're part of a larger expression. This can sometimes cause unexpected results.

    - *Parentheses for Clarity*: Even if they're not strictly necessary, using parentheses can make it clearer which parts of the code are part of the condition and which parts are the results.

    - *Variable Assignment and Return Statements*: Ternary operators are frequently used for assigning a value to a variable or in a return statement based on a condition.


## Example: Ternary Operators

- #### **Example Without Ternary Operator in Python**:

    ```python
    # Without Ternary Operators

    def check_even_or_odd(number):
        if number % 2 == 0:
            return "Even"
        else:
            return "Odd"

    # Usage:
    print(check_even_or_odd(3))  # Output: Odd
    print(check_even_or_odd(2))  # Output: Even
    ```

    In this function, a regular `if-else` statement is used to decide what to return.

- #### **Example Using Ternary Operator in Python**:

    ```python
    # With Ternary Operator

    def check_even_or_odd(number):
        return "Even" if number % 2 == 0 else "Odd"

    # Usage:
    print(check_even_or_odd(3))  # Output: Odd
    print(check_even_or_odd(2))  # Output: Even
    ```

    In the second function, a ternary operator is used instead of the `if-else` statement. This simplifies the function and makes it more concise.
    
    Ternary operator is shorter and may be considered more readable, particularly for someone familiar with ternary operators. Again, it's worth noting that for more complex conditions, an `if-else` statement can be easier to understand.

- #### **Example Without Ternary Operator in PowerShell**:
    PowerShell also supports a form of ternary operator as of version 7. Let's use the same concept of checking whether a number is even or odd

    ```powershell
    # Without Ternary Operator

    function Check-EvenOrOdd ($number) {
        if ($number % 2 -eq 0) {
            "Even"
        }
        else {
            "Odd"
        }
    }

    # Usage:
    Check-EvenOrOdd 3  # Output: Odd
    Check-EvenOrOdd 2  # Output: Even
    ```

- #### **Example Using Ternary Operator in PowerShell**:

    ```powershell
    # With Ternary Operator

    function Check-EvenOrOdd ($number) {
        return ($number % 2 -eq 0) ? "Even" : "Odd"
    }

    # Usage:
    Check-EvenOrOdd 3  # Output: Odd
    Check-EvenOrOdd 2  # Output: Even
    ```
In Bash, we don't have a ternary operator like the one available in languages like Python, JavaScript, or C. However, Bash does support conditional expressions that can be used in a similar way. Here are examples of checking whether a number is even or odd in Bash.

- #### **Example Without Ternary Operator in Bash**:

    ```bash
    #!/bin/bash

    # Without Ternary Operator

    check_even_or_odd() {
        if (( $1 % 2 == 0 ))
        then
            echo "Even"
        else
            echo "Odd"
        fi
    }

    # Usage
    check_even_or_odd 3  # Output: Odd
    check_even_or_odd 2  # Output: Even
    ```

- #### **Example using Ternary Operator (Conditional Expression) in Bash**

    ```bash
    #!/bin/bash

    # With Conditional Expression 'Simulated Ternary Operator'

    check_even_or_odd() {
        (( $1 % 2 == 0 )) && echo "Even" || echo "Odd"
    }

    # Usage
    check_even_or_odd 3  # Output: Odd
    check_even_or_odd 2  # Output: Even
    ```

    In the second example, we're using a combination of `&&` (AND) and `||` (OR) to create a behavior similar to a ternary operator. This checks if the condition is true and executes the first `echo` if it is, otherwise it executes the second `echo`. 

    While this makes the function more concise, it could be considered less readable if you're not familiar with this syntax. 

<br>

The ultimate goal of this recommendation is to improve code readability. Readability is an essential quality of good code. When code is easy to read, it's easier to maintain and debug, which saves time and effort in the long run.

<br>

___
# [Return to The Automator's Guide](../README.md#the-evolution-of-bugs-often-ignored-but-critical-aspect-of-scripting)
