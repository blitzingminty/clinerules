# ClineRules: Rules for Cline

## Overview

ClineRules is a standardized format for instructing Cline on various aspects of software development workflows. These rules empower users to clearly define expectations for documentation, Git practices, and coding standards, ensuring consistency, quality, and productivity across projects. ClineRules is designed to work alongside the [CLINE project](https://github.com/cline/cline) to enhance AI-assisted development workflows.

## Purpose and Benefits

- **Consistency**: Establish consistent standards across projects and teams
- **Efficiency**: Reduce time spent explaining standards to Cline
- **Quality**: Ensure higher quality output by applying proven best practices
- **Flexibility**: Select rule sets based on project needs and team expertise
- **Clarity**: Provide clear expectations for Cline to follow

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

See [AGENTS.md](AGENTS.md) for guidance on agent roles and personas, and how they complement the `.clinerules/` directory.

## How to Use

1. **Select Rule Sets**: Choose the appropriate rule sets based on your project requirements and team expertise level
2. **Create the directory**: Create a `.clinerules/` directory in your project root
3. **Apply Rules**: Copy the relevant rule files (e.g. `.clinerules/documentation.md`, `.clinerules/git.md`, `.clinerules/coding.md`) into that directory
4. **Instruct Cline**: Tell Cline to follow the rules in the `.clinerules/` directory
5. **Customize**: Modify rule sets as needed to meet your specific project requirements

Because `.clinerules/` is a directory of individual files, you can **enable or disable specific rules** at any time simply by adding or removing the corresponding file — no other configuration is required.

## Automation Options

ClineRules supports three implementation approaches to fit different workflow preferences:

### Manual Approach

The manual approach gives you complete control over which rules Cline follows:

1. Select the specific rule files you want (documentation, git, coding)
2. Copy them into your project's `.clinerules/` directory
3. Instruct Cline to follow those specific rules

This approach is ideal when you want to tailor the ruleset precisely to your project needs.

### Automated Approach

The automated approach provides a comprehensive documentation and governance system with minimal setup:

1. Copy the `default.md` file from `clinerules-templates` into your project's `.clinerules/` directory
2. Ask Cline to check for its "PRIME DIRECTIVE"

When Cline detects the default rule, it will:

1. Automatically initialize a `.my_stuff` documentation structure
2. Ask for your preferences on documentation, git, code quality, and implementation policies
3. Generate policy files based on your selections
4. Set up templates and documentation index
5. Maintain comprehensive documentation throughout the project

This approach is ideal for projects requiring thorough documentation and governance.

### Hybrid Approach

Combine both approaches by:

1. Using the automated `default.md` for documentation governance
2. Adding specific manual rules for other aspects like git or coding standards

This gives you both comprehensive documentation automation and precise control over specific rules.

## Examples

The [`examples/`](examples/README.md) directory provides copy-pasteable `.clinerules/` setups for common project types:

- [Python (Standard tier)](examples/python/README.md) — Standard documentation, Git, and coding rules for professional Python projects
- [TypeScript (Standard tier)](examples/typescript/README.md) — Standard documentation, Git, and coding rules for professional TypeScript projects

Open the example that matches your project type, copy its `.clinerules/` directory into your project root, and customize as needed.

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
4. **Toggle individual rules** by adding or removing the corresponding file from your `.clinerules/` directory

## Related Projects

### [CLINE](https://github.com/cline/cline)
CLINE is a command-line tool that enhances development workflows with AI assistance. ClineRules is specifically designed to integrate with CLINE to provide structured guidance and standards for AI-assisted development.

## Contributing

These rule sets are living documents. As best practices evolve and as you discover what works best for your projects, consider:

1. Refining rules based on project experiences
2. Sharing successful rule configurations with the community
3. Creating specialized rule sets for specific technologies or domains

---

*ClineRules is an enhancement for Cline developed to work with the [CLINE project](https://github.com/cline/cline).*

## License

ClineRules is licensed under the [Apache License 2.0](LICENSE).
