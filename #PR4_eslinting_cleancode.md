# PR Contribution to Code Repo

- **PR Link**: [My PR](http://github.com/dishak/Collaborative-code-editor/pull/1)
- **Code Repo**: [Code Repository](http://github.com/dishak/Collaborative-code-editor/tree/linting-codebase)

## Task: Linting & Code Formatting the Codebase (2 Backend Services and 1 Frontend Service)

### Description
Exercising good code practices makes the codebase easier to maintain across development history.

### Analysis
To implement industry-level code maintenance practices, various tools are available to achieve linting (Detects errors, code quality issues, and enforces coding standards) & code formatting (styling of code). In this PR, the famous tool ESLint & Prettier is used. Airbnb's style guide is applied for code linting in the PR for the codebase and recommneded styling for code formatting by prettier is used.

### Key Code Practices Fixed
1. **No Use Before Define**: A function call should not be made before it is declared.
2. **Variable Naming Conflicts**: A variable name in the local scope is not allowed when the same name is used in the global scope.
3. **Unused Variables**: Unused variables are removed.
4. **Function Return**: Every function should have a return statement.
5. **Promise Executor Functions**: No return from a promise executor function, as a promise executor function never returns a value; it either resolves or throws an error.
6. **Code Formatting**: Appropriate indentation, semicolons at the end of every code statement, and appropriate spacing in between function parentheses.(from prettier)

These are a few among many other code practices applied to the codebase. While it is not strictly necessary to use linting & code formatting but, it is always beneficial to maintain good code practices, especially when multiple developers are working on the same project, to ensure standardization across development environments.

### Issue Addressed in PR
- **PR Contribution**: [PR Contribution](http://github.com/dishak/Collaborative-code-editor/pull/1)
