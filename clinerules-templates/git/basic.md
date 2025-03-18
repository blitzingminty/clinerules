# Basic Git Rules

## Purpose

These rules establish minimal Git workflow requirements for individual developers or small teams prioritizing simplicity and flexibility. They provide fundamental structure while maintaining low overhead, making them ideal for personal projects, prototypes, and small-scale development efforts.

## Commit Requirements

### Commit Message Format

1. **Subject Line**
   - Must be concise (under 80 characters)
   - Should clearly describe what the commit does
   - Should use present tense ("Add feature" not "Added feature")

2. **Optional Body**
   - May include additional details about the change
   - Should explain why the change was made
   - Should be separated from the subject by a blank line

### Content Requirements

1. **Commit Scope**
   - Each commit should focus on a single logical change
   - Avoid mixing unrelated changes in one commit
   - Strive for smaller, focused commits over large omnibus commits

2. **Working Code**
   - Code should compile and run correctly
   - Basic tests should pass (if applicable)
   - Avoid committing commented-out code

## Branching Strategy

### Main Branch

1. **Main Branch Protection**
   - Main branch (main/master) should contain working code
   - Direct commits to main are acceptable for small projects
   - Consider using feature branches for larger changes

### Feature Branches

1. **Naming Convention**
   - Use descriptive names for branches
   - Consider using prefixes to indicate purpose (e.g., feature/, bugfix/)
   - Names should be lowercase with hyphens for spaces (e.g., feature/add-login)

2. **Branch Lifecycle**
   - Create branches from main/master
   - Merge or rebase changes from main/master regularly
   - Delete branches after merging

## Merging Process

### Pre-Merge Checks

1. **Review Requirements**
   - Self-review code changes before merging
   - Ensure code meets project standards
   - Verify changes fulfill their intended purpose

2. **Testing**
   - Run tests before merging (if applicable)
   - Manually test changes for expected behavior
   - Fix any issues before merging

### Merge Techniques

1. **Preferred Methods**
   - Regular merge or squash merge are both acceptable
   - Include a clear merge commit message if using regular merge
   - Ensure the merged code works properly

## Tagging and Versioning

### Version Tagging

1. **When to Tag**
   - Tag significant releases
   - Consider using semantic versioning (X.Y.Z)
   - Include a brief description with tags

## Best Practices

### General Workflow

1. **Regular Commits**
   - Commit changes regularly
   - Avoid long periods without committing
   - Use descriptive commit messages

2. **Backup and Remote**
   - Push to remote repository regularly
   - Use remotes as backup for your work
   - Consider using GitHub/GitLab/Bitbucket for additional tooling

3. **Repository Hygiene**
   - Include a .gitignore file
   - Don't commit large binary files
   - Don't commit sensitive information (passwords, API keys)

### Communication

1. **Documentation**
   - Keep README up to date
   - Document major decisions
   - Comment on complex or non-obvious changes

## Examples

### Good Commit Messages

```
Add user authentication functionality

Implement basic login/logout with password hashing.
Uses bcrypt for password storage and JWT for session management.
```

```
Fix navigation menu on mobile devices

Menu was not displaying correctly on screens smaller than 320px.
Changed CSS to use relative units instead of fixed pixels.
```

```
Update dependencies to address security vulnerability

Updates package X to version Y.Z which fixes CVE-2023-12345.
```

### Simple Branching Example

```
main
 ↑
 |
 +-- feature/add-login
 |    |
 |    +-- commit: "Create login form"
 |    |
 |    +-- commit: "Add validation"
 |    |
 |    +-- commit: "Connect to API"
 |
 +-- merge: "Add login functionality"
 |
 +-- bugfix/fix-typo
      |
      +-- commit: "Fix typo in welcome message"
      |
      +-- (merged to main)
```

## Exceptions

1. **Solo Projects**
   - For single-developer projects, some rules can be relaxed
   - Direct commits to main are more acceptable
   - Less formal process is needed for merging

2. **Experimental Work**
   - For experimental or proof-of-concept work, rules can be relaxed
   - Focus on capturing thought process in commits
   - Clean up history before sharing or formalizing

## Common Pitfalls to Avoid

1. **Commit Issues**
   - Avoid vague commit messages like "Fix stuff" or "Update"
   - Avoid very large commits that mix many different changes
   - Avoid committing temporary or debugging code

2. **Branch Management**
   - Avoid working on the wrong branch
   - Avoid letting branches get too out of date with main
   - Avoid keeping branches around after they're merged

3. **Merge Problems**
   - Avoid merging broken code
   - Resolve conflicts carefully
   - Test after merging to ensure everything still works
