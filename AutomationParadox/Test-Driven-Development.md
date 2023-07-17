# Test-Driven Development

Test-Driven Development (TDD) is a software development practice. Here's a breakdown of what it means:

- **From day one of development**: TDD promotes the idea that testing should start early in the development process, ideally right from the beginning.
- **All functions need to be pre-stubbed out with accompanying test code**: Before implementing the actual functionality of a function, a "stub" (a basic, incomplete version) is created along with a corresponding test code. This allows for testing before the function is fully implemented.
- **Functions not yet implemented should trigger a non-implemented flag**: When a function is called but not yet implemented, it should raise an exception or produce an indication (flag) that the function is not yet implemented. This serves as a reminder to the developer to complete the function.
- **All tests should be written and clearly marked as 'skipped' if the comprehensive check of the test code is still under development**: Test code should be written for each function, even if the function is not fully implemented. These tests can be marked as 'skipped' or 'pending' to indicate that they are not yet ready for execution because the comprehensive check of the test code is still in progress.
- **The code should run and fail gracefully, indicating to the developer that the unit tests are verifying the code as expected**: When the code is executed, the tests associated with each function should run. Since the functions are not fully implemented, the tests are expected to fail. This serves as an indication to the developer that the unit tests are working correctly and validating the code as expected.

## Example: Test-Driven Development (TDD)

- ### **Example without Test-Driven Development (TDD) in Python**:
    > **Note**: Skipping TDD? its like navigate the Total Perspective Vortex without a towel - a surefire way to lose your sanity and end up utterly bewildered!"

    ```python
    # Without TDD

    # Function to calculate the factorial of a number
    def factorial(n):
        if n == 0:
            return 1
        else:
            return n * factorial(n - 1)

    # Using the factorial function
    result = factorial(5)
    print(result)
    ```
    In this example, the factorial function is implemented without any accompanying tests. The function is called directly with the argument `'5'` to calculate the factorial. However, without tests, it's difficult to ensure that the function behaves as expected in various scenarios and edge cases. This approach may lead to issues or bugs that go unnoticed until they cause problems in the application.

- ### **Example with Test-Driven Development (TDD) using pytest in Python**:
    ```python
    # With TDD and pytest

    # Function to calculate the factorial of a number
    def factorial(n):
        if n == 0:
            return 1
        else:
            return n * factorial(n - 1)

    # Test case for the factorial function
    def test_factorial():
        assert factorial(0) == 1
        assert factorial(1) == 1
        assert factorial(5) == 120
        assert factorial(10) == 3628800

    # Running the tests
    pytest.main()
    ```
    In this example, the factorial function is implemented along with corresponding test cases using the pytest framework. The `'test_factorial'`  function contains multiple assertions to check the expected results for different inputs. By running the tests using `'pytest'`, we can ensure that the factorial function produces the correct results in different scenarios. If any of the assertions fail, pytest will indicate which test case failed and the expected versus actual values, making it easier to identify and fix issues in the code early on.

    Using Test-Driven Development with unit-test tools like pytest helps enforce a systematic approach to testing and ensures that code is thoroughly validated throughout the development process.

- ### **Example without Test-Driven Development (TDD) in PowerShell**:
    > **Note**: Skipping TDD is inconceivable! It's like storming the Castle of Bad Practices without a plan. Prepare to be defeated by the six-fingered bugs of regression!

    ```powershell
    # Without TDD

    # Function to calculate the factorial of a number
    function Factorial {
        param (
            [int]$n
        )

        if ($n -eq 0) {
            return 1
        }
        else {
            return $n * (Factorial ($n - 1))
        }
    }

    # Using the factorial function
    $result = Factorial 5
    Write-Output $result
    ```
    In this example, the `'Factorial'` function is implemented without any accompanying tests. The function is called directly with the argument 5 to calculate the factorial. However, without tests, it's challenging to ensure that the function behaves correctly in various scenarios and edge cases. This approach may lead to issues or bugs that go unnoticed until they cause problems in the application.
