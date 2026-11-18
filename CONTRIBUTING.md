# Contributing to OCI Codex Incubator

Start with the [project catalog and roadmap](https://github.com/oci-codex-incubator/.github/blob/main/docs/projects.md). Documentation, reproducible bug reports, tests, and focused fixes are useful contributions. For new projects, follow the [planning guide](https://github.com/oci-codex-incubator/.github/blob/main/docs/project-planning.md) and the appropriate language skill.

## Propose and implement a change

For a substantial feature or a new project, open an issue describing the user, problem, smallest useful outcome, and acceptance checks. For a small fix, a focused pull request with that context is enough. Check existing issues before opening another. Maintainers and organization owners decide repository admission and ownership; no specific review time is promised.

Work in a branch or personal fork. Keep changes scoped, preserve existing public behavior, and update affected documentation. AI-assisted contributions are welcome; contributors are responsible for understanding the changes, checking generated code and dependencies, and describing verification honestly. Follow project-local AGENTS.md instructions.

## Verify before a pull request

For the skill repositories, run from the repository root:

| Repository | Checker regressions | Full starter verification |
| --- | --- | --- |
| oci-python-project-skill | `python3 -m unittest discover -s tests -v` | `python3 scripts/verify_templates.py` |
| oci-node-project-skill | `node --test tests/*.test.mjs` | `node scripts/verify-templates.mjs` (Node 24) |

Starter verification needs package-registry access, uses temporary projects, and needs no OCI credentials. Python also needs uv and Python 3.12; CI covers 3.12 and 3.13. Generated applications run their own documented tests/lint/build and the appropriate structural checker. Run shell syntax checks for changed run scripts. For documentation changes, verify links and command examples. Explain any check you could not run; do not describe mocked tests as live OCI validation.

Never commit OCI config, private keys, tokens, complete PAR URLs, populated environment files, customer data, or generated dependency/build directories. Use synthetic fixtures and keep cloud integration tests opt-in. Obtain the project owner's agreement on cloud resources and costs before live tests or deployments.

## Submit for review

Describe the problem, resulting behavior, checks run, and any compatibility or operational impact. Include screenshots when the change affects a UI. A maintainer reviews and merges; repository access and branch protection are managed separately by organization owners.

Before transferring a new repository, agree on its name, visibility, maintainer, license, and verification status with an organization owner. Follow the [handoff instructions](https://github.com/oci-codex-incubator/.github/blob/main/profile/README.md#contribute).

See [licensing guidance](https://github.com/oci-codex-incubator/.github/blob/main/docs/licensing.md) before adding a license or third-party assets. Report vulnerabilities using the [security policy](https://github.com/oci-codex-incubator/.github/blob/main/SECURITY.md), rather than a public issue. Treat contributors respectfully, give actionable feedback, and avoid sharing private information.
