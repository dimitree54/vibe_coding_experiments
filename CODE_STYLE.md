# Python Code Style Guide

## Naming Conventions

### Naming
- Use nouns for class and interface names
- Avoid prefixes and suffixes like Manager, Service, Handler, Processor, Helper, Data, Info in class and interface names
- Use singular form (not plural) in package and module names

## Programming Principles

### Principle Priority
We follow programming principles in this order: STUPID > KISS > SOLID > SoC

### Avoid STUPID Code
- **S - Singleton**: Use with caution, properly implemented Singleton is acceptable
- **T - Tight coupling**: Keep components loosely coupled
- **U - Untestability**: Write testable code
- **P - Premature optimization**: "Premature optimization is the root of all evil" - Donald Knuth
- **I - In-descriptive Naming**: Use clear, descriptive names
- **D - Duplication**: Don't Repeat Yourself (DRY)

### Code Reuse and DRY
- Before creating any function, first verify it doesn't already exist in the codebase
- If code is repeated in more than one place, merge it into a shared class, interface, method/function, or variable
- Extract common logic patterns into reusable functions or methods
- Use composition and inheritance to avoid duplicating behavior across classes
- Apply the "Rule of Three" - when you find yourself writing similar code for the third time, refactor it into a reusable component
- Avoid copy-paste programming - if you're copying code, consider if it should be extracted instead
- Use configuration or parameters to handle variations rather than duplicating entire functions with minor differences
- For similar algorithms with different values, parameterize the values rather than duplicating the algorithm

### KISS - Keep It Stupid Simple
Write simple, clear code that is easy to understand and maintain

### SOLID Principles
- **S - Single responsibility**: Each class/function should have one reason to change
- **O - Open-closed**: Open for extension, closed for modification
- **L - Liskov substitution**: Subtypes must be substitutable for their base types
- **I - Interface segregation**: Don't force clients to depend on interfaces they don't use
- **D - Dependency inversion**: Depend on abstractions, not concretions

### SoC - Separation of Concerns
Keep different concerns in different modules/classes/functions

## Module Structure and Imports

- Keep __init__.py files empty - they should only serve as package markers, not contain any code


## Type Safety

- Use TypedDict for structured dictionary types instead of generic Dict
- Provide proper type hints for all dictionary structures with known schemas
- Prefer immutable data structures (tuple over list, frozenset over set) when data doesn't need to change

## Environment Management

- Always work in `.env` virtual environment, never use or modify global Python interpreter

## Dependency Management

- Use `uv` for all dependency management operations
- Do not use `pip install` directly - all dependencies must be managed through `uv`
- Keep the pyproject.toml up-to-date. Do not just `uv pip install` something, use `uv add` instead
- pyproject.toml must contain version specifications for all packages - avoid unversioned dependencies to ensure reproducible builds
- When pyproject.toml is updated, always run `uv sync` to update uv.lock accordingly
- When committing changes that include pyproject.toml modifications, always commit uv.lock as well in the same commit

## Testing Requirements

- Maintain minimum test coverage of 80% for all Python code
- Write proper asserting tests rather than logging tests - tests must use assertions to verify behavior, not just log outputs
- Keep debugging and testing logic separate from production logic - production code should not contain test-specific conditions or adapt to testing environments
- Avoid over-mocking - prefer testing with real data or saved test data over excessive mocking; mock only external dependencies that cannot be reproduced locally

## HTML Processing

- Use lxml as the HTML parsing engine for better performance when using BeautifulSoup
- Prefer BeautifulSoup operations over regex for HTML manipulation
- Use tenacity library for retry logic instead of custom retry implementations

### **Revised Exception Handling Rules**

1.  **Fail Fast and Avoid Silent Errors**
    *   The default behavior for any failure should be to raise an explicit, descriptive exception. Avoid masking problems with fallback values, default behaviors, or by catching exceptions only to ignore them. Let errors propagate unless you have a specific, approved recovery strategy.

2.  **Startup Failures Must Be Fatal**
    *   The application must never start in a degraded or unpredictable state. Any failure during initialization—such as loading configuration, checking dependencies, or reading critical data files—should terminate the process immediately with a clear error message.

3.  **Handle Runtime Errors Gracefully but Deliberately**
    *   During runtime (e.g., while a server is handling requests), it may be acceptable to handle an error without crashing the entire application. However, this must be a conscious decision. Such recovery logic (like logging an error and returning an error response) requires review and approval to prevent unintentionally hiding problems.

## Performance and Object Lifecycle Management

- Separate initialization and runtime logic - create expensive objects during initialization, not during runtime
- Avoid repeated object creation - if an object can be created once and reused across multiple function calls, create it at initialization time
- Be careful with object creation in loops - move object creation outside loops when possible, or to class initialization
- Cache expensive computations - store results of expensive operations that don't change between calls
- Examples of objects to create at init time: HTTP clients, database connections, compiled regex patterns, configuration objects, loggers

## Code Quality and Development Workflow

### Comment Guidelines
- Write comments only if they bring additional information beyond what the code expresses
- Well-named classes, methods, and variables should not need redundant explanatory comments
- Comments should explain "why" not "what" - the code itself shows what it does
- Avoid obvious comments that restate what the code is doing
- Prioritize self-documenting code through meaningful names over explanatory comments

## Security

### Input/Output Sanitization
- Always escape, sanitize, or filter all input and output based on context
- Validate and sanitize file paths to prevent directory traversal attacks