# ClinerRules: Rules for Claude

## Overview

ClinerRules is a standardized format for instructing Claude on various aspects of software development workflows. These rules empower users to clearly define expectations for documentation, Git practices, and coding standards, ensuring consistency, quality, and productivity across projects.

## Purpose and Benefits

- **Consistency**: Establish consistent standards across projects and teams
- **Efficiency**: Reduce time spent explaining standards to Claude
- **Quality**: Ensure higher quality output by applying proven best practices
- **Flexibility**: Select rule sets based on project needs and team expertise
- **Clarity**: Provide clear expectations for Claude to follow

## Categories

### Documentation Rules
Rules for comment formatting, documentation coverage, writing style, markup usage, and versioning practices.

- **Basic**: Minimal documentation for quick prototyping and personal projects
- **Standard**: Balanced documentation for typical professional projects
- **Strict**: Comprehensive documentation for critical or public-facing projects

### Git Rules
Rules for commit messages, branching strategies, merging practices, versioning, and issue linking.

- **Basic**: Simple Git workflow for individual developers or small teams
- **Standard**: Conventional commits and feature branch workflow for professional teams
- **Strict**: Rigorous commit standards and comprehensive branching strategy for large teams

### Coding Rules
Rules for code formatting, naming conventions, error handling, logging, security, performance, and complexity limits.

- **Basic**: Essential code quality rules for rapid development
- **Standard**: Comprehensive rules for professional software development
- **Strict**: Rigorous standards for mission-critical systems

## How to Use

1. **Select Rule Sets**: Choose the appropriate rule sets based on your project requirements and team expertise level
2. **Apply Rules**: Add relevant `.clinerules` files to your project
3. **Instruct Claude**: Tell Claude to follow the rules in the `.clinerules` directory
4. **Customize**: Modify rule sets as needed to meet your specific project requirements

## Automation Options

ClinerRules supports three implementation approaches to fit different workflow preferences:

### Manual Approach

The manual approach gives you complete control over which rules Claude follows:

1. Select the specific rule files you want (documentation, git, coding)
2. Copy them to your project's `.clinerules` directory
3. Instruct Claude to follow those specific rules

This approach is ideal when you want to tailor the ruleset precisely to your project needs.

### Automated Approach

The automated approach provides a comprehensive documentation and governance system with minimal setup:

1. Copy the `default.md` file from `clinerules-templates` to your project's `.clinerules` directory
2. Restart VS Code (to ensure Claude recognizes the new file)
3. **Important**: Your first interaction with Claude must focus ONLY on the PRIME DIRECTIVE. Simply ask: "Please check your PRIME DIRECTIVE" or "Have you read your PRIME DIRECTIVE?"

When Claude detects the default rule, it will:

1. Automatically initialize a `.my_stuff` documentation structure
2. Ask for your preferences on documentation, git, code quality, and implementation policies
3. Generate policy files based on your selections
4. Set up templates and documentation index
5. Maintain comprehensive documentation throughout the project

This approach is ideal for projects requiring thorough documentation and governance.

### Important Notes on Initialization

* **First interaction is critical**: Always make your first question specifically about the PRIME DIRECTIVE. Do not include any task requests in this first message.
* **Wait for complete initialization**: Let Claude fully set up the .my_stuff folder and policy files before requesting any tasks.
* **Avoid distractions**: Questions like "Can you help me with X while checking your PRIME DIRECTIVE?" may cause Claude to skip the initialization process.
* **Example phrases that work well**:
  - "Please check your PRIME DIRECTIVE"
  - "Have you read your PRIME DIRECTIVE?"
  - "Please review your AI instructions first"
* **Examples to avoid**:
  - "I need help with X, but first check your PRIME DIRECTIVE" (includes a task)
  - "Let's work on my project" (doesn't mention PRIME DIRECTIVE)

### Hybrid Approach

Combine both approaches by:

1. Using the automated `default.md` for documentation governance
2. Adding specific manual rules for other aspects like git or coding standards

This gives you both comprehensive documentation automation and precise control over specific rules.

## Rule Selection Guide

| Project Type | Documentation | Git | Coding |
|--------------|--------------|-----|--------|
| Personal project | Basic | Basic | Basic |
| Team prototype | Basic/Standard | Standard | Standard |
| Production application | Standard | Standard | Standard |
| Mission-critical system | Strict | Strict | Strict |
| Open source project | Standard/Strict | Standard | Standard/Strict |
| Regulated industry | Strict | Strict | Strict |

## Customization

These rule sets are designed to be customizable to your specific needs. You can:

1. Modify existing rule files to adjust requirements
2. Mix and match rules from different strictness levels
3. Create specialized rule sets for specific project types

## Contributing

These rule sets are living documents. As best practices evolve and as you discover what works best for your projects, consider:

1. Refining rules based on project experiences
2. Sharing successful rule configurations with the community
3. Creating specialized rule sets for specific technologies or domains
