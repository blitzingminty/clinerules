# TypeScript Documentation Rules (Standard)

## Purpose

These rules define a balanced documentation standard for professional TypeScript projects.

## Comment style

- Use TSDoc or JSDoc consistently for exported APIs.
- Document intent, parameters, return values, and thrown errors when relevant.
- Add `@remarks` or `@example` for behavior that is not obvious.
- Keep comments aligned with actual runtime behavior and type signatures.

## Coverage expectations

- Document all exported functions, classes, interfaces, and types.
- Document public class members that are part of the external contract.
- Add module-level context for non-trivial packages or entrypoints.
- Add short explanatory comments for complex domain logic.

## README requirements

- Maintain a root `README.md` with project purpose and architecture overview.
- Include installation, local development, and build instructions.
- Provide usage examples for primary entrypoints or APIs.
- Document testing, linting, and formatting commands.
- Include contribution and license information.

## Maintenance rules

- Update docs whenever API behavior or contracts change.
- Keep examples valid against current code and dependencies.
- Treat missing export documentation as a quality defect.
