# Python Documentation Rules (Standard)

## Purpose

These rules define a balanced documentation standard for professional Python projects.

## Docstring style

- Use Google-style docstrings consistently across modules, classes, and functions.
- Write docstrings in English with concise, explicit wording.
- Include `Args`, `Returns`, `Raises`, and `Examples` sections when applicable.
- Keep docstrings synchronized with function signatures and behavior.

## Coverage expectations

- Add module-level docstrings for all non-trivial modules.
- Document all public classes, public functions, and public methods.
- Document public constants when their meaning is not obvious.
- Add short comments for non-obvious business rules or algorithmic decisions.

## README requirements

- Maintain a root `README.md` with project purpose and scope.
- Document installation and environment setup steps.
- Document common usage patterns and runnable examples.
- Include testing, linting, and formatting commands.
- Include contribution and license information.

## Maintenance rules

- Update docs in the same change set as behavior changes.
- Treat stale documentation as a defect to be fixed.
- Ensure examples remain executable and accurate.
