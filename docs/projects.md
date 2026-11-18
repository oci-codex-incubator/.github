# Project catalog and roadmap

This catalog covers the three repositories maintained together in this workspace; it is not an inventory of every organization repository. All three are incubating. Repository-specific maintainers have not been assigned in this catalog; organization owners coordinate admission and reviewer assignment until each repository names a maintainer.

| Project | Purpose | Maturity and verification | Next useful contribution |
| --- | --- | --- | --- |
| [Organization .github](https://github.com/oci-codex-incubator/.github) | Planning, onboarding, contribution defaults, and this catalog | Incubating documentation; review links and examples | Name project maintainers and resolve per-repository licenses |
| [Python project skill](https://github.com/oci-codex-incubator/oci-python-project-skill) | CLI, Streamlit, Flask, and FastAPI + JavaScript starters | Starter CI defined for Python 3.12/3.13; no live OCI deployment certification | Generate and independently test a reference app using the prompt below |
| [Node.js project skill](https://github.com/oci-codex-incubator/oci-node-project-skill) | CLI, service, web, and Electron starters | Starter CI defined for Node 24; Electron checks compile/policy, not desktop execution | Generate a reference app, then add desktop launch verification on a suitable runner |

Workflow definitions do not imply that a hosted run has passed. Inspect each repository's Actions results for its actual default-branch status.

## Near-term work

1. Run the new workflows on GitHub and require the selected checks through repository settings where appropriate.
2. Use the [reference-application prompts](reference-app-prompts.md) to create, test, review, and commit one independent example per language. Link the repositories here only once they exist; record the skill revision and verification evidence.
3. Have organization owners assign maintainers, choose approved licenses, and confirm a private vulnerability-reporting path for each repository.
4. Validate a container deployment in a designated OCI test environment, recording rollout, rollback, IAM, networking, and cleanup evidence without credentials or real resource identifiers.

## Environment maintenance

Both language skills include a source-review workflow for synchronizing configuration after code or requirement changes. It keeps active local values, removes proven-defunct inputs from the example while preserving their local values as inactive DEFUNCT comments, retains uncertain indirect consumers, and requires read-only validation before local/build/deploy operations. The skill's structural checker is not a source scanner or proof of configuration validity.

## Scope and compatibility

Both skills maintain local and OCI Container Instances workflows with one shared `run/.env`, `RUN_ENV_FILE` overrides, and `build-push-image.sh` / `deploy-container-instance.sh` when containers are selected. Load Balancer ownership is explicit and optional. Existing Node adopters using the older script names or a separate container env file need to migrate deliberately; preserve their working interfaces until the project owner accepts that change.

The checkers recognize legacy `function` and `oci-devops` manifest values for compatibility. Neither has a maintained starter or verified deployment path here. Add one only when a concrete project justifies its documentation and test coverage. Additional frameworks follow the same rule.

## Propose a project

Describe its users, repeated problem, smallest useful operation, OCI services, intended maintainer, and verification plan in a feature request. Link its plan and clarify whether it is an experiment, a reusable skill, or an application. Follow the [contribution guide](../CONTRIBUTING.md) for admission and handoff.

## Repository administration

The community defaults in this `.github` repository apply on GitHub only when it is public and the target repository has no corresponding override; they are not copied into clones. See [GitHub's default community-file rules](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file). Licensing is a separate per-repository decision.

Adding workflow and policy files does not configure branch protection, enable private vulnerability reporting, grant access, or appoint maintainers. Organization owners should review those settings after the commits are published.
