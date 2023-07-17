# Assertions

Assertions are statements that assert or state a fact confidently in your program. For instance, you may assert that a certain variable is never null, or that a certain list is not empty at a given point in the program. If the assertion statement turns out to be false during execution, the program will throw an AssertionError, which can help identify bugs more easily and more quickly.

- **Assertions**: are recommended, meaning they are optional, addionaly the code will be checked for presents of assertions on complex scripts.

- **Two Assertions**: Each script and/or controller should include, on average, at least two assertions. This suggests a balance between not using assertions at all and using them excessively. It's important to note that the actual number can vary - some scripts/controllers may need more, others may need fewer.

- **Catch and Prevent Errors**: The reason given for this guideline is that assertions help to catch and prevent errors early in the development process. By triggering an AssertionError when something goes wrong, developers are notified of the problem right away, rather than discovering it through more complex debugging or, even worse, after the software has been released. This can significantly reduce the cost (both time and money) of fixing bugs.
    >**Note**: Test-Driven Development (TDD) has largely replaced the need for assertion code. However, assertions can still play a critical role in developing core processes and/or workflows, especially in sensitive and critical code areas. So, don't completely disregard assertions.
  
    #### **Assertion Tips**:

   - *Assertions are Not Error Handlers*: Assertions are meant to be internal self-checks for your code. They are typically enabled during development and testing and disabled in the production environment. Don't use them to handle runtime errors or expected conditions. Those should be handled by appropriate error handling code.
    
   - *Test the Edge Cases*: Assertions are a great way to test the edge cases of your program. By testing these unusual or extreme input cases, you can ensure that your program will behave as expected even in unexpected scenarios.

   - *Asserting with Collections*: When you're asserting on collections (like lists or dictionaries in Python), it's often useful to assert on their length first. This gives you a more useful error message than a generic 'list index out of range' error.

   - *Assertions Can Be Turned Off*: In many languages (like Python), assertions can be globally disabled with an interpreter setting. Never use assertions to implement logic that your program relies on.

   - *Negative Assertions*: In unit testing, it's often useful to not only assert that the right thing happens, but also that the wrong thing does *not* happen. For example, `assert not user.is_admin()`.

   - *Using Assertions to Confirm API Contracts
   - *: Assertions can be used to check if an API's responses are as expected, like a certain key being present in the response dictionary.

   - *Assertions in Multithreading/Parallel Processing*: Assertions can help ensure that certain conditions are met in a multi-threaded or parallel processing environment, reducing the chance of race conditions or concurrency issues.

   - *Use Assertions to Document Assumptions*:* Assertions can serve as executable documentation. When you assert that a condition holds true, you're documenting an assumption your code makes. When an assertion fails, you know your assumption was incorrect.

## Example: Assertions

- #### **Example without using Assertions in Python**:
    > **Note**:

    ```python
    # Without Assertion

    def square(num):
        result = num * num
        return result

    # Call the function with a positive number
    print(square(4))  # Output: 16

    # Call the function with a negative number
    print(square(-4))  # Output: 16
    ```

    In the above example, the function `square` will calculate the square of any number you pass into it, even if the number is negative. This may not be the desired behavior, and could potentially lead to bugs.

- #### **Example using Assertions in Python**:

    ```python
    # With Assertion

    def square(num):
        assert isinstance(num, (int, float)), 'Input must be a numeric value.'
        assert num >= 0, 'Input must be a non-negative number.'
        result = num * num
        return result

    # Call the function with a positive number
    print(square(4))  # Output: 16

    # Call the function with a negative number
    try:
        print(square(-4))
    except AssertionError as error:
        print(error)  # Output: Input must be a non-negative number.
    ```

    In the second example, the function `square` includes two assertions: one to ensure that the input `num` is a numeric value (either an integer or a float), and the other to ensure that `num` is non-negative. If either assertion fails, an `AssertionError` will be raised with the corresponding error message.

    In Python, assertions can be globally disabled by running the interpreter with the `-O` (optimize) flag. When the interpreter is run in this way, all `assert` statements are ignored. It's important to remember that because of this, assertions should not be used for handling expected errors or for implementing essential program logic. They're designed to be used as a debugging aid, and to ensure that the program's state is as expected.


