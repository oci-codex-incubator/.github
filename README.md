# OCI Codex Incubator

Reusable Codex skills and project standards for applications that use Oracle Cloud Infrastructure. Start with a plan, build and verify the application, then contribute useful improvements or projects.

## Common prompts

The **[prompt guide](docs/prompts.md)** contains copyable requests for the everyday workflows:

| Task | Start here |
| --- | --- |
| Create a Python or Node.js app | [Plan](docs/prompts.md#plan-an-application), then [build](docs/prompts.md#create-an-application) |
| Standardize an existing app | [Update an application](docs/prompts.md#update-an-existing-application) |
| Update my environment files based on code changes | [Regenerate and sync environment files](docs/prompts.md#update-environment-files) |
| Set me up for Container deployment to OCI | [Prepare OCI Container Instances deployment](docs/prompts.md#set-up-container-deployment) |
| Create a tested reference app | [Python and Node.js reference-app prompts](docs/reference-app-prompts.md) |
| Contribute a change or a new project | **[Contribution process](CONTRIBUTING.md)** |

Run application prompts inside the application repository with its language skill installed. Container setup prepares scripts and documentation; actual cloud operations follow the generated application's run guide. Reference apps belong in separate repositories.

## Project skills

- [OCI Python Project Standard](https://github.com/oci-codex-incubator/oci-python-project-skill): CLI, Streamlit, Flask, and FastAPI + JavaScript.
- [OCI Node.js Project Standard](https://github.com/oci-codex-incubator/oci-node-project-skill): CLI, service, web, and Electron.

See the [organization profile](profile/README.md) for installation and getting started, the [planning guide](docs/project-planning.md) for choosing a project shape, and the [project catalog and roadmap](docs/projects.md) for maturity and next contributions.

## Contributing

The separate **[CONTRIBUTING.md](CONTRIBUTING.md)** explains branches/forks and PRs, verification, new-project admission, and personal-to-organization repository handoff. Reference applications follow the same process. Read the [security policy](SECURITY.md) for private reporting and [licensing guidance](docs/licensing.md) before distributing or transferring a project.
