# Standard Coding Rules

## Purpose

These rules establish comprehensive standards for professional software development. They provide detailed guidance for code quality, maintainability, and reliability without being overly restrictive. This standard is suitable for most professional software projects, ensuring a balance between rigor and practicality.

## Code Formatting and Style

1. **Consistent Formatting**
   - Use a standard code formatter for the language (e.g., Prettier, Black, gofmt)
   - Configure the formatter in the project's repo (e.g., .prettierrc, .editorconfig)
   - Run formatting as part of CI/CD pipelines
   - Enforce consistent formatting across all files of the same type

2. **Indentation and Spacing**
   - Use consistent indentation (spaces/tabs per project convention)
   - Maintain 1-2 blank lines between functions and classes
   - Use single blank lines to separate logical sections within functions
   - Use consistent spacing around operators, after commas, and inside brackets

3. **Line Length and Wrapping**
   - Limit lines to 100 characters (or language/project convention)
   - Break long statements and function signatures in a readable manner
   - Align parameters and operands logically when wrapping
   - Follow language-specific conventions for line continuation

4. **Brace and Parenthesis Style**
   - Follow a consistent style for braces (e.g., K&R, Allman)
   - Match opening and closing braces/parentheses at the same indentation level
   - Use consistent spacing inside and outside braces/parentheses
   - For empty blocks, use a consistent style (e.g., `{}` or `{ }`)

## Naming Conventions

1. **General Naming Rules**
   - Use descriptive, unambiguous names that convey intent
   - Names should accurately reflect the purpose and behavior
   - Avoid misleading names or names with multiple possible interpretations
   - Use consistent terminology throughout the codebase

