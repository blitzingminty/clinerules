# Basic Documentation Rules

## Purpose

These rules establish minimal documentation requirements for quick prototyping, personal projects, and situations where development speed is prioritized over comprehensive documentation. They focus on essential code comments and basic README content to ensure fundamental understanding without imposing significant documentation overhead.

## Requirements

### Project Documentation

1. **README Requirements**
   - Project must include a basic README.md with:
     - Project name and purpose
     - Setup/installation instructions
     - Basic usage examples
     - Dependencies list

2. **API Documentation**
   - Public APIs must have minimal documentation describing:
     - Purpose of the API
     - Required parameters
     - Return values

### Code Documentation

1. **Comment Requirements**
   - Comments required for:
     - Non-obvious code sections
     - Complex algorithms
     - Workarounds or temporary solutions
     - Public functions/methods (purpose and parameters)

2. **Documentation Format**
   - Use standard documentation formats for the language (e.g., JSDoc, docstrings)
   - Comments should be concise and to the point

3. **Naming Practices**
   - Use descriptive names for variables, functions, and classes
   - Names should indicate purpose without requiring additional comments

## Exemptions

1. **Exempted Components**
   - Throw-away prototype code
   - Simple, self-explanatory utility functions
   - Temporary debugging code

2. **Exemption Process**
   - Clearly mark exempted code with `// TEMP` or `// PROTOTYPE` comments
   - Exemptions should be regularly reviewed and removed when no longer applicable

## Best Practices

1. **Documentation Timing**
   - Document code while writing it, not afterwards
   - Update documentation when changing functionality

2. **Quality over Quantity**
   - Focus on writing fewer, but more meaningful comments
   - Avoid obvious comments that simply restate the code
   - Explain "why" rather than "what" when possible

3. **Maintenance**
   - Remove outdated comments
   - Keep README updated with major changes

## Examples

### Good README Example

```markdown
# Simple Task Manager

A command-line tool for managing personal tasks.

## Setup

```bash
npm install
npm start
```

## Usage

```bash
# Add a new task
node app.js add "Buy groceries"

# List all tasks
node app.js list

# Mark task as complete
node app.js complete 1
```

## Dependencies
- Node.js v14+
- Commander.js for CLI interface
```

### Good Code Comment Examples

```javascript
// Cache results to avoid recalculating on each request
function getCalculatedValue(input) {
  if (cache[input]) return cache[input];
  
  const result = expensiveCalculation(input);
  cache[input] = result;
  return result;
}

/**
 * Validates user input against security rules
 * @param {string} input - The user-provided input
 * @returns {boolean} True if valid, false otherwise
 */
function isValidInput(input) {
  // Using regex for validation to prevent injection attacks
  return /^[a-zA-Z0-9_\-]+$/.test(input);
}
```

### Bad Code Comment Examples

```javascript
// Avoid comments like these:

// This function adds two numbers
function add(a, b) {
  return a + b;
}

// Loop through the array
for (let i = 0; i < array.length; i++) {
  // Get the current item
  const item = array[i];
  // Process the item
  process(item);
}
