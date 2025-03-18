# Strict Git Rules

## Purpose

These rules establish a rigorous and comprehensive framework for version control practices in critical projects or large teams. They ensure code integrity, maintainability, and traceability through strict adherence to standardized processes. This policy enforces high-quality commit standards, a well-defined branching strategy, and mandatory review processes to maintain a clean, well-documented history.

## Commit Standards

### Commit Message Format

All commit messages MUST follow this precise structure:

```
<type>(<scope>): <subject>

<body>

<footer>
```

1. **Type**: Must be one of the following, exactly as written:
   - `feat`: A new feature
   - `fix`: A bug fix
   - `docs`: Documentation only changes
   - `style`: Changes that do not affect the meaning of the code
   - `refactor`: A code change that neither fixes a bug nor adds a feature
   - `perf`: A code change that improves performance
   - `test`: Adding missing tests or correcting existing tests
   - `build`: Changes that affect the build system or external dependencies
   - `ci`: Changes to CI configuration files and scripts
   - `chore`: Other changes that don't modify src or test files
   - `revert`: Reverts a previous commit

2. **Scope**: Must be included and specify the component affected:
   - Must be a noun describing the component (e.g., `auth`, `api`, `database`)
   - Must be lowercase with no spaces
   - Must use consistent naming across the project
   - May use slash hierarchy for nested components (e.g., `api/users`)

3. **Subject**:
   - Must not exceed 50 characters
   - Must use imperative, present tense (e.g., "change", not "changed" or "changes")
   - Must not capitalize the first letter
   - Must not end with a period
   - Must describe what the commit does, not why

4. **Body**:
   - Must be included for all non-trivial changes
   - Must use imperative, present tense
   - Must explain the motivation for the change
   - Must contrast with previous behavior
   - Must be separated from the subject by a blank line
   - Must be wrapped at 72 characters per line
   - Must be separated from the footer by a blank line

5. **Footer**:
   - Must include issue references (e.g., `Fixes #123`, `Related to #456`)
   - Must document breaking changes with `BREAKING CHANGE:` prefix
   - Must use `Co-authored-by:` for multiple authors
   - Each footer item must be on a separate line

### Commit Content Standards

1. **Atomic Commits**:
   - Each commit must represent a single, cohesive change
   - Commits must not mix different concerns
   - Commits must not include unrelated changes
   - Commits must be as small as possible while maintaining atomicity

2. **Code Quality**:
   - Every commit must compile and pass all tests
   - All commits must adhere to the project's code style
   - Commits must not introduce technical debt without documentation
   - Commits must not include debug code, commented-out code, or TODOs without issues

3. **Commit Verification**:
   - All commits must be GPG-signed by their author
   - Author details must match the verified identity
   - All commits must pass the pre-commit hook validations
   - Commits with code changes must include or be linked to relevant tests

## Branching Strategy

### Branch Types

1. **main/master**: Production-ready code only.
   - Absolutely protected from direct commits
   - Only accepts merges from release and hotfix branches
   - Each commit must correspond to a tagged release
   - History must be linear and must never be rewritten

2. **develop**: Integration branch for ongoing development.
   - Protected from direct commits
   - Must always be in a deployable state
   - Accepts merges only from feature, bugfix, and release branches
   - Regular CI/CD builds must validate stability

3. **feature/\<issue-id\>-\<description\>**: For new features.
   - Created from: develop
   - Merges into: develop only
   - Must reference an issue/ticket ID
   - Must include descriptive name (e.g., `feature/PROJ-123-implement-oauth`)

4. **bugfix/\<issue-id\>-\<description\>**: For non-critical bugs.
   - Created from: develop
   - Merges into: develop only
   - Must reference an issue/ticket ID
   - Must include descriptive name (e.g., `bugfix/PROJ-456-fix-login-redirect`)

5. **hotfix/\<issue-id\>-\<description\>**: For critical production fixes.
   - Created from: appropriate release tag in main/master
   - Merges into: main/master AND develop
   - Must reference an issue/ticket ID
   - Must include descriptive name (e.g., `hotfix/PROJ-789-fix-security-vulnerability`)

6. **release/v\<major\>.\<minor\>.\<patch\>**: For release preparation.
   - Created from: develop
   - Merges into: main/master AND develop
   - Must use semantic versioning format (e.g., `release/v1.2.0`)
   - Only bug fixes allowed, no new features

### Branch Lifecycle

1. **Branch Creation**:
   - Branches must be created using project tooling or standard commands
   - Branch names must strictly follow the naming convention
   - Branch must be tied to specific, documented requirements
   - Creation of long-lived branches requires team lead approval

2. **Branch Maintenance**:
   - Feature/bugfix branches must be rebased on develop daily
   - Branches must not exist for more than 1 sprint/iteration without approval
   - Branch owners are responsible for keeping their branches current
   - Stale branches (inactive > 30 days) must be archived or deleted

3. **Branch Protection**:
   - Protected branches must enforce status checks
   - Protected branches must require at least two approved reviews
   - Protected branches must enforce signed commits
   - Force pushes must be disabled on all branches

## Pull/Merge Request Process

### PR/MR Creation

1. **Title and Description**:
   - Title must match the Conventional Commits format
   - Description must follow the project template
   - Description must include comprehensive testing instructions
   - Description must link to relevant issues, documents, and designs

2. **Content Requirements**:
   - PRs must address a single concern
   - PRs must include all necessary tests
   - PRs must include updated documentation
   - PR size should not exceed 400 changed lines (excluding tests/docs)

3. **Draft PRs**:
   - Work-in-progress PRs must use the Draft/WIP feature
   - Draft PRs should be used for early feedback
   - Draft PRs must clearly indicate completion criteria
   - Draft PRs should not remain open for more than 5 working days

