# Contributing to OCI Codex Incubator

Start with the [project catalog and roadmap](https://github.com/oci-codex-incubator/.github/blob/main/docs/projects.md). Documentation, reproducible bug reports, tests, and focused fixes are useful contributions. For new projects, follow the [planning guide](https://github.com/oci-codex-incubator/.github/blob/main/docs/project-planning.md) and the appropriate language skill.

## Choose the contribution path

- **Improve an existing repository:** work in a branch or fork, run its verification, push your branch, and open a focused pull request for maintainers to review.
- **Introduce a new application:** build and verify it in a personal repository, then follow [the new-project handoff](#contribute-a-new-application) with an organization owner. A reference application uses this same process.

See the [common prompts](https://github.com/oci-codex-incubator/.github/blob/main/docs/prompts.md#contribute) for a contribution-preparation prompt. Documentation and test improvements count as contributions too.

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

For a new application, follow the project handoff process below after agreeing on its name, visibility, maintainer, license, and verification status with an organization owner.

See [licensing guidance](https://github.com/oci-codex-incubator/.github/blob/main/docs/licensing.md) before adding a license or third-party assets. Report vulnerabilities using the [security policy](https://github.com/oci-codex-incubator/.github/blob/main/SECURITY.md), rather than a public issue. Treat contributors respectfully, give actionable feedback, and avoid sharing private information.

## Contribute a new application

### 1. Build in your own GitHub account

Create and own the repository in your personal GitHub account while you are developing it. Run the project locally, verify its behavior, and make the initial history before asking the organization to take ownership:

Before the initial commit, run setup, tests, lint/build, environment validation, and the application's structural checker (`check_project.py` for Python or `check-project.mjs` for Node.js). Review the files to be staged so local OCI configuration, private keys, tokens, populated `.env` files, and generated artifacts are excluded. Create an empty personal repository on GitHub for the remote URL below, then commit and push the verified work:

```bash
git init
git add .
git commit -m "Initial project"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/my-oci-project.git
git push -u origin main
```


### 2. Move the repository into the organization

When the project is ready for shared ownership, ask an organization owner to review it and confirm the intended repository name, visibility, maintainers, and any required license or contribution files. Then choose one of these paths:

**Transfer the repository** — use this when the organization should become the repository's owner while preserving its full Git history, issues, releases, and pull requests. In the personal repository, open **Settings** → **General** → **Danger Zone** → **Transfer**, enter `oci-codex-incubator` as the new owner, and confirm the repository name. You need administrator access to the personal repository and permission to create repositories in the organization. GitHub keeps the original owner as a collaborator; organization policies apply after the transfer. See GitHub's [repository-transfer requirements and steps](https://docs.github.com/en/repositories/creating-and-managing-repositories/transferring-a-repository).

**Push to a new organization repository** — use this when an organization maintainer creates an empty destination repository first. Preserve the personal remote, add the organization remote, and push the reviewed branch after you have been granted write access:

```bash
git remote rename origin personal
git remote add origin git@github.com:oci-codex-incubator/my-oci-project.git
git push -u origin main
```

If you do not have the necessary organization permission, do not attempt the transfer or push. Send the personal repository URL to an organization owner and ask them to create the destination repository or approve the transfer.
