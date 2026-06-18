# AGENTS.md

## Overview

`AGENTS.md` is a place to describe the AI agent personas and roles that work within this repository, and to provide project-specific context that helps those agents approach tasks effectively. Where `.clinerules/` defines *what* agents must do (the rules, standards, and policies), `AGENTS.md` describes *who* the agents are — their roles, responsibilities, and how they should collaborate with the project.

This file is intended to be read by any AI agent or developer wanting to understand the agent landscape of the project before starting work.

## Relationship to `.clinerules/`

`.clinerules/` and `AGENTS.md` are complementary; they are meant to be used together.

| Concern | `.clinerules/` | `AGENTS.md` |
|---|---|---|
| Purpose | Defines rules and standards | Describes agent roles and project context |
| Content | Code style, commit conventions, documentation requirements | Personas, responsibilities, collaboration guidance |
| Scope | *How* tasks should be performed | *Who* performs them and *why* |
| Audience | Enforced for all agents and contributors | Read by agents to orient themselves |

When an agent begins a task it should consult both: `AGENTS.md` to understand its role and the project context, and the relevant `.clinerules/` files to understand the standards it must follow while executing that role.

## Recommended Placement

**Primary — repository root (`AGENTS.md`)**

A single `AGENTS.md` at the repository root is the recommended default. It is easy to discover, mirrors the familiar pattern of `README.md` and `CONTRIBUTING.md`, and works well when the project has a small number of agent roles that can be described in one file.

**Alternative — `.agents/` directory**

When a project requires many distinct agent definitions, or when each persona needs its own detailed specification, place individual agent files inside an `.agents/` directory (for example `.agents/reviewer.md`, `.agents/refactoring.md`). The root `AGENTS.md` can then serve as an index that links to those files.

## Example Agent Personas

### Documentation Agent

The Documentation Agent is responsible for keeping written documentation accurate, complete, and up to date as the codebase evolves.

**Responsibilities**

- Write and update inline code comments, README sections, and changelog entries.
- Ensure new features are documented before a pull request is merged.
- Flag areas of the codebase that lack sufficient documentation.

**Primary `.clinerules/` categories used**

- Documentation rules (basic / standard / strict, depending on project tier).
- Git rules — for commit messages that reference documentation changes.

### Code Review Agent

The Code Review Agent reviews pull requests and proposes improvements, catching issues before they reach the main branch.

**Responsibilities**

- Identify bugs, logic errors, and security concerns in changed code.
- Check that code follows the project's coding standards.
- Verify that commits conform to the project's git rules.
- Provide actionable, constructive feedback.

**Primary `.clinerules/` categories used**

- Coding rules (formatting, naming, error handling, complexity limits).
- Git rules (commit message format, branch naming).

### Refactoring Agent

The Refactoring Agent improves the internal structure of existing code without changing its external behavior.

**Responsibilities**

- Identify and reduce code duplication.
- Simplify overly complex functions or modules.
- Ensure that refactored code continues to pass all tests.
- Keep commits small and focused so changes are easy to review.

**Primary `.clinerules/` categories used**

- Coding rules (complexity limits, naming conventions).
- Git rules (atomic commits, conventional commit messages).
- Documentation rules — to update comments and docs that describe refactored areas.

## How Agents and `.clinerules/` Work Together

The following example shows a Documentation Agent completing a task according to the project's rules.

**Scenario:** A new helper function has been merged without inline documentation. The Documentation Agent is asked to add documentation.

```text
1. Agent reads AGENTS.md
   → Confirms it is acting as the Documentation Agent.
   → Notes responsibility: "Write and update inline code comments."

2. Agent reads .clinerules/documentation/standard.md
   → Learns the required comment format (e.g., JSDoc / docstring style).
   → Learns the minimum coverage requirement for public functions.

3. Agent reads .clinerules/git/standard.md
   → Learns commit message convention: "docs(<scope>): <description>".

4. Agent writes the missing documentation following the standard.

5. Agent commits with message: "docs(helpers): add JSDoc for parseConfig"
   → Message satisfies the git rule for conventional commits.
   → Change is scoped, small, and reviewable — satisfying the coding rule
     on atomic commits.
```

By combining the role context from `AGENTS.md` with the enforceable standards from `.clinerules/`, agents can work autonomously while remaining consistent with the project's quality expectations.

---

*For more on the `.clinerules/` rule sets and how to configure them, see the [README](README.md) and the [CLINE project](https://github.com/cline/cline).*