2. **Language-Specific Conventions**
   - Follow established conventions for the language (e.g., PascalCase for C# classes)
   - Use camelCase for variables/methods and PascalCase for classes in JavaScript/TypeScript
   - Use snake_case for Python variables/functions and PascalCase for classes
   - Adhere to framework-specific conventions where applicable

3. **Special Naming Patterns**
   - Prefix boolean variables with verbs like "is", "has", or "should"
   - Use noun phrases for objects and variables representing things
   - Use verb phrases for functions that perform actions
   - Use plural names for collections and arrays

4. **Constants and Enums**
   - Use UPPER_SNAKE_CASE for constants
   - Use descriptive enum names in singular form
   - Use descriptive names for enum values
   - Group related constants and enums

## Code Structure and Organization

1. **Function/Method Design**
   - Functions should do one thing and do it well
   - Limit function length to 30-50 lines maximum
   - Functions should operate at a single level of abstraction
   - Limit parameter count to 4 or fewer (use objects for more parameters)

2. **Class/Module Design**
   - Follow the Single Responsibility Principle
   - Keep classes focused on a specific concern
   - Limit class size to 300-500 lines
   - Organize members logically (e.g., properties, constructors, public methods, private methods)

3. **Code Organization**
   - Group related functionality in modules, packages, or namespaces
   - Organize files in a logical directory structure
   - Separate interface from implementation when appropriate
   - Keep side effects isolated and clearly documented

4. **Design Patterns**
   - Use appropriate design patterns to solve common problems
   - Document pattern usage in complex implementations
   - Avoid overengineering simple solutions with patterns
   - Apply patterns consistently within the codebase

## Documentation and Comments

1. **Code Documentation**
   - Document all public APIs, classes, and interfaces
   - Follow language-specific documentation formats (e.g., JSDoc, docstring)
   - Include parameter descriptions, return values, and exceptions
   - Document any assumptions, limitations, or edge cases

2. **Comment Guidelines**
   - Write comments that explain why, not what
   - Document complex algorithms or business rules
   - Comment workarounds, edge cases, and non-obvious behavior
   - Update comments when code changes

3. **Self-Documenting Code**
   - Write code that is self-explanatory when possible
   - Use descriptive names that reveal intent
   - Extract complex conditions into well-named methods
   - Prefer clear code over complex comments

4. **TODO and FIXME Comments**
   - Use consistent format for TODO comments
   - Include ticket/issue numbers in TODOs
   - Regularly review and address TODOs
   - Don't leave TODOs in production code without a plan to resolve them

## Error Handling

1. **Structured Error Handling**
   - Use structured error handling mechanisms (try/catch, Result types)
   - Never ignore exceptions without documentation
   - Catch specific exceptions rather than general ones
   - Preserve stack traces when re-throwing exceptions

2. **Error Reporting**
   - Provide clear, actionable error messages
   - Include context information in error messages
   - Log errors with appropriate severity levels
   - Consider internationalization for user-facing errors

3. **Error Recovery**
   - Implement graceful fallback behavior when appropriate
   - Fail fast for unrecoverable errors
   - Design robust retry mechanisms for transient failures
   - Consider circuit breakers for external dependencies

4. **Validation**
   - Validate all inputs at trust boundaries
   - Implement defensive programming for critical code paths
   - Provide clear validation failure messages
   - Distinguish between validation errors and runtime errors

## Logging

1. **Logging Levels**
   - Use appropriate log levels (error, warning, info, debug, trace)
   - Configure log verbosity differently per environment
   - Be consistent in log level usage across the application
   - Document log level usage guidelines

2. **Log Content**
   - Include relevant context in log messages
   - Use structured logging when possible
   - Include timestamp, source location, and correlation IDs
   - Avoid sensitive information in logs (PII, credentials)

3. **Log Performance**
   - Optimize high-volume logging for performance
   - Use guard clauses to avoid expensive logging operations
   - Consider asynchronous logging for high-throughput paths
   - Monitor and manage log storage and rotation

4. **Monitoring Integration**
   - Design logs to integrate with monitoring tools
   - Consider alerting needs when designing log messages
   - Include sufficient information for troubleshooting
   - Support correlation across components

## Security Best Practices

1. **Input Validation**
   - Validate all user-supplied inputs
   - Implement server-side validation in addition to client-side
   - Use parameterized queries to prevent SQL injection
   - Sanitize inputs used in HTML to prevent XSS

2. **Authentication and Authorization**
   - Use proven authentication frameworks/libraries
   - Implement proper password storage (hashing + salting)
   - Apply the principle of least privilege
   - Perform authorization checks at every level

3. **Sensitive Data Management**
   - Never hard-code sensitive information
   - Use appropriate encryption for sensitive data
   - Implement secure key management
   - Minimize storage of sensitive data

4. **Security Headers and Configuration**
   - Set appropriate security headers (CSP, X-Frame-Options, etc.)
   - Configure TLS properly
   - Use secure cookie flags
   - Keep dependencies updated to avoid known vulnerabilities

## Performance Considerations

1. **Resource Efficiency**
   - Use appropriate data structures for the task
   - Be mindful of memory allocations
   - Release resources promptly (close files, connections, etc.)
   - Cache expensive operations judiciously

2. **Algorithm Efficiency**
   - Select appropriate algorithms for the data size and operations
   - Consider time complexity and space complexity
   - Optimize critical paths and hot spots
   - Avoid premature optimization

3. **Database and I/O Operations**
   - Minimize database roundtrips
   - Use appropriate indexes
   - Optimize queries for common access patterns
   - Batch database operations when possible

4. **Asynchronous Processing**
   - Use asynchronous operations for I/O-bound work
   - Implement proper concurrency controls
   - Consider background processing for CPU-intensive tasks
   - Design for appropriate parallelism

## Code Complexity Management

1. **Cyclomatic Complexity**
   - Limit cyclomatic complexity to 10-15 per function
   - Extract complex conditional logic into separate functions
   - Use polymorphism over complex conditionals when appropriate
   - Break down complex algorithms into smaller steps

2. **Cognitive Complexity**
   - Minimize nesting levels (limit to 3-4 levels)
   - Use early returns to reduce nesting
   - Use guard clauses to handle edge cases first
   - Extract complex expressions into well-named variables

3. **Dependencies**
   - Minimize dependencies between components
   - Apply Dependency Injection patterns
   - Follow the Law of Demeter to reduce coupling
   - Design for testability

4. **Code Duplication**
   - Avoid copy-pasting code
   - Extract shared functionality into reusable components
   - Use inheritance or composition for shared behavior
   - Apply the DRY principle judiciously

## Testing Requirements

1. **Unit Testing**
   - Write unit tests for all new code
   - Maintain 70%+ code coverage
   - Test both normal and edge cases
   - Use mocks and stubs appropriately

2. **Test Structure**
   - Follow Arrange-Act-Assert pattern
   - Keep tests focused and atomic
   - Use descriptive test names that indicate scenario and expected outcome
   - Organize tests to mirror production code structure

3. **Test Quality**
   - Tests should be deterministic and repeatable
   - Avoid test interdependence
   - Ensure tests are maintainable
   - Balance test coverage with maintenance cost

4. **Integration and E2E Testing**
   - Write integration tests for critical paths
   - Test API contracts with contract tests
   - Include end-to-end tests for key user flows
   - Consider performance and load testing for critical systems

## Code Review Standards

1. **Review Process**
   - All code must be reviewed before merging
   - Reviews should focus on correctness, maintainability, and security
   - Use automated tools to catch style and basic issues
   - Provide constructive feedback with rationale

2. **Review Checklist**
   - Verify requirements are met
   - Check for security vulnerabilities
   - Ensure adequate test coverage
   - Verify adherence to code standards

3. **Review Responsiveness**
   - Respond to review comments promptly
   - Address all feedback before merging
   - Be open to alternative approaches
   - Thank reviewers for their input

## Examples

### Good Code Example

```typescript
/**
 * Calculates the total price for a collection of order items, 
 * including appropriate tax and any applicable discounts.
 * 
 * @param orderItems - The items in the order with quantity and price information
 * @param taxRate - The tax rate as a decimal (e.g., 0.07 for 7%)
 * @param discountCode - Optional discount code to apply to the order
 * @returns The calculated total price including tax and discounts
 * @throws {InvalidDiscountError} If the provided discount code is invalid
 */
function calculateOrderTotal(
  orderItems: OrderItem[],
  taxRate: number,
  discountCode?: string
): number {
  // Validate inputs
  if (!Array.isArray(orderItems) || orderItems.length === 0) {
    return 0;
  }
  
  if (taxRate < 0 || taxRate > 1) {
    throw new Error('Tax rate must be between 0 and 1');
  }
  
  // Calculate subtotal
  const subtotal = orderItems.reduce((sum, item) => {
    return sum + (item.price * item.quantity);
  }, 0);
  
  // Apply discount if provided
  let discountedSubtotal = subtotal;
  if (discountCode) {
    const discount = getDiscountAmount(discountCode, subtotal);
    discountedSubtotal = subtotal - discount;
  }
  
  // Calculate tax and total
  const taxAmount = discountedSubtotal * taxRate;
  const total = discountedSubtotal + taxAmount;
  
  return total;
}
```

### Bad Code Example (With Problems)

```typescript
// Calculates total
function calc(items, tax, discount) {
  // No items case
  if (!items || items.length == 0) return 0;
  
  var subtotal = 0;
  // Get subtotal
  for (var i = 0; i < items.length; i++) {
    subtotal += items[i].p * items[i].q; // price * quantity
  }
  
  // Apply discount
  if (discount && discount != "") {
    // 10% off for SAVE10, 15% for SAVE15, 20% for SAVE20
    if (discount == "SAVE10") {
      subtotal = subtotal * 0.9;
    } else if (discount == "SAVE15") {
      subtotal = subtotal * 0.85;
    } else if (discount == "SAVE20") {
      subtotal = subtotal * 0.8;
    }
  }
  
  // Calculate total with tax
  var total = subtotal * (1 + tax);
  return total;
}
```

## Common Anti-patterns to Avoid

1. **God Objects/Classes**
   - Classes that know or do too much
   - Classes with excessive responsibilities
   - Classes with too many instance variables
   - Classes that change for many different reasons

2. **Excessive Comments**
   - Commenting obvious code
   - Redundant comments that repeat the code
   - Outdated comments that no longer match the code
   - Using comments to justify bad code

3. **Feature Envy**
   - Methods that use more features of another class than its own
   - Methods that would be more appropriate in another class
   - Excessive calls to another object's getters and setters

4. **Primitive Obsession**
   - Using primitive types for domain concepts
   - Using strings for codes, IDs, or enumerations
   - Using magic numbers instead of named constants
   - Not creating types for important domain concepts
