# Returning Value:

Returing Value when a function or script processes some input or performs some action and then outputs the result, we say that the function "returns" a value. This good practice for programming and automation development, specifically in regards to using scripts and functions. Let's break it down:

1. **Returning Value:** Functions are designed to perform specific tasks. Once a task is completed, a function can return the result. This result is known as a "return value." For example, a function may be designed to add two numbers, and the sum of those numbers would be the return value.

2. **All scripts and/or Functions should always return data or the result of the action it is performing:** This part suggests that whenever you write a script or function, it should ideally give back a result. This might be the processed data, the status of a task, or any output that denotes the completion and result of the task.

3. **This improves the testability of the code:** When functions return values, it allows for easier testing. You can check the returned value against the expected outcome to see if your function is working as intended. 

4. **Allows the results of functions to be used elsewhere in the script:** When a function returns a value, you can store that value in a variable and use it in other parts of your script. This enables the development of more complex programs, as the output from one function can serve as the input for another.


    #### **Returning Value Tips**:
   - *Explicit is better than implicit:* Always aim to return a value explicitly from your function. It makes your code more readable and maintainable. For example, in Python, instead of relying on the fact that the last evaluated statement's value is returned by default, explicitly use the `return` statement.

   - *Use return values for testability:* Return values allow you to easily write tests for your functions. You can provide known inputs to a function and then check that it returns the correct output.

   - *Avoid side effects:* Try to make your functions pure, meaning that they only depend on their input arguments and do not affect or rely on any external state. This is easier to understand, test, and reuse. It also allows the results of the function to be cached, if that's beneficial.

   - *Single exit point:* While this is not strictly necessary, having a single exit point (i.e., one return statement at the end of your function) can make your function easier to understand and debug. However, this is a matter of personal or team coding style preference, and there may be situations where multiple return statements make sense.

   - *Be clear about what you're returning:* Make sure it's clear from your function's name, comments, or docstring what kind of value it returns. If your function can return different types of values (like a string or `None`, for instance), make sure this is clearly documented and that code that calls your function handles all possible return types.

   -  *Consistent return statements:* If your function has multiple return statements, they should return data of consistent types. This helps in maintaining the integrity of the function and avoids confusion during debugging.

   - *Think about error handling:* What should your function do if it encounters an error? Should it return a special value (like `None` or `-1`)? Should it throw an exception? This will depend on what makes the most sense for your specific use case and the language you're using. But it's an important thing to consider.

<br>

## Example: Returning Value

- ### **Example without Returning Value in Python**:
    > **Note**: Foo bars have been multiplied and best practices seem to have taken an interstellar hitchhike.


  Let's consider a script that calculates the square of a number:

  ```python
  # Without Returning Value

  def square(number):
      squared = number ** 2
      print(squared)

  square(5)
  ```
  In this script, we have a function `square(number)` that calculates the square of a number and prints it. However, it doesn't return anything. So, if you try to assign the result to a variable, you will get `None`.

    ```python
    result = square(5)
    print(result)  # Will print None because square function does not return a value
    ```

- ### **Example Using Return Values in Python**:

    Now, let's modify the previous script so that it returns the squared value:

    ```python
    # With Returning Value

    def square(number):
        squared = number ** 2
        return squared

    result = square(5)
    print(result)  # Will print 25
    ```

    In this script, the function `square(number)` calculates the square of a number and returns it. Therefore, when we call the function and assign its result to a variable `result`, the variable holds the returned value (25 in this case). The value can then be used elsewhere in the script, which increases the reusability of the code.



- ### **Example Without Using Return Values in PowerShell**:
    > **Note**: "Inconceivable! Your code is as confusing as Vizzini's battle of wits, filled with more foo bars than Fezzik has rhymes. This is certainly not as you wish.

    PowerShell script examples illustrating the use and non-use of return values. Let's consider a script that calculates the square of a number:

    ```powershell
    # Without Returning Value

    function Square($number) {
        $squared = $number * $number
        Write-Host $squared
    }

    Square 5
    ```

    In this script, we have a function `Square` that calculates the square of a number and writes it to the console using `Write-Host`. However, it doesn't return anything. So, if you try to assign the result to a variable, you will get nothing.

    ```powershell
    $result = Square 5
    Write-Output $result  # Will print nothing because Square function does not return a value
    ```

- ### **Example Using Return Values in PowerShell**:

    Now, let's modify the previous script so that it returns the squared value:

    ```powershell
    # With Returning Value

    function Square($number) {
        $squared = $number * $number
        return $squared
    }

    $result = Square 5
    Write-Output $result  # Will print 25
    ```

    In this script, the function `Square` calculates the square of a number and returns it. Therefore, when we call the function and assign its result to a variable `$result`, the variable holds the returned value (25 in this case). The value can then be used elsewhere in the script, which increases the reusability of the code.

    Sure, here are bash script examples with and without using return values:

- ### **Example Without Using Return Values in Bash**:
  > **Note**:  Your code is like a wild ride on the Slumberland Express, filled with unforeseen foo bars and flying bedsteads. Perhaps it's time to wake from this dream and adopt better practices.

    Consider a script that calculates the square of a number:

    ```bash
    # Without Returning Value

    function square {
        squared=$(( $1*$1 ))
        
    }

    square 5
    ```

    In this script, we have a function `square` that calculates the square of a number and echoes it. However, it doesn't return anything. So, if you try to assign the result to a variable, you will get an empty string:

    ```bash
    result=$(square 5)
    echo "Result: $result"  # Will print the result of the echo within the function because it does not return a value
    ```

- ### **Example Using Return Values**

    Now, let's modify the previous script so that it 'returns' the squared value. Please note that bash functions don't actually 'return' values like functions in other languages. Instead, they echo the output, and you capture it in a variable.

    ```bash
    # With Returning Value

    function square {
        squared=$(( $1*$1 ))
        echo $squared
    }

    result=$(square 5)
    echo "Result: $result"  # Will print 25
    ```

    In this script, the function `square` calculates the square of a number and echoes it. When we call the function and assign its result to a variable `result`, the variable holds the 'returned' value (25 in this case). The value can then be used elsewhere in the script, which increases the reusability of the code.

In summary, this statement is emphasizing that your code (specifically scripts and functions) should always provide some form of output that can be used for testing or further actions. This enhances the reusability and verifiability of your code.

<br>

___
# [Return to The Automator's Guide](../README.md)
