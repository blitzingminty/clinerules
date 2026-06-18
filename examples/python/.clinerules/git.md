# Python Git Rules (Standard)

## Purpose

These rules define a professional Git workflow for collaborative Python development.

## Commit message standard

- Follow Conventional Commits for every commit.
- Use types such as `feat`, `fix`, `docs`, `refactor`, `test`, `ci`, and `chore`.
- Keep the summary line imperative and concise.
- Add context in the body when behavior or design changes are not obvious.

## Branch workflow

- Do not commit directly to `main`.
- Create branches from `main` using:
  - `feature/<issue-id>-<short-description>`
  - `fix/<issue-id>-<short-description>`
  - `docs/<issue-id>-<short-description>`
- Keep each branch scoped to one issue or cohesive unit of work.
- Open a pull request for review before merging.

## Issue linking

- Link related issues in commits and pull requests.
- Use closing keywords in pull requests when appropriate, such as `Closes #123`.
- Use `Refs #123` when work is related but does not fully close the issue.

## Merge quality gate

- Require passing CI checks before merge.
- Require at least one approval before merge.
- Squash merge by default to keep history concise.
