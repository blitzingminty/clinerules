# Standard Git Rules

## Purpose

These rules establish professional Git workflow requirements for development teams. They provide a structured approach to version control with clear conventions for commits, branching, and merging. This standard balances rigor with practicality, making it suitable for most professional software development projects.

## Commit Standards

### Conventional Commits Format

All commits MUST follow the [Conventional Commits](https://www.conventionalcommits.org/) format:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

1. **Types**: Each commit message must begin with one of the following types:
   - `feat`: A new feature
   - `fix`: A bug fix
   - `docs`: Documentation only changes
   - `style`: Changes that do not affect the meaning of the code (formatting, etc.)
   - `refactor`: A code change that neither fixes a bug nor adds a feature
   - `perf`: A code change that improves performance
   - `test`: Adding missing tests or correcting existing tests
   - `build`: Changes that affect the build system or external dependencies
   - `ci`: Changes to CI configuration files and scripts
   - `chore`: Other changes that don't modify src or test files
   - `revert`: Reverts a previous commit

2. **Scope**: Optionally provide context about the change:
   - Should be a noun describing the section of the codebase (e.g., `auth`, `api`, `ui`)
   - Must be lowercase
   - May contain slashes for hierarchy (e.g., `api/users`)

3. **Description**:
   - Must be a brief summary of the change (less than 72 characters)
   - Must use imperative, present tense (e.g., "change", not "changed" or "changes")
   - Must not capitalize the first letter
   - Must not end with period

4. **Body**:
   - Should include the motivation for the change and contrast with previous behavior
   - Must use imperative, present tense
   - Must be separated from the description by a blank line
   - Should be wrapped at 72 characters

5. **Footer**:
   - May include `BREAKING CHANGE:` to indicate breaking API changes
   - May reference issues and PRs (e.g., `Fixes #123`, `Related to #456`)
   - May include other metadata as needed

### Commit Content Standards

1. **Atomic Commits**:
   - Each commit must represent a single, cohesive change
   - Commits should be as small as is practical while maintaining atomicity
   - Related changes should be grouped in a single commit

2. **Code Quality**:
   - Commits must not break the build
   - Commits must pass all automated tests
   - Commits must adhere to the project's code style
   - Commits should not include debugging code or commented-out code

## Branching Strategy

### Branch Types

1. **main/master**: 
   - Primary branch containing production-ready code
   - Protected from direct commits
   - Only merged into via pull/merge requests from approved branches

2. **develop**:
   - Integration branch for ongoing development
   - Contains the latest delivered development changes
   - Should always be in a deployable state
   - Protected from direct commits

3. **feature/\<issue-id\>-\<description\>**:
   - Used for developing new features
   - Created from: develop
   - Merges into: develop
   - Naming: `feature/ABC-123-add-login-page`

4. **bugfix/\<issue-id\>-\<description\>**:
   - Used for fixing non-critical bugs
   - Created from: develop
   - Merges into: develop
   - Naming: `bugfix/ABC-123-fix-login-redirect`

5. **hotfix/\<issue-id\>-\<description\>**:
   - Used for critical production fixes
   - Created from: main/master
   - Merges into: main/master AND develop
   - Naming: `hotfix/ABC-123-fix-security-vulnerability`

6. **release/v\<major\>.\<minor\>.\<patch\>**:
   - Used for preparing releases
   - Created from: develop
   - Merges into: main/master AND develop
   - Naming: `release/v1.2.0`

### Branch Lifecycle

1. **Branch Creation**:
   - Branches must be created from the appropriate parent branch
   - Branch names must follow the naming convention
   - Branch names should include the associated issue/ticket ID

2. **Branch Maintenance**:
   - Keep branches up to date with their parent branch (rebase or merge)
   - Keep branches focused on a single feature or fix
   - Delete branches after they are merged

3. **Branch Protection**:
   - main/master and develop branches must be protected
   - Direct pushes to protected branches must be prohibited
   - Force pushes to protected branches must be prohibited

## Pull/Merge Request Process

### PR/MR Creation

1. **Title and Description**:
   - Title must follow the same format as commit messages
   - Description must include:
     - What changes were made
     - Why the changes were made
     - Any notes on implementation details
     - References to related issues/tickets

2. **Content Requirements**:
   - PRs should represent a complete, cohesive change
   - Large changes should be broken into smaller, logical PRs when possible
   - PRs should include tests for new functionality or bug fixes
   - PRs should include documentation updates when relevant

3. **Draft PRs**:
   - Use draft/WIP PRs for work in progress
   - Indicate clearly what is missing or incomplete

### Code Review Requirements

1. **Review Process**:
   - At least one review is required for all PRs
   - Two reviews are recommended for complex changes
   - Author should respond to all feedback
   - Reviewers should provide constructive feedback

2. **Review Scope**:
   - Functionality: Does the code work as intended?
   - Code quality: Is the code well-structured and maintainable?
   - Tests: Are there appropriate tests?
   - Documentation: Is the documentation updated?
   - Standards: Does the code follow project standards?

3. **Addressing Feedback**:
   - All feedback must be addressed before merging
   - Feedback can be addressed by:
     - Making requested changes
     - Explaining why changes weren't made
     - Deferring changes to a future PR (with an issue created)

### Merge Requirements

1. **Pre-Merge Checks**:
   - All automated checks must pass
   - All required reviews must be approved
   - Any merge conflicts must be resolved
   - Code must be up to date with the target branch

2. **Merge Strategy**:
   - Feature and bugfix branches should be squashed when merged
   - Release and hotfix branches should be merged with a merge commit
   - Rebase merging is acceptable for maintaining a linear history

3. **Post-Merge Actions**:
   - Branch should be deleted after merging
   - Associated issues should be updated
   - Dependent work should be rebased as needed

## Release Management

### Version Numbering

1. **Semantic Versioning**:
   - Follow [Semantic Versioning 2.0.0](https://semver.org/)
   - Format: MAJOR.MINOR.PATCH
   - Increment MAJOR for incompatible API changes
   - Increment MINOR for backward-compatible functionality
   - Increment PATCH for backward-compatible bug fixes

2. **Pre-release Versions**:
   - Use suffixes for pre-release versions (e.g., `1.0.0-alpha.1`, `1.0.0-beta.2`)
   - Pre-release versions have lower precedence than normal versions

### Release Process

1. **Release Preparation**:
   - Create a release branch from develop
   - Only bug fixes are allowed in release branches
   - Version numbers and other release-specific changes are made in release branch
   - Test thoroughly in release branch

2. **Release Tagging**:
   - Tag releases in the repository with the version number
   - Tags should follow the format `v1.2.3`
   - Tags should include release notes
   - Tags should be GPG-signed when possible

3. **Release Notes**:
   - Group changes by type (Features, Bug Fixes, etc.)
   - Reference issue numbers
   - Highlight breaking changes
   - Include upgrade instructions when needed

## Repository Management

### Repository Configuration

1. **Required Files**:
   - README.md with project overview
   - LICENSE with license terms
   - .gitignore appropriate for the project type
   - CONTRIBUTING.md with contribution guidelines
   - CHANGELOG.md for tracking changes

2. **Branch Protection**:
   - Configure branch protection rules for main/master and develop
   - Require pull request reviews before merging
   - Require status checks to pass before merging
   - Do not allow bypassing the above settings

### Issue Tracking Integration

1. **Issue References**:
   - Reference issues in commit messages and PR descriptions
   - Use keywords to automatically close issues when appropriate (e.g., `Fixes #123`)
   - Keep issue status updated to reflect development status

2. **Branch Naming**:
   - Include issue IDs in branch names
   - Use descriptive branch names that indicate the content of the changes

## Best Practices

### General Workflow

1. **Regular Commits**:
   - Commit regularly with clear, atomic changes
   - Push changes to remote regularly
   - Keep PRs as small as practical while maintaining completeness

2. **Communication**:
   - Use PR comments to discuss code
   - Document significant decisions
   - Keep the team informed of major changes

3. **Git Hygiene**:
   - Don't commit sensitive information
   - Don't commit large binary files without LFS
   - Don't commit temporary or generated files

### Example Workflow

```
main
 ↑
 |
 +-- develop
      ↑
      |
      +-- feature/ABC-123-user-registration
      |    |
      |    +-- commit: "feat(auth): add user registration form"
      |    |
      |    +-- commit: "feat(auth): connect registration to API"
      |    |
      |    +-- commit: "test(auth): add tests for registration"
      |    |
      |    +-- (squash merge to develop)
      |
      +-- "feat(auth): implement user registration (#456)"
      |
      +-- feature/ABC-124-user-login
           |
           +-- commit: "feat(auth): add login form"
           |
           +-- commit: "feat(auth): implement JWT authentication"
           |
           +-- (continues...)
```

### Example Commit Messages

```
feat(auth): implement OAuth2 authentication

Add OAuth2 authentication flow with Google and GitHub providers.
This implementation uses the authorization code flow for better security.

Refs: #123
```

```
fix(ui): correct alignment of navigation menu on mobile

The navigation menu was misaligned on mobile devices with viewport
width less than 375px. This change makes the menu responsive and
properly aligned on all device sizes.

Fixes: #456
```

```
chore(deps): update dependencies to latest versions

Update all dependencies to their latest compatible versions.
- React: 17.0.2 -> 18.0.0
- TypeScript: 4.5.4 -> 4.6.3
- Jest: 27.4.7 -> 28.0.0

Breaking change in React 18 was addressed by updating component
lifecycle methods.
