# Python example setup

## What this example is

This example is a *Standard-tier* `.clinerules/` setup for a typical professional Python project.

It includes:

- `documentation.md` for Google-style docstrings, coverage expectations, and README guidance.
- `git.md` for Conventional Commits, feature-branch workflow, and issue linking.
- `coding.md` for PEP 8 style, naming, type hints, error handling, logging, and complexity limits.

## How to use this setup

1. Copy this example's `.clinerules/` directory into the root of your Python project.
2. Ensure your project now has files like:

   ```text
   .clinerules/documentation.md
   .clinerules/git.md
   .clinerules/coding.md
   ```

3. Instruct Cline to follow the rules in your `.clinerules/` directory.
4. Adjust the copied rules to match team preferences and domain requirements.

## Template mapping and tier swaps

This example is based on these *Standard* templates:

- [Documentation Standard](../../clinerules-templates/documentation/standard.md)
- [Git Standard](../../clinerules-templates/git/standard.md)
- [Coding Standard](../../clinerules-templates/coding/standard.md)

To use a different strictness level, replace one or more files with the corresponding template:

- `../../clinerules-templates/documentation/basic.md` or `../../clinerules-templates/documentation/strict.md`
- `../../clinerules-templates/git/basic.md` or `../../clinerules-templates/git/strict.md`
- `../../clinerules-templates/coding/basic.md` or `../../clinerules-templates/coding/strict.md`
