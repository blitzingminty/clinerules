# Basic Coding Rules

## Purpose

These rules establish essential code quality standards for rapid development, personal projects, and prototyping. They focus on fundamental best practices that improve code quality without imposing significant overhead, allowing for flexibility and speed while maintaining a baseline of quality.

## Formatting and Style

1. **Consistency**
   - Follow a consistent style throughout the codebase
   - Adhere to the established coding style of the project
   - Use an automatic formatter when available

2. **Indentation**
   - Use consistent indentation (spaces or tabs)
   - Maintain the same indentation level for related code blocks
   - Use proper alignment for readability

3. **Line Length**
   - Keep lines to a reasonable length (80-120 characters)
   - Break long statements into multiple lines for readability
   - Use appropriate line continuation techniques for your language

4. **Whitespace**
   - Use whitespace effectively to improve readability
   - Add empty lines to separate logical code sections
   - Be consistent with spacing around operators and keywords

## Naming Conventions

1. **Descriptive Names**
   - Use clear, descriptive names for variables, functions, and classes
   - Names should indicate purpose and usage
   - Avoid cryptic abbreviations and single-letter variables (except for common conventions like loop counters)

2. **Naming Style**
   - Follow language-specific naming conventions
   - Use camelCase, PascalCase, snake_case, etc. as appropriate for your language
   - Be consistent with the chosen style

3. **Name Length**
   - Names should be as short as possible while remaining descriptive
   - Use longer names for broader scopes and shorter names for local scopes
   - Avoid unnecessarily long names that reduce readability

## Code Structure

1. **Function/Method Size**
   - Keep functions and methods small and focused on a single task
   - Aim for no more than 20-30 lines per function
   - Extract complex logic into separate functions

2. **Function Parameters**
   - Limit the number of function parameters (ideally 3 or fewer)
   - Consider using object parameters for functions with many inputs
   - Keep related parameters grouped together

3. **Class/Module Organization**
   - Organize related functionality together
   - Separate unrelated functionality into different files
   - Group related classes and functions in a logical manner

## Comments and Documentation

1. **Comment Purpose**
   - Write comments to explain "why" not "what"
   - Comment complex or non-obvious code sections
   - Document any workarounds or temporary solutions

2. **Documentation**
   - Document public APIs with basic usage information
   - Include parameter descriptions and return values
   - Document any exceptions or errors that may occur

3. **Comment Maintenance**
   - Keep comments up-to-date with code changes
   - Remove obsolete or misleading comments
   - Prefer self-documenting code when possible

## Error Handling

1. **Basic Error Handling**
   - Handle expected error conditions
   - Prevent silent failures
   - Provide useful error messages

2. **Exception Usage**
   - Use exceptions for exceptional circumstances
   - Catch exceptions at appropriate levels
   - Don't use exceptions for normal flow control

3. **Defensive Programming**
   - Validate input data before processing
   - Check for null/undefined values when necessary
   - Include basic error recovery mechanisms

## Performance Considerations

1. **Basic Optimization**
   - Avoid unnecessary computations
   - Be mindful of loop efficiency
   - Watch for obvious performance issues

2. **Resource Management**
   - Close resources properly (files, connections, etc.)
   - Avoid memory leaks by cleaning up resources
   - Be aware of expensive operations

## Security Basics

1. **Input Validation**
   - Validate all user input before processing
   - Don't trust external data sources
   - Sanitize data before using in sensitive contexts

2. **Data Protection**
   - Don't hardcode sensitive information (passwords, API keys)
   - Protect user data appropriately
   - Be cautious with error messages containing sensitive information

## Examples

### Good Code Example

```javascript
// Calculate the total price including tax
function calculateTotalPrice(items, taxRate) {
  if (!items || !items.length) {
    return 0;
  }
  
  // Sum all item prices
  const subtotal = items.reduce((sum, item) => {
    return sum + (item.price * item.quantity);
  }, 0);
  
  // Apply tax rate
  const tax = subtotal * taxRate;
  
  return subtotal + tax;
}
```

### Bad Code Example

```javascript
// Avoid code like this
function calc(i, t) {
  let s = 0;
  // Loop through all items
  for (let x = 0; x < i.length; x++) {
    // Add price times quantity
    s = s + i[x].p * i[x].q;
  }
  // Calculate with tax
  return s + (s * t);
}
```

## Common Anti-patterns to Avoid

1. **Duplicate Code**
   - Avoid copying and pasting code
   - Extract repeated code into functions
   - Use abstraction to remove duplication

2. **Magic Numbers/Strings**
   - Avoid hardcoded values in logic
   - Use named constants for better readability
   - Document the meaning of necessary magic numbers

3. **Deep Nesting**
   - Avoid deep nesting of loops and conditionals
   - Use early returns to reduce nesting
   - Extract complex nested logic to separate functions

4. **Overly Complex Expressions**
   - Break complex expressions into simpler parts
   - Use intermediate variables for clarity
   - Keep boolean expressions simple and readable

## Implementation Flexibility

1. **Prototype Exceptions**
   - These rules can be relaxed for quick prototypes
   - Focus on core functionality first, then refine
   - Mark areas needing improvement with TODO comments

2. **Small Project Adaptations**
   - For small projects, some rules may be simplified
   - Maintain basic structure and naming conventions
   - Prioritize working code that's reasonably maintainable
