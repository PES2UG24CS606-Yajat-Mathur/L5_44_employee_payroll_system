# Lab 5: Reflection Questions

### 1. What is the purpose and scope of static code analysis? How do tools like Pylint, Bandit, and Flake8 complement each other?
Static code analysis is the practice of evaluating source code without executing it to discover syntax errors, logical bugs, security vulnerabilities, and formatting deviations early in the software development lifecycle. 

The three tools complement each other by covering distinct domains of code quality:
* **Pylint:** Acts as a strict code reviewer, analyzing code structure, variable naming, logic flaws, missing docstrings, and overall maintainability.
* **Bandit:** Functions as a security guard, specifically searching for common security vulnerabilities (e.g., use of unsafe functions like `eval()`, shell injection via `os.system()`, hardcoded secrets, or insecure cryptographic algorithms).
* **Flake8:** Operates as a style and grammar checker, strictly enforcing PEP 8 guidelines including line length limitations, whitespace consistency, unused imports, and basic syntax checking.

Together, they ensure code is secure, readable, maintainable, and syntactically sound.

---

### 2. How do issues like mutable default arguments or overly broad exceptions impact code maintainability and reliability?
* **Mutable Default Arguments:** In Python, default parameter values are evaluated once when the function is defined, not each time it is called. Using a mutable data structure (like a list or dictionary) as a default argument means state persists across multiple function calls. This causes subtle, hard-to-track bugs where modified state unexpectedly leaks between independent executions.
* **Overly Broad Exceptions (`except:`):** Catching generic exceptions without specifying the expected exception type suppresses critical error information. It can obscure syntax errors, typing mistakes, or system interrupts (like `KeyboardInterrupt`), preventing developers from identifying root causes and leading to unpredictable application behavior.

---

### 3. Why is it important to address security vulnerabilities early in the development lifecycle?
Addressing security vulnerabilities during development (Shift-Left approach) is significantly more cost-effective and efficient than patching flaws after release. Early detection prevents security breaches, unauthorized access, and data leaks before software reaches production. Additionally, fixing issues during development reduces technical debt and helps developers build secure coding habits.