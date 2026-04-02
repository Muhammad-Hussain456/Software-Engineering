
# Module 07: Software Implementation & Coding

## Learning Objectives
- Write clean, readable, and maintainable code following best practices.
- Understand and enforce coding standards and conventions.
- Apply refactoring techniques to improve code quality.
- Use version control effectively during implementation.

## Key Topics

### 1. Coding Standards & Conventions
- **Why**: Improve readability, maintainability, team collaboration.
- **Examples**:
  - Naming conventions (camelCase, PascalCase, snake_case).
  - Indentation, line length, commenting.
  - Language-specific guidelines (PEP 8 for Python, Google Java Style).
- **Tools**: Linters (ESLint, Pylint), formatters (Prettier, Black).

### 2. Clean Code Principles (Robert C. Martin)
- **Meaningful names** (variables, functions, classes).
- **Functions**:
  - Small, do one thing.
  - Few arguments (0–3 preferred).
  - No side effects.
- **Comments**: Explain *why*, not *what*.
- **Error handling** using exceptions, not error codes.
- **Avoid duplication** (DRY: Don't Repeat Yourself).

### 3. Refactoring
- **Definition**: Restructuring existing code without changing external behavior.
- **Common Refactorings**:
  - Extract Method, Rename Variable, Replace Magic Number with Constant.
  - Remove Duplicate Code, Split Loop.
- **When to refactor**:
  - Before adding new features.
  - During code reviews.
  - When fixing bugs (boy scout rule: leave cleaner than found).

### 4. Code Documentation
- **Inline vs. external**.
- **Docstrings / Javadoc / Doxygen**.
- **Self-documenting code** > excessive comments.

### 5. Version Control Integration (Git)
- Commit early and often.
- Write meaningful commit messages (Conventional Commits).
- Branching strategies (GitFlow, GitHub Flow).

### 6. Code Review Practices
- **Formal inspections** vs. lightweight reviews.
- **Checklists**: Correctness, clarity, consistency, performance.
- **Tools**: GitHub PRs, Gerrit, Crucible.

## Learning Activities
- Refactor a given poorly written code snippet.
- Peer review session with predefined checklist.

## Assessment
- Coding assignment with rubric: style, design, refactoring, documentation.
- Code review report (reviewer perspective).

## References
- Martin, R. C. *Clean Code*.
- Fowler, M. *Refactoring*.
- McConnell, S. *Code Complete*.
