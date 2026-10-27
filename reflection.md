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

---

### 4.: What are the trade-offs between using inline security suppressions (such as `# nosec` for Bandit) versus refactoring legacy code to use cryptographically secure alternatives, and when is each approach appropriate?
Inline suppressions like `# nosec` are practical when legacy constraints, performance requirements, or non-security contexts (such as non-cryptographic identifier hashing or basic token generation) make heavy cryptographic refactoring unnecessary. They allow developers to document and explicitly acknowledge a controlled risk without breaking existing system dependencies.
However, the major trade-off is the risk of masking genuine vulnerabilities if suppressions are applied carelessly or without adequate justification. Refactoring to secure alternatives (such as using `secrets` instead of `random`, or `sha256` instead of `md5`) provides robust, future-proof protection, but can sometimes introduce breaking changes or slight performance overhead.
* **When to use suppressions:** When dealing with legacy codebases where the flagged function serves a strictly non-security purpose and changing it would break downstream contracts, provided the exception is explicitly commented and audited.
* **When to refactor:** In production environments handling sensitive user data, authentication credentials, or financial transactions, where cryptographic integrity is paramount.


---