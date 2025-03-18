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
