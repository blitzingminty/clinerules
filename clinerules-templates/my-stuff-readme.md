<!-- PRIME DIRECTIVE REMINDER -->
<!-- Always update the memory bank after tasks and consult critical learnings -->
<!-- See .clinerules/default.md for full PRIME DIRECTIVE -->

# Project Knowledge & Memory Bank

## Overview

This directory (`.my_stuff`) serves as the project's institutional knowledge repository and memory bank. It contains documentation, templates, policies, and accumulated learnings that help Claude maintain consistency, avoid repeating past mistakes, and continuously improve its assistance.

## PRIME DIRECTIVE Compliance

All files in this memory bank include a PRIME DIRECTIVE reminder header to ensure:
- Consistent adherence to the project's governance standards
- Regular updates to the memory bank after each task
- Consultation of critical learnings before implementing solutions
- Compliance with established project policies

The PRIME DIRECTIVE reminder is maintained as the first element in every file created or updated by Claude.

## Purpose

The memory bank system is designed to:

1. **Preserve Knowledge**: Capture important learnings, decisions, and patterns
2. **Prevent Mistakes**: Maintain a registry of past issues and their solutions
3. **Promote Consistency**: Establish standard approaches to common problems
4. **Provide Context**: Store project history and evolution
5. **Progressively Improve**: Update with new learnings after each task

## Directory Structure

```
.my_stuff/
├── README.md                       # This overview file
├── documentation-index.md          # Central navigation hub
├── my_templates/                   # Templates for documentation
│   ├── implementation-plan-template.md
│   ├── progress-tracker-template.md
│   ├── learning-template.md
│   ├── mistake-template.md
│   ├── decision-template.md
│   └── pattern-template.md
├── memory/                         # Memory bank storage
│   ├── learnings.md                # Accumulated knowledge
│   ├── mistakes-registry.md        # Known issues and solutions
│   ├── decisions-log.md            # Project decisions history
│   └── patterns/                   # Code patterns directory
│       ├── successful-patterns.md  # Patterns that work well
│       └── anti-patterns.md        # Patterns to avoid
└── staging/                        # Policy file staging area
    └── [policy files]              # Policies before final placement
```

## How It Works

### Memory Update Process

After completing each task, Claude automatically:

1. **Extracts Learnings**: Documents new techniques, approaches, and knowledge
2. **Records Mistakes**: Captures any errors and their solutions
3. **Documents Decisions**: Records important design and implementation choices
4. **Identifies Patterns**: Recognizes effective patterns and anti-patterns
5. **Updates Cross-References**: Maintains links between related information

### Memory Usage During Tasks

Before implementing solutions, Claude consults:

1. The mistakes registry to avoid repeating known issues
2. The anti-patterns documentation to avoid problematic approaches
3. The learnings registry to apply accumulated knowledge
4. The decisions log for consistency with past decisions

## User Interaction

### How You Can Help

- **Review Updates**: Periodically review memory bank updates for accuracy
- **Suggest Additions**: Recommend important learnings or patterns to document
- **Provide Feedback**: Let Claude know if proposed solutions don't account for past learnings

### Managing the Memory Bank

The memory bank is maintained automatically, but you can:

- Request specific updates to any memory files
- Ask for summaries of learnings in specific areas
- Direct Claude to pay special attention to particular past issues or patterns

## Benefits

This system ensures:

- **Continuous Improvement**: Claude learns from each interaction
- **Institutional Knowledge**: Critical information isn't lost between sessions
- **Error Prevention**: Common mistakes aren't repeated
- **Consistency**: Solutions follow established patterns and decisions
- **Knowledge Transfer**: New team members can quickly understand project context

The memory bank allows Claude to provide increasingly effective assistance as your project evolves.
