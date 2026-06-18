# TypeScript Coding Rules (Standard)

## Purpose

These rules establish maintainable, production-ready coding standards for TypeScript projects.

## Formatting and style

- Use Prettier as the default formatter for TypeScript, JavaScript, JSON, and Markdown.
- Keep ESLint enabled and treat lint violations as defects.
- Prefer explicit, readable code over compact but unclear expressions.
- Keep modules focused and avoid oversized files.

## Naming conventions

- Use `camelCase` for variables, functions, and methods.
- Use `PascalCase` for classes, interfaces, and type aliases.
- Use `UPPER_SNAKE_CASE` for constants.
- Use descriptive names that reflect domain intent.

## Strict typing expectations

- Enable strict TypeScript settings, including `strict: true`.
- Avoid `any`; use precise union, interface, and generic types.
- Model external data with runtime validation at boundaries.
- Explicitly type exported function signatures.

## Error handling

- Throw or propagate typed errors with actionable messages.
- Handle rejected promises explicitly.
- Validate untrusted inputs before business logic execution.
- Do not hide exceptions in empty `catch` blocks.

## Async and concurrency guidance

- Prefer `async`/`await` over raw promise chains for readability.
- Use `Promise.all` only when operations are truly independent.
- Apply timeouts or cancellation for long-running external calls.
- Avoid unbounded parallelism in loops.

## Complexity guideline

- Target cyclomatic complexity of 10 or less per function.
- Keep nesting shallow by using guard clauses and early returns.
- Extract helpers when conditionals become difficult to reason about.
