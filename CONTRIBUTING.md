# Contributing to ClinerRules

Thank you for your interest in contributing to ClinerRules! This document provides guidelines and instructions for contributing to this project.

## Introduction

ClinerRules is a standardized format for instructing Claude on various aspects of software development workflows. The project aims to establish consistent standards, improve efficiency, ensure quality, and provide clarity in AI-assisted development.

We welcome contributions in several areas:
- New rule sets for different development contexts
- Improvements to existing rules
- Bug fixes
- Documentation enhancements
- Examples and use cases

## Getting Started

### Repository Setup

1. Fork the repository to your own GitHub account
2. Clone your fork to your local machine:
   ```
   git clone https://github.com/YOUR-USERNAME/clinerules.git
   cd clinerules
   ```
3. Add the original repository as an upstream remote:
   ```
   git remote add upstream https://github.com/blitzingminty/clinerules.git
   ```
4. Keep your fork up to date:
   ```
   git fetch upstream
   git merge upstream/main
   ```

### Development Environment

No special development environment is required for contributing to ClinerRules. A text editor with Markdown support is recommended for editing the rule files.

## Contribution Process

### Creating Issues

Before making changes, please:

1. Check existing issues to see if your idea or bug report has already been discussed
2. Create a new issue describing the problem or enhancement you're proposing
3. Wait for feedback and discussion before proceeding with implementation

### Branch Naming Conventions

When creating a branch for your contribution, please follow these naming conventions:

- `feature/brief-description` - For new features or rule sets
- `fix/brief-description` - For bug fixes
- `docs/brief-description` - For documentation improvements
- `refactor/brief-description` - For code refactoring without changing functionality

### Pull Request Process

1. Create a branch for your changes
2. Make your changes following the guidelines below
3. Commit your changes with clear, descriptive commit messages
4. Push your branch to your fork
5. Submit a pull request to the main repository
6. Respond to any feedback from maintainers

### Review Criteria

Pull requests will be reviewed based on:

- Adherence to the guidelines in this document
- Quality and clarity of the rule definitions
- Completeness of documentation
- Consistency with existing rules
- Value added to the project

## Guidelines for Rule Creation

### Style and Formatting

- Use clear, concise language in all rules
- Follow the established Markdown formatting patterns
- Organize rules logically, from general to specific
- Use bullet points for lists of requirements
- Include examples where appropriate

### Testing New Rules

Before submitting new rules:

1. Test them with Claude in a real project context
2. Verify that Claude can correctly interpret and apply the rules
3. Document any edge cases or limitations

### Documentation Requirements

All rule sets should include:

- A clear title and description
- Purpose and benefits
- Detailed requirements with examples
- Any necessary context or prerequisites
- Guidance on when to apply the rule set

### Compatibility Considerations

- Ensure new rules don't conflict with existing ones
- Consider how rules might interact across categories
- Document any dependencies between rules

## Category-Specific Guidelines

### Documentation Rules

- Focus on clarity, completeness, and usefulness
- Consider different documentation audiences (developers, users, etc.)
- Include guidelines for file-level, function-level, and inline documentation

### Git Rules

- Ensure compatibility with common Git workflows
- Consider team size and experience level when defining strictness
- Include examples of good and bad practices

### Coding Rules

- Balance strictness with practicality
- Consider performance, maintainability, and security implications
- Provide rationales for rules that might seem arbitrary

## Template Modifications

### Modifying Existing Templates

- Maintain the original purpose and structure
- Document improvements clearly in your PR
- Ensure backward compatibility where possible

### Adding New Templates

- Follow the established format and style
- Include clear documentation about when and how to use the template
- Demonstrate the template's value with examples

## Code of Conduct

### Community Standards

- Be respectful and inclusive in all communications
- Focus on constructive feedback rather than criticism
- Give and receive feedback graciously
- Assume good intentions from other contributors

### Communication Guidelines

- Keep discussions on-topic and professional
- Use clear, specific language
- Be patient with new contributors
- Document decisions and rationales

## Recognition

Contributors will be acknowledged in the project's README.md file. Significant contributions may result in maintainer status with direct commit access.

## Questions?

If you have any questions about contributing that aren't answered here, please open an issue labeled "question" in the repository.

Thank you for helping improve ClinerRules!
