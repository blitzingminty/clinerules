# Critical Learnings

This document contains critical, foundational knowledge that has been elevated from the memory bank to serve as mandatory rules. These learnings represent essential knowledge that must be applied across all project work.

**Last Full Review:** [DATE]

## How to Use This Document

- Treat each entry as a mandatory rule, not just as reference information
- Apply these learnings in all relevant contexts
- Follow the linked references for more detailed implementation guidance
- If a learning seems to conflict with current requirements, seek clarification before proceeding

## Architectural Foundations

### Core Architecture Patterns

**[Critical Learning Title]**
- **Description:** [Clear, concise description of the critical learning]
- **Rationale:** [Why this is critical to the project]
- **Example:** [Brief example of application]
- **Reference:** [Link to detailed documentation in the memory bank]
- **Last Updated:** [DATE]

### Technology Constraints

**Environment-Specific Configurations**
- **Description:** All deployment configurations must account for differences between development, staging, and production environments, especially regarding external service endpoints and security settings.
- **Rationale:** Prevents production outages caused by environment mismatches
- **Example:** Using environment variables for all environment-specific values and loading them appropriately per environment
- **Reference:** [.my_stuff/memory/mistakes-registry.md#environment-configuration-mismatch]
- **Last Updated:** 2025-03-15

## Performance Essentials

**Database Query Optimization**
- **Description:** Always use proper indexing and avoid N+1 query patterns when fetching related data from the database.
- **Rationale:** Prevents exponential performance degradation as data volume grows
- **Example:** Use eager loading with proper `include` statements for ORM queries or JOIN clauses in raw SQL
- **Reference:** [.my_stuff/memory/learnings.md#learning-optimizing-database-queries]
- **Last Updated:** 2025-03-10

**Resource Cleanup**
- **Description:** All resource acquisitions (file handles, database connections, network sockets) must have corresponding release mechanisms, preferably in finally blocks or disposal patterns.
- **Rationale:** Prevents resource leaks that can crash the application over time
- **Example:** Using try-with-resources in Java or using/dispose pattern in C#
- **Reference:** [.my_stuff/memory/mistakes-registry.md#resource-leak-in-file-processing]
- **Last Updated:** 2025-03-05

## Security Fundamentals

**Input Validation**
- **Description:** All user inputs must be validated both client-side and server-side with appropriate sanitization for the context of use.
- **Rationale:** Prevents injection attacks and data corruption
- **Example:** Validating and sanitizing user input differently for SQL queries, HTML context, and JSON payloads
- **Reference:** [.my_stuff/memory/patterns/successful-patterns.md#pattern-input-validation-strategy]
- **Last Updated:** 2025-03-02

**Authentication Token Handling**
- **Description:** Authentication tokens must never be stored in localStorage or sessionStorage, and should be stored in HTTP-only cookies with appropriate expiration.
- **Rationale:** Prevents XSS attacks from stealing authentication credentials
- **Example:** Setting JWT tokens in HTTP-only cookies with secure and SameSite flags
- **Reference:** [.my_stuff/memory/decisions-log.md#decision-jwt-authentication-strategy]
- **Last Updated:** 2025-02-28

## Error Handling

**Graceful Degradation**
- **Description:** The application must be designed to function with limited capabilities when non-critical dependencies are unavailable, rather than failing completely.
- **Rationale:** Maintains core functionality during partial outages
- **Example:** Displaying cached content when API calls fail, providing offline capabilities when possible
- **Reference:** [.my_stuff/memory/patterns/successful-patterns.md#pattern-circuit-breaker-for-external-services]
- **Last Updated:** 2025-02-25

**Error Boundaries**
- **Description:** Errors must be contained at appropriate boundaries to prevent cascading failures, with proper fallback UI for frontend components.
- **Rationale:** Isolates failures to minimize user impact
- **Example:** Using React Error Boundaries around major UI sections, implementing bulkhead pattern in microservices
- **Reference:** [.my_stuff/memory/mistakes-registry.md#cascading-failure-in-component-tree]
- **Last Updated:** 2025-02-20

## UI/UX Principles

**Accessibility Requirements**
- **Description:** All user interfaces must meet WCAG 2.1 AA compliance, including proper semantic markup, keyboard navigation, and screen reader support.
- **Rationale:** Ensures usability for all users and meets legal requirements
- **Example:** Using proper heading structure, providing alt text for images, ensuring sufficient color contrast
- **Reference:** [.my_stuff/memory/learnings.md#learning-accessibility-implementation]
- **Last Updated:** 2025-02-15

## Testing Standards

**Test Data Independence**
- **Description:** Tests must create and manage their own test data and not rely on pre-existing data in the test environment.
- **Rationale:** Ensures tests are repeatable and isolated
- **Example:** Using factories or fixtures to generate test data within each test, cleaning up after test execution
- **Reference:** [.my_stuff/memory/mistakes-registry.md#non-repeatable-test-failures]
- **Last Updated:** 2025-02-10

## Implementation Patterns

**State Management Isolation**
- **Description:** UI component state should be categorized as local, shared, or global, with appropriate management strategies for each type.
- **Rationale:** Prevents state management complexity and performance issues
- **Example:** Using local useState for component-specific state, Context API for shared state, and Redux for global application state
- **Reference:** [.my_stuff/memory/learnings.md#learning-effective-state-management-in-react]
- **Last Updated:** 2025-02-05

## Maintenance and Operations

**Logging Standards**
- **Description:** All logging must include contextual information (request ID, user ID if applicable, timestamp) and use appropriate severity levels.
- **Rationale:** Enables effective troubleshooting in production
- **Example:** Using structured logging with consistent fields across all services
- **Reference:** [.my_stuff/memory/patterns/successful-patterns.md#pattern-structured-logging]
- **Last Updated:** 2025-02-01

## How to Update This Document

1. **Adding New Critical Learnings**:
   - Verify that the learning meets at least one of the critical learning criteria
   - Use clear, concise language that focuses on the rule rather than explanation
   - Include all required sections (Description, Rationale, Example, Reference, Last Updated)
   - Add to the appropriate category, creating a new one if necessary

2. **Updating Existing Critical Learnings**:
   - Preserve the original learning if still relevant, but clarify or expand as needed
   - Update the "Last Updated" timestamp
   - Add new examples if they provide additional clarity
   - Update references to point to the most current detailed documentation

3. **Removing Outdated Critical Learnings**:
   - Remove learnings that are no longer applicable or have been superseded
   - Consider moving deprecated learnings to a historical section if they provide valuable context
   - Update the document's "Last Full Review" timestamp when doing comprehensive reviews
