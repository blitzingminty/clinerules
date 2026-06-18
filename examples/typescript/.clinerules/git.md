# TypeScript Git Rules (Standard)

## Purpose

These rules define a professional Git workflow for collaborative TypeScript development.

## Commit message standard

- Follow Conventional Commits for every commit.
- Use types such as `feat`, `fix`, `docs`, `refactor`, `test`, `build`, `ci`, and `chore`.
- Keep the subject line imperative and concise.
- Include a body when behavior, migration, or design context is needed.

## Branch workflow

- Do not push directly to `main`.
- Create branches from `main` using:
  - `feature/<issue-id>-<short-description>`
  - `fix/<issue-id>-<short-description>`
  - `docs/<issue-id>-<short-description>`
- Keep branch scope limited to one feature or fix.
- Open a pull request and complete review before merge.

## Issue linking

- Reference related issues in commit footers and pull request descriptions.
- Use `Closes #123` when the change resolves the issue.
- Use `Refs #123` for partial or related work.

## Merge quality gate

- Require passing CI checks before merge.
- Require at least one approval before merge.
- Prefer squash merge to keep history readable.
