# Contributing to This Project

First off, thank you for taking the time to contribute to this project! 🎉

## Table of Contents

- [Getting Started](#getting-started)
- [Branching Strategy](#branching-strategy)
- [Commit Conventions](#commit-conventions)
- [Code Review Process](#code-review-process)
- [Testing Requirements](#testing-requirements)
- [Guidelines](#guidelines)
- [Reporting Issues](#reporting-issues)

---

## Getting Started

1. Fork the repository.
2. Clone your fork locally: `git clone https://github.com/<your-username>/<repo>.git`
3. Create a new branch for your contribution (see [Branching Strategy](#branching-strategy)).
4. Make your changes and ensure tests are included and passing.
5. Submit a pull request detailing what you changed and why.

---

## Branching Strategy

- `main` — stable, production-ready code. Direct commits are not allowed.
- `feature/<name>` — for new features or enhancements.
- `bugfix/<name>` — for bug fixes.
- `hotfix/<name>` — for urgent production fixes.
- `docs/<name>` — for documentation updates only.
- `chore/<name>` — for maintenance tasks (dependency updates, refactors, etc.).

Always branch off from `main` unless otherwise instructed.

---

## Commit Conventions

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>(<scope>): <short description>
```

### Types

| Type       | Description                                      |
|------------|--------------------------------------------------|
| `feat`     | A new feature                                    |
| `fix`      | A bug fix                                        |
| `docs`     | Documentation changes only                      |
| `style`    | Formatting, missing semicolons, etc.            |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `test`     | Adding or updating tests                         |
| `chore`    | Build process or auxiliary tool changes          |

### Examples

```
feat(auth): add OAuth2 login support
fix(api): handle null response from user endpoint
docs(readme): update installation instructions
```

- Keep the subject line under 72 characters.
- Use the imperative mood: "add feature" not "added feature".
- Reference related issues in the commit body: `Closes #42`.

---

## Code Review Process

1. All pull requests require at least **one approval** before merging.
2. Copilot code review is encouraged — check the **Copilot reviewed** checkbox in the PR template.
3. Address all review comments before requesting a re-review.
4. Do not force-push to a branch under active review.
5. Squash commits before merging to keep history clean.

---

## Testing Requirements

- All new features must include relevant unit tests.
- Bug fixes should include a regression test.
- Ensure all existing tests pass before submitting a PR: `npm test` / `pytest` / equivalent.
- Aim for a minimum of **80% code coverage** on new code.
- Integration tests should be added for any new API endpoints or services.

---

## Guidelines

- Keep commits descriptively short.
- Open issues to discuss major proposed features before starting work.
- Follow existing code styles and patterns.
- Avoid introducing unnecessary dependencies.
- Keep pull requests focused — one feature or fix per PR.
- Update documentation alongside code changes.

---

## Reporting Issues

- Search existing issues before opening a new one.
- Use the provided issue templates (Bug Report / Feature Request).
- Provide as much context as possible, including steps to reproduce.
- Label issues appropriately (`bug`, `enhancement`, `question`, etc.).
