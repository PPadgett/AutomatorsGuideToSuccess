# [**Automation Paradox**](./AutomationParadox/Coding-Guidelines.md): Automator’s Guide to Success!

- ### [**Sensitive Information**](./AutomationParadox/Sensitive-Information.md): Information like passwords and API keys should not be hard coded in scripts. Instead, developers should use secure methods to handle secrets, such as environment variables, credential parameters, or secure vault services. 
  > [*Example code snippet in 'Python'*](./AutomationParadox/Sensitive-Information.md#example-of-hard-coding-sensitive-information-in-python), [*'PowerShell'*](./AutomationParadox/Sensitive-Information.md#example-of-hard-coding-sensitive-information-in-powershell), [*'Bash'*](./AutomationParadox/Sensitive-Information.md#example-of-hard-coding-sensitive-information-in-bash)

- ### [**Code Analysis and Pipeline Automation**](./AutomationParadox/Code-Analysis-and-PipelineAutomation.md): Integrate static code analysis tools within the pipeline to identify possible security risks in the code, along with automated ‘syntax’, ‘lint’, 'unit' and 'mock' testing. This multifactor strategy guarantees an exhaustive review and verification of the code, greatly improving its overall security and performance.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Code-Analysis-and-PipelineAutomation.md#example-without-code-analysis-and-pipeline-automation-for-python-code-via-azure-devops-pipelines), [*'PowerShell'*](./AutomationParadox/Code-Analysis-and-PipelineAutomation.md#example-without-code-analysis-and-pipeline-automation-for-powershell-code-via-azure-devops-pipelines), [*'Bash'*](./AutomationParadox/Code-Analysis-and-PipelineAutomation.md#example-without-code-analysis-and-pipeline-automation-for-bash-code-via-azure-devops-pipelines),  [*'Terraform'*](./AutomationParadox/Code-Analysis-and-PipelineAutomation.md#example-without-code-analysis-and-pipeline-automation-for-terraform-code-via-azure-devops-pipelines), [*'Ansible'*](./AutomationParadox/Code-Analysis-and-PipelineAutomation.md#example-without-code-analysis-and-pipeline-automation-for-ansible-playbook-via-azure-devops-pipelines)

- ### [**Test-Driven Development**](./AutomationParadox/Test-Driven-Development.md): From the initial phase of development, functions should be pre-stubbed with corresponding test code. Unimplemented functions should trigger a 'non-implemented' flag. All tests must be documented and marked as 'skipped' if the complete verification of the test code is ongoing. The code should execute and fail elegantly, signaling to the developer that the unit tests are inspecting the code as planned. 
  >[*Example code snippet in 'Python'*](./AutomationParadox/Test-Driven-Development.md#example-without-test-driven-development-tdd-in-python), [*'PowerShell'*](./AutomationParadox/Test-Driven-Development.md#example-without-test-driven-development-tdd-in-powershell), [*'Bash'*](./AutomationParadox/Test-Driven-Development.md#example-without-test-driven-development-tdd-in-bash)

- ### [**Bootstrapping**](./AutomationParadox/Bootstrapping.md): A bootstrap script, often part of the initial server setup or provisioning, prepares a server for operation. It configures the OS for Operational and Security Compliance (e.g., Monitoring Agents, Antivirus Agent, etc.). Best practices recommend using commandlets (e.g., ansible-playbook -i inventory playbook.yml) from a trusted package manager or a secure source.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Bootstrapping.md#example-without-bootstraping-in-python-via-onprem-centos-package-manager), [*'PowerShell'*](./AutomationParadox/Bootstrapping.md#example-without-bootstrapping-in-powershell-via-gist), [*'Bash'*](./AutomationParadox/Bootstrapping.md#example-without-bootstrapping-in-bash-via-ansible)

- ### [**Style Guide**](./AutomationParadox/Style-Guide.md): Developers should follow a coding and/or Scripting specific language style guide to maintain consistency across the codebase. This practice improves the readability of the code.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Style-Guide.md#example-without-style-in-python), [*'PowerShell'*](./AutomationParadox/Style-Guide.md#example-without-style-in-powershell), [*'Bash'*](./AutomationParadox/Style-Guide.md#example-without-style-in-bash)

- ### [**Meaningful Naming Conventions**](./AutomationParadox/Meaningful-Naming-Conventions.md): Verbose Names for variables, functions, and classes should reflect their purpose or behavior. Consistency in naming across the codebase also aids in comprehensibility and maintenance.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Meaningful-Naming-Conventions.md#example-without-meaningful-naming-conventions-in-python), [*'PowerShell'*](./AutomationParadox/Meaningful-Naming-Conventions.md#example-without-meaningful-naming-conventions-in-powershell), [*'Bash'*](./AutomationParadox/Meaningful-Naming-Conventions.md#example-without-meaningful-naming-conventions-in-python)

- ### [**Parameters Passing**](./AutomationParadox/Parameter-Passing.md): All scripts and/or functions should define parameters to pass inputs. This promotes flexibility and reusability of functions and scripts.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Parameter-Passing.md#example-without-parameter-passing-in-python), [*'PowerShell'*](./AutomationParadox/Parameter-Passing.md#example-without-parameter-passing-in-powershell), [*'Bash'*](./AutomationParadox/Parameter-Passing.md#example-without-parameter-passing-in-bash)  

- ### [**Retuning Value**](./AutomationParadox/Returning-Value.md): Verbose Names for variables, functions, and classes should reflect their purpose or behavior. Consistency in naming across the codebase also aids in comprehensibility and maintenance.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Returning-Value.md#example-without-returning-value-in-python), [*'PowerShell'*](./AutomationParadox/Returning-Value.md#example-without-using-return-value-in-powershell), [*'Bash'*](./AutomationParadox/Returning-Value.md#example-without-using-return-values-in-bash)

- ### [**Inline-Comments**](./AutomationParadox/Inline-Comments.md): Inline Comments: Developers should add inline comments to complex code sections. This best practice makes the code easier to understand for others and for the future self.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Inline-Comments.md#example-without-comments-in-python), [*'PowerShell'*](../AutomationParadox/Inline-Comments.md#example-without-comments-in-powershell), [*'Bash'*](./AutomationParadox/Inline-Comments.md#example-without-comments-in-bash)

- ### [**Modularity**](./AutomationParadox/Modularity.md): Code should be organized into smaller, reusable, and maintainable modules or functions. This standard approach leads to cleaner code that is easier to understand, test, and maintain.
  > [*Example code snippet in 'Python'*](./AutomationParadox/Modularity.md#example-without-modularity-in-python), [*'PowerShell'*](./AutomationParadox/Modularity.md#example-without-modularity-in-powershell), [*'Bash'*](./AutomationParadox/Modularity.md#example-without-modularity-in-bash)

<br>

_______
# [**The Evolution of Bugs**](./TheEvolutionOfBugs/Logic-Guidelines.md): often ignored, but critical aspect of scripting

- ### [**Global Variables**](./TheEvolutionOfBugs/Global-Variables.md): The policy is to prohibit the use of global variables as they can lead to code that is difficult to understand and debug. The standard practice should be to always use local variables and pass them as arguments to functions if needed. This promotes more predictable behaviors and easier debugging. 
  > [*Example code snippet in 'Python'*](./Global-Variables.md#example-of-using-global-variables-in-python), [*'PowerShell'*](./Global-Variables.md#example-of-using-global-variables-in-powershell), [*'Bash'*](./Global-Variables.md#example-of-using-global-variables-in-bash)

- ### [**Function Length**](./TheEvolutionOfBugs/Function-Length.md): No function should be longer than what can be printed on a single sheet of paper in a standard reference format with one line per statement and one line per declaration. Typically, this means no more than about 60 lines of code per function.
  > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Function-Length.md#example-without-function-lenght-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Function-Length.md#example-without-function-lenght-in-powershell), [*'Bash'*](./TheEvolutionOfBugs/Function-Length.md#example-without-function-lenght-in-bash), [*'Terraform'*](./TheEvolutionOfBugs/Function-Length.md#example-without-function-lenght-in-terraform-via-azure), [*'Ansible'*](./TheEvolutionOfBugs/Function-Length.md#example-without-function-lenght-in-ansible)


- ### [**Assertions**](./TheEvolutionOfBugs/Assertions.md): Leverage assertions, aiming for an average of at least two per script. Utilizing assertions can help identify and halt errors early in the development process, thereby mitigating the cost associated with bug fixing.
  > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Assertions.md#example-without-using-assertions-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Assertions.md#example-without-using-assertions-in-powershell), [*'Bash'*](./TheEvolutionOfBugs/Assertions.md#example-without-using-assertions-in-powershell)


- ### [**Fixed Upper-Bound Loop**](./TheEvolutionOfBugs/Fixed-Uper-Bound-Loop.md): Means that every loop in the code must have a maximum number of iterations it can perform, and this maximum number must be known (and not changed) at run-time, which is before the script is executed.
  > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Fixed-Uper-Bound-Loop.md#example-without-a-fixed-upper-bound-loop-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Fixed-Uper-Bound-Loop.md#example-without-a-fixed-upper-bound-loop-in-powershell), [*'Bash'*](./TheEvolutionOfBugs/Fixed-Uper-Bound-Loop.md#example-without-a-fixed-upper-bound-loop-in-bash)


- ### [**Strong Typing**](./TheEvolutionOfBugs/Strong-Typing.md): Use strong typing to catch potential errors at compile time. This can avoid potential runtime errors and make the code easier to understand.
  > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Strong-Typing.md#example-without-strong-typing-type-hints-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Strong-Typing.md#example-without-strong-typing-type-hints-in-python), [*'Bash'*](./TheEvolutionOfBugs/Strong-Typing.md#example-without-strong-typing-simulated-in-bash), [*'Terraform'*](./TheEvolutionOfBugs/Strong-Typing.md#example-without-strong-typing-context-in-terraform)

 - ### [**Ternary Operators**](./TheEvolutionOfBugs/Ternary-Operators.md): Use ternary operators instead of if-else statements for simpler conditions to increase code readability.
    > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Ternary-Operators.md#example-without-ternary-operator-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Ternary-Operators.md#example-without-ternary-operator-in-powershell), [*'Bash'*](./TheEvolutionOfBugs/Ternary-Operators.md#example-without-ternary-operator-in-bash)


- ### [**Refactoring**](./TheEvolutionOfBugs/Refactoring.md): Automation Developers should regularly refactor their code to improve its structure and design without altering its external behavior. This is a best practice for maintainable code.
  > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Refactoring.md#example-before-refactoring-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Refactoring.md#example-before-refactoring-in-powershell), [*'Bash'*](./TheEvolutionOfBugs/Refactoring.md#example-before-refactoring-in-bash)

- ### [**Execution Instructions including Usage Examples**](./TheEvolutionOfBugs/Execution-Instructions-Including-Usage-Examples.md): For each function and/or script, should be provided. This practice helps new developers to understand how to use the functions and scripts.

  > [*Example code snippet in 'Python'*](./TheEvolutionOfBugs/Execution-Instructions-Including-Usage-Examples.md#example-without-execution-instructions-or-usage-examples-in-python), [*'PowerShell'*](./TheEvolutionOfBugs/Execution-Instructions-Including-Usage-Examples.md#example-without-execution-instructions-or-usage-examples-in-powershell), [*'Bash'*](./TheEvolutionOfBugs/Execution-Instructions-Including-Usage-Examples.md#example-without-execution-instructions-or-usage-examples-in-bash)
  , [*'Terraform'*](./TheEvolutionOfBugs/Execution-Instructions-Including-Usage-Examples.md#example-without-execution-instructions-or-usage-examples-in-terraform), [*'Ansible'*](./TheEvolutionOfBugs/Execution-Instructions-Including-Usage-Examples.md#example-without-execution-instructions-or-usage-examples-in-ansible)
  

<br>

___
[Return to Top](#automation-paradox-automators-guide-to-success)

