# Python Coding Rules (Standard)

## Purpose

These rules establish maintainable, production-ready coding standards for Python projects.

## Formatting and style

- Follow PEP 8 consistently.
- Use a standard formatter such as Black for all Python source files.
- Use import sorting (for example, isort) with stable configuration.
- Keep lines readable and prefer small, focused functions.

## Naming conventions

- Use `snake_case` for variables, functions, and module names.
- Use `PascalCase` for classes.
- Use `UPPER_SNAKE_CASE` for module-level constants.
- Choose names that reflect domain meaning, not implementation trivia.

## Type hints

- Add type hints to all public functions and methods.
- Add return types explicitly for public callables.
- Prefer precise types over overly broad `Any`.
- Keep type annotations compatible with static checking.

## Error handling

- Raise specific exceptions with actionable messages.
- Do not swallow exceptions silently.
- Validate external inputs at boundaries.
- Use `try`/`except` only around code that can fail in expected ways.

## Logging

- Use the standard `logging` module instead of `print` for runtime diagnostics.
- Use appropriate levels (`DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`).
- Include contextual fields that support debugging and incident response.
- Never log secrets, credentials, tokens, or personal data.

## Complexity guideline

- Target cyclomatic complexity of 10 or less per function.
- Prefer early returns and helper extraction over deep nesting.
- Refactor functions that exceed three nested control-flow levels.