- ### **Example with Test-Driven Development (TDD) in PowerShell using Pester**:
    ```powershell
    # With TDD and Pester

    # Function to calculate the factorial of a number
    function Factorial {
        param (
            [int]$n
        )

        if ($n -eq 0) {
            return 1
        }
        else {
            return $n * (Factorial ($n - 1))
        }
    }

    # Importing Pester module
    Import-Module Pester

    # Describe block for the factorial function tests
    Describe "Factorial Tests" {
        Context "When calculating the factorial of 0" {
            It "Should return 1" {
                $result = Factorial 0
                $result | Should -Be 1
            }
        }

        Context "When calculating the factorial of a positive number" {
            It "Should return the correct factorial" {
                $result = Factorial 5
                $result | Should -Be 120
            }
        }
    }

    # Running the tests
    Invoke-Pester
    ```
    In this example, the `'Factorial'` function is implemented along with corresponding tests using the Pester framework, which is commonly used for testing PowerShell code. The tests are defined within a `'Describe'`  block, containing multiple `Context` blocks that specify different scenarios. Each scenario has an `'It'` block that performs assertions using the `'Should'` syntax to validate the expected results.

    By running the tests using `'Invoke-Pester'`, we can ensure that the `'Factorial'` function produces the correct results in different scenarios. If any of the assertions fail, Pester will indicate which test case failed and the expected versus actual values, making it easier to identify and fix issues in the code early on.

    Using Test-Driven Development with unit-testing tools like Pester helps enforce a systematic approach to testing and ensures that code is thoroughly validated throughout the PowerShell development process.

- ### **Example without Test-Driven Development (TDD) in Bash**:
    > **Note**:  Skipping TDD? Is like venturing into Nightmare Land without the protection of your trusty Dream Sword. It's a surefire way to encounter the monstrous creatures of sloppy coding and endless debugging quests.

    ```bash
    #!/bin/bash

    # Without TDD

    # Function to calculate the factorial of a number
    factorial() {
        local n=$1
        if (( n == 0 )); then
            echo 1
        else
            echo $(( n * $(factorial $((n-1))) ))
        fi
    }

    # Using the factorial function
    result=$(factorial 5)
    echo $result
    ```
    In this example, the `'factorial'`  function is implemented without any accompanying tests. The function is called directly with the argument 5 to calculate the factorial. However, without tests, it's challenging to ensure that the function behaves correctly in various scenarios and edge cases. This approach may lead to issues or bugs that go unnoticed until they cause problems in the application.
- ### **Example with Test-Driven Development (TDD) in Bash using ShellSpec**:
    ```bash
    #!/bin/bash

    # With TDD and ShellSpec

    # Function to calculate the factorial of a number
    factorial() {
        local n=$1
        if (( n == 0 )); then
            echo 1
        else
            echo $(( n * $(factorial $((n-1))) ))
        fi
    }

    # Importing ShellSpec library
    source shellspec/shellspec.sh

    # Describe block for the factorial function tests
    describe "Factorial Tests" do
        context "When calculating the factorial of 0" do
            it "Should return 1" do
                When run factorial 0
                The output should equal 1
            end
        end

        context "When calculating the factorial of a positive number" do
            it "Should return the correct factorial" do
                When run factorial 5
                The output should equal 120
            end
        end
    done

    # Running the tests
    shellspec
    ```
    In this example, the `'factorial'`  function is implemented along with corresponding tests using the ShellSpec framework, which is commonly used for testing shell scripts in Bash. The tests are defined within a `'describe'` block, containing multiple context blocks that specify different scenarios. Each scenario has an `'it'` block that performs assertions using the `'When'`, `'The'`, and `'output'` syntax to validate the expected results.

    By running the tests using `'shellspec'`, we can ensure that the `'factorial'` function produces the correct results in different scenarios. If any of the assertions fail, ShellSpec will indicate which test case failed and the expected versus actual values, making it easier to identify and fix issues in the code early on.

    Using Test-Driven Development with unit-test tools like ShellSpec helps enforce a systematic approach to testing and ensures that code is thoroughly validated throughout the Bash scripting process.
    <br>
    <br>

Overall, Test-Driven Development emphasizes writing tests before implementing code, ensuring that the code is thoroughly tested and verified throughout the development process. It helps improve code quality, maintainability, and reduces the likelihood of introducing bugs or regressions.

<br>

___
# [Return to The Automator's Guide](../README.md)
