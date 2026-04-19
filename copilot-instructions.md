# GitHub Copilot Instructions

## Repository Purpose

This repository serves as a collaborative space for developers to contribute to the project's goals. The purpose of this repository is to facilitate high-quality, maintainable, and scalable software development.

## What to Work On

- Prioritize issues labeled `help wanted` or `good first issue`.
- Focus on features that align with the project roadmap.
- Fix bugs that are reproducible and have detailed reports.
- Optimize performance for critical bottlenecks.
- Maintain and improve documentation for better clarity.

## Style and Goals

- **Readability:** Write code that is easy to read and understand for others.
- **Consistency:** Follow the existing coding style and adhere to established patterns.
- **Testability:** Ensure all code is covered by unit tests where applicable.
- **Simplicity:** Avoid overengineering and write solutions that are as simple as possible.
- **Documentation:** Comment code to explain complex logic and update relevant documentation.
- **Security:** Never commit secrets or credentials; validate user inputs; prefer least-privilege designs.

## Best Practices for Copilot Assistance

- **Context Matters:** Ensure your code suggestions are relevant to the context of the repository.
- **Iterate Collaboratively:** Use Copilot-generated code as a starting point and refine it as needed.
- **Review Generated Code:** Assess Copilot's suggestions critically to ensure they meet quality standards.
- **Avoid Overreliance:** Leverage Copilot responsibly and only for tasks that suit its capabilities.
- **Use Proper Inputs:** Provide clear and descriptive prompts to Copilot for generating precise suggestions.
- **Security Review:** Always review generated code for potential security issues before committing.

## Development Best Practices

- Follow [Conventional Commits](https://www.conventionalcommits.org/) for all commit messages.
- Ensure all pull requests pass CI checks defined in `.github/workflows/ci.yml` before merging.
- Write or update tests for every functional change.
- Do not introduce new dependencies without evaluating their security posture and license compatibility.
- Keep pull requests focused and small — one concern per PR.
- Respect the branching strategy defined in [CONTRIBUTING.md](CONTRIBUTING.md).

## Notes

- Make use of the `.github/workflows/ci.yml` file for continuous integration guidance.
- Check for code style and linting requirements before creating pull requests.
- Reference any template files for creating issues and pull requests to align with repository standards.

## Additional Resources

- **Code of Conduct:** [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)
- **Contributing Guide:** [CONTRIBUTING.md](CONTRIBUTING.md)
- **Security Policy:** [SECURITY.md](SECURITY.md)
- **Pull Request Template:** [pull_request_template.md](pull_request_template.md)
- **CI/CD Pipeline:** [.github/workflows/ci.yml](.github/workflows/ci.yml)
