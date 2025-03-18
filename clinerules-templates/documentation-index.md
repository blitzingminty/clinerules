# Project Documentation Index

This document serves as the central navigation hub for all project documentation. Use this index to find specific information about the project, its implementation, and the institutional knowledge we've accumulated.

Last Updated: [Current Date]

## Quick Links

- [Project Overview](../README.md)
- [Critical Learnings](../.clinerules/critical-learnings.md)
- [Policy Documentation](#policy-documentation)
- [Memory Bank](#memory-bank)
- [Templates](#templates)
- [Current Progress](#current-progress)

## Critical Learnings

The critical learnings file contains foundational knowledge that must be treated as mandatory rules:

| Document | Description | Path |
|--------|-------------|------|
| Critical Learnings | Mandatory rules derived from project experience | `.clinerules/critical-learnings.md` |

## Policy Documentation

These documents define the standards and guidelines that govern the project development:

| Policy | Description | Path |
|--------|-------------|------|
| Documentation Policy | Standards for project documentation | `.clinerules/documentation-policy.md` |
| Git Policy | Standards for version control practices | `.clinerules/git-policy.md` |
| Code Quality Policy | Standards for code quality and practices | `.clinerules/code-quality-policy.md` |
| Implementation Policy | Standards for implementation approach | `.clinerules/implementation-policy.md` |

## Memory Bank

The memory bank stores accumulated knowledge and learnings from project development:

### Learnings Repository
📁 [Learnings Registry](memory/learnings.md) - Collection of knowledge gained during development

**Recent Learnings:**
- [State Management in React](memory/learnings.md#learning-effective-state-management-in-react)
- [Database Query Optimization](memory/learnings.md#learning-optimizing-database-queries)
- [Accessibility Implementation](memory/learnings.md#learning-accessibility-implementation)

### Mistakes Registry
📁 [Mistakes Registry](memory/mistakes-registry.md) - Documentation of issues encountered and their solutions

**Key Mistakes to Avoid:**
- [N+1 Query Performance Issues](memory/mistakes-registry.md#mistake-n1-query-performance-issue)
- [Memory Leaks in React Components](memory/mistakes-registry.md#mistake-memory-leak-in-component-lifecycle)
- [Timezone Handling Errors](memory/mistakes-registry.md#mistake-incorrect-timezone-handling)

### Decisions Log
📁 [Decisions Log](memory/decisions-log.md) - Record of key architectural and implementation decisions

**Recent Decisions:**
- [TypeScript Adoption](memory/decisions-log.md#decision-adopt-typescript-for-frontend-development)
- [JWT Authentication Strategy](memory/decisions-log.md#decision-implement-jwt-authentication-strategy)
- [Microservices Architecture](memory/decisions-log.md#decision-move-to-microservices-architecture)

### Code Patterns
📁 [Successful Patterns](memory/patterns/successful-patterns.md) - Effective patterns to adopt
📁 [Anti-Patterns](memory/patterns/anti-patterns.md) - Patterns to avoid

**Recommended Patterns:**
- [Repository Abstraction](memory/patterns/successful-patterns.md#pattern-repository-abstraction)
- [Feature Flag Configuration](memory/patterns/successful-patterns.md#pattern-feature-flag-configuration)
- [Circuit Breaker Pattern](memory/patterns/successful-patterns.md#pattern-circuit-breaker-for-external-services)

**Patterns to Avoid:**
- [God Component](memory/patterns/anti-patterns.md#anti-pattern-god-component)
- [Direct DOM Manipulation with React](memory/patterns/anti-patterns.md#anti-pattern-direct-dom-manipulation-with-react)
- [Nested Callback Hell](memory/patterns/anti-patterns.md#anti-pattern-nested-callback-hell)

## Templates

These templates should be used when creating new documentation:

| Template | Description | Path |
|----------|-------------|------|
| Implementation Plan | Template for planning implementation | `my_templates/implementation-plan-template.md` |
| Progress Tracker | Template for tracking project progress | `my_templates/progress-tracker-template.md` |
| Learning Entry | Template for documenting new learnings | `my_templates/learning-template.md` |
| Mistake Entry | Template for documenting mistakes | `my_templates/mistake-template.md` |
| Decision Record | Template for documenting decisions | `my_templates/decision-template.md` |
| Pattern Documentation | Template for documenting patterns | `my_templates/pattern-template.md` |

## Current Progress

- **Project Status**: [In Progress/Completed/Planning]
- **Current Sprint**: [Sprint Name/Number]
- **Key Milestones**: [List of upcoming milestones]

### Recent Updates

1. [Date] - [Significant update or milestone]
2. [Date] - [Significant update or milestone]
3. [Date] - [Significant update or milestone]

### Upcoming Work

1. [Task or feature]
2. [Task or feature]
3. [Task or feature]

## How to Use This Documentation

1. **Finding Information**: Use this index as your starting point to navigate to specific documentation
2. **Contributing**: Follow the Documentation Policy and use the appropriate templates
3. **Memory Bank**: Consult the Memory Bank before implementing solutions to avoid known pitfalls
4. **Updates**: Keep documentation up-to-date as the project evolves

Remember that this documentation represents our collective knowledge and serves as a critical resource for current and future development.