- #### **Example without using Assertions in PowerShell**:
    > **Note**:

    PowerShell doesn't have built-in assertion functionality in the same way that Python or other languages do. However, you can accomplish similar behavior using conditional checks and throwing exceptions.

    ```powershell
    # Without Assertion

    function Get-Square {
        param(
            [Parameter(Mandatory=$true)]
            [int]$num
        )
        $result = $num * $num
        return $result
    }

    # Call the function with a positive number
    Write-Output (Get-Square 4)  # Output: 16

    # Call the function with a negative number
    Write-Output (Get-Square -4)  # Output: 16
    ```

    In this example, the `Get-Square` function will calculate the square of any integer you pass to it, even if the number is negative. This may not be the desired behavior and could lead to unexpected results.

- #### **Example using Assertions in PowerShell**:

    ```powershell
    # With Assertion

    function Assert-Condition ([bool]$Condition, $Message ) {    
        # If the hash code is not 0 (meaning the DebugPreference is 'Stop', 'Continue' or 'Inquire'), the function will check the condition
        if ($DebugPreference.GetHashCode() -ne 0) {
            # If the condition is met (is true), it will throw the provided message, otherwise it will not do anything
            $Condition ? throw "Assertion failed: $Message" : $null
        }
    }

    function Get-Square {
        param(
            [Parameter(Mandatory=$true)]
            [int]$num
        )
        Assert-Condition ($num -lt 0) "Input must not be a negative number."
        
        $result = $num * $num
        return $result
    }

    # Call the function with a positive number
    Write-Output (Get-Square 4)  # Output: 16

    # Call the function with a negative number
    $DebugPreference = 'Continue'
    Write-Output (Get-Square -4) # Output: Input must be a non-negative number.
    ```

    In the second example, `Get-Square` checks if the system variable `$DebugPreference` is true. If it is, it then checks that the input number is non-negative. If this check fails, an exception is thrown.

    This is somewhat similar to an assertion in other languages, although it's not quite the same thing. PowerShell does not have a mechanism to globally disable all assertions like Python's `-O` flag. However, by using a system variable, we can create a similar effect, disabling this check by setting `$DebugPreference` to `SilentlyContinue`.



- #### **Example without using Assertions in Bash**:
    > **Note**:

    Bash does not have built-in assertions in the same way as other languages like Python or Java. However, you can emulate similar behavior by using conditional statements and exiting the script when certain conditions aren't met.

    ```bash
    #!/bin/bash

    # Without Assertion

    function square {
        local num=$1
        local result=$((num*num))
        echo $result
    }

    # Call the function with a positive number
    square 4  # Output: 16

    # Call the function with a negative number
    square -4  # Output: 16
    ```

    In this example, the `square` function will calculate the square of any number you pass to it, even if the number is negative. This might not always be the desired behavior.

- #### **Example using Assertions in Bash**:

    ```bash
    #!/bin/bash

    # With Assertion

    ASSERTIONS_ENABLED=true

    function assert {
        if ! $ASSERTIONS_ENABLED; then
            return 0
        fi

        if ! eval $1; then
            echo "Assertion failed: \"$1\" in $BASH_SOURCE at line $BASH_LINENO"
            exit 1
        fi
    }

    function square {
        local num=$1
        assert "[ $num -ge 0 ]"
        local result=$((num*num))
        echo $result
    }

    # Call the function with a positive number
    square 4  # Output: 16

    # Call the function with a negative number
    ASSERTIONS_ENABLED=false
    square -4  # Output: 16
    ```

    In the second example, the `square` function includes an assertion to ensure that the input number is non-negative. The `assert` function will evaluate the condition and exit the script if the condition isn't met, printing a message to the console about what failed and where. The global variable `ASSERTIONS_ENABLED` can be used to disable the assertions.

Remember, while assertions can be very useful, they should not be used to handle expected errors or to replace proper error handling and testing strategies. They are a supplement to good coding practices, not a replacement.

<br>

___
# [Return to The Automator's Guide](../README.md#the-evolution-of-bugs-often-ignored-but-critical-aspect-of-scripting)
