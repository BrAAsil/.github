# Contributing to BrAAsil

Thank you for your interest in contributing! This guide covers the workflow and conventions used across all BrAAsil repositories.

## Getting Started

1. **Fork** the repository (or create a branch if you have write access)
2. **Clone** your fork locally
3. **Install** [go-task](https://taskfile.dev/installation/) — our universal task runner
4. **Run** `task quality` to verify everything works before making changes

## Conventional Commits

All commits **must** follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. This is enforced on every commit in a PR, not just the PR title.

### Format

```
type(scope): description

[optional body]

[optional footer(s)]
```

### Allowed Types

| Type | Description |
|------|-------------|
| `feat` | A new feature |
| `fix` | A bug fix |
| `chore` | Maintenance tasks |
| `docs` | Documentation changes |
| `refactor` | Code refactoring (no feature or fix) |
| `test` | Adding or updating tests |
| `ci` | CI/CD changes |
| `build` | Build system or dependency changes |
| `perf` | Performance improvements |
| `style` | Code style changes (formatting, etc.) |

### Examples

```
feat(auth): add OAuth2 login flow
fix: resolve null reference in player sync
chore(deps): update NuGet packages
docs: add API endpoint documentation
refactor(database): extract connection pooling logic
test(inventory): add edge case tests for item stacking
ci: add security scanning workflow
```

### Breaking Changes

Append `!` after the type/scope for breaking changes:

```
feat(api)!: change authentication endpoint response format
```

## Merge Strategy

We use **rebase merge only** to maintain a linear commit history. This means:

- Every commit on `main` is meaningful and follows conventional commit format
- No merge commits
- Your branch must be rebased on top of the latest `main` before merging

## Pull Request Guidelines

1. **Create a descriptive PR** — explain what changed and why
2. **Link related issues** — use `Closes #123` or `Fixes #456`
3. **Run quality checks** — execute `task quality` locally before pushing
4. **Keep PRs focused** — one logical change per PR
5. **Respond to reviews** — address all review comments before requesting re-review

## Task Runner

Every BrAAsil repo uses [go-task](https://taskfile.dev/) with a `Taskfile.yml`. The standard tasks are:

| Task | Description |
|------|-------------|
| `task quality` | Run all quality checks (CI entrypoint) |
| `task build` | Build the project |
| `task test` | Run tests |
| `task format` | Format code |
| `task format-check` | Check formatting without modifying |
| `task lint` | Run linter |
| `task clean` | Clean build outputs |

Run `task --list` in any repo to see all available tasks.

## Code Review

- All PRs require at least 1 approval from `@braasil/leads`
- Stale reviews are dismissed on new pushes
- All conversations must be resolved before merging
- CI checks must pass (quality + security)

## Standards

Our reusable workflows, composite actions, and org-wide standards live in [braasil-standards](https://github.com/braasil/braasil-standards). Refer to that repo for details on CI pipelines, security scanning, and release automation.