### Code Review Requirements

1. **Review Process**:
   - At least two approving reviews required for all changes
   - Domain expert review required for specialized areas
   - Security review required for security-sensitive code
   - Performance review required for critical paths

2. **Review Scope**:
   - Functionality: Complete verification against requirements
   - Code quality: Adherence to all standards
   - Test coverage: Verification of test completeness
   - Security: Check for vulnerabilities
   - Performance: Evaluation of efficiency
   - Documentation: Completeness and accuracy check

3. **Addressing Feedback**:
   - All review comments must be addressed
   - Resolutions must be either implemented or explicitly justified
   - Significant changes after review require re-review
   - Review resolution must be documented

### Merge Requirements

1. **Pre-Merge Checks**:
   - All CI checks must pass
   - All required reviews must be approved
   - Code coverage must not decrease
   - Performance must not degrade
   - Security scans must pass

2. **Merge Strategy**:
   - Feature and bugfix branches must be squashed when merged
   - Release and hotfix branches must use merge commits
   - Merge messages must follow Conventional Commits format
   - Merge commits must include the PR number

3. **Post-Merge Actions**:
   - Branch must be deleted after successful merge
   - Associated issues must be updated/closed
   - Dependent branches must be rebased
   - Deployment must be monitored

## Release Management

### Version Numbering

1. **Semantic Versioning**:
   - Strict adherence to Semantic Versioning 2.0.0
   - MAJOR: Incompatible API changes
   - MINOR: Backward-compatible functionality
   - PATCH: Backward-compatible bug fixes
   - Pre-release: Alpha, beta, rc suffixes with incremental numbers

2. **Version Incrementation**:
   - Version changes must be explicitly approved
   - MAJOR version changes require architectural review
   - Version updates must be documented in CHANGELOG.md
   - All versions must be permanently tagged

### Release Process

1. **Release Preparation**:
   - Release branch must be created from develop
   - Release candidate must undergo full QA cycle
   - Release notes must be comprehensive
   - Pre-release checklist must be completed

2. **Release Approval**:
   - Release must be approved by product owner
   - Release must be approved by technical lead
   - Release must be approved by QA lead
   - Approval must be documented

3. **Release Execution**:
   - Release deployment must follow the release plan
   - Release tags must be GPG-signed
   - Release artifacts must be permanently archived
   - Release announcement must be distributed

### Post-Release

1. **Monitoring**:
   - Production deployment must be monitored for 24 hours
   - Key metrics must be compared to baseline
   - User feedback must be collected and triaged
   - Regression plan must be ready if needed

2. **Documentation**:
   - Release retrospective must be conducted
   - Knowledge base must be updated
   - Feedback must be incorporated into future planning
   - Release success metrics must be recorded

## Repository Management

### Repository Configuration

1. **Required Files**:
   - Comprehensive README.md with setup, usage, and contribution guidelines
   - CONTRIBUTING.md with detailed contribution process
   - CHANGELOG.md with complete version history
   - LICENSE with full legal text
   - SECURITY.md with vulnerability reporting process
   - CODE_OF_CONDUCT.md with community standards

2. **Branch Protection**:
   - Protected branches: main/master, develop, release/*
   - Required reviewers: at least 2
   - Required status checks: all CI jobs
   - Signed commits: required
   - Linear history: enforced

### Repository Maintenance

1. **Housekeeping**:
   - Regular maintenance schedule must be established
   - Large binary files must use Git LFS
   - Build artifacts must be excluded via .gitignore
   - Repository size should be monitored

2. **Permissions Management**:
   - Access must follow the principle of least privilege
   - Access review must occur quarterly
   - Access changes must be documented
   - Temporary access must expire automatically

## Compliance and Enforcement

### Automated Verification

1. **Pre-commit Hooks**:
   - Must validate commit message format
   - Must run linters and formatters
   - Must perform basic sanity checks
   - Must be used by all contributors

2. **CI Pipelines**:
   - Must validate branch naming
   - Must enforce commit message standards
   - Must verify signing
   - Must enforce test coverage thresholds

### Auditing

1. **Regular Audits**:
   - Repository compliance must be audited quarterly
   - Audit results must be documented
   - Remediation plans must be created for issues
   - Process improvements must be implemented

2. **Exception Management**:
   - Exceptions must be formally documented
   - Exceptions must have expiration dates
   - Exceptions must be approved by team leads
   - Exceptions must be regularly reviewed

## Example Commit Message

```
feat(auth): implement OAuth2 authentication with role-based permissions

Implement OAuth2 authentication flow with Google and GitHub providers,
including role-based permission system with hierarchical access control.
This implementation uses the authorization code flow for better security
and adds comprehensive logging for security audit purposes.

The new system replaces the legacy Basic Auth implementation and provides
improved security through shorter token lifetimes and refresh token
rotation.

Fixes #123
Related to #456
Co-authored-by: Jane Smith <jane@example.com>
```

## Example Branching Workflow

```
main (v1.0.0, v1.1.0, v1.2.0)
 ↑
 |
 +-- develop
      ↑
      |
      +-- feature/PROJ-123-user-registration
      |    |
      |    +-- commit: "feat(auth): create user registration form"
      |    |
      |    +-- commit: "feat(auth): implement form validation"
      |    |
      |    +-- commit: "feat(auth): connect registration to API"
      |    |
      |    +-- (squash merge to develop)
      |
      +-- "feat(auth): implement user registration (#456)"
      |
      +-- release/v1.3.0
           |
           +-- commit: "chore(release): bump version to 1.3.0"
           |
           +-- commit: "fix(docs): correct API endpoint in README"
           |
           +-- (merge to main AND develop)
