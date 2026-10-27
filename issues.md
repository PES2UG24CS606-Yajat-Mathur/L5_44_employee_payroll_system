# Issue Documentation Table

| Issue | Type | Line(s) | Description | Fix Approach |
| :--- | :--- | :--- | :--- | :--- |
| **Mutable Default Argument** | Bug / Security | 15 | `transaction_logs=[]` in `processSalary()` is mutable and retains state across multiple function calls. | Changed default parameter to `None` and initialized `transaction_logs = []` inside the function if `None`. |
| **Insecure Code Execution (`eval`)** | Security (Bandit - B307) | 36 | `eval(deduction_expr)` evaluates untrusted dynamic code, creating arbitrary code execution risks. | Removed `eval()` and refactored function to take a numeric `tax_multiplier` parameter for safe arithmetic calculation. |
| **Unsafe Command Injection (`os.system`)** | Security (Bandit - B605/B607) | 49 | `os.system()` executes shell commands vulnerable to command injection attack vectors. | Removed `os.system()` invocation completely and safely handled operations natively in Python. |
| **Broad Exception Catching** | Code Quality (Pylint - W0702) | 24 | `except:` in `deduct_penalty()` catches all exceptions (including system signals) indiscriminately. | Replaced bare `except:` with specific exception handling `except KeyError:`. |
| **Missing Module & Function Docstrings** | Style / Quality (Pylint - C0114/C0116) | Various | Functions and module lacked standard docstrings explaining their purpose and arguments. | Added docstrings following standard PEP 257 guidelines for all public functions and module header. |
| **Naming Convention Violation** | Style (Pylint - C0103) | 15 | `processSalary` uses camelCase instead of snake_case required by PEP 8 guidelines. | Renamed function to `process_salary` and updated corresponding function calls in `main()`. |