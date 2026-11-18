# Common Codex prompts

Use these in the **application repository**, with the appropriate skill installed. Use `oci-python-project` for Python or `oci-node-project` for TypeScript/Node.js. Retain choices already recorded in PROJECT_PLAN.md and the repository. These prompts are ordinary language requests to Codex, not shell commands.

| I want to… | Start here |
| --- | --- |
| Plan a new app | [Plan an application](#plan-an-application) |
| Build an approved plan | [Create an application](#create-an-application) |
| Standardize an existing app | [Update an existing application](#update-an-existing-application) |
| Refresh configuration after code changes | [Update environment files](#update-environment-files) |
| Prepare OCI Container Instances deployment | [Set up container deployment](#set-up-container-deployment) |
| Generate a tested reference app | [Create a reference application](#create-a-reference-application) |
| Contribute a fix or a new project | [Contribute](#contribute) |

## Plan an application

Create an empty application folder outside the skill repositories, initialize Git, and open it in Codex. Replace the bracketed details:

> Apply the `oci-python-project` or `oci-node-project` skill as appropriate. Help me plan an OCI application for [users] to [outcome], using [OCI services]. The team prefers [Python/TypeScript] and users need [CLI/API/web/desktop]. Create PROJECT_PLAN.md, recommend the smallest suitable format, and record authentication, local/container deployment, resource ownership, trade-offs, open questions, and acceptance checks. Do not implement it yet.

Read and refine the plan before continuing. See the [planning guide](project-planning.md) for format choices and a plan template.

## Create an application

> Read the approved PROJECT_PLAN.md and build the application using the appropriate `oci-python-project` or `oci-node-project` skill. Preserve the plan's scope and interfaces. Generate the standard project structure, tests, documentation, run scripts, lockfile, and structural checker. Derive environment settings and explanations from the implemented code; preserve existing local values and add operation-specific validation. Run the applicable checks, tests, and build, fix failures, and tell me how to perform the first useful local operation. Do not deploy or publish anything.

## Update an existing application

> Apply the appropriate `oci-python-project` or `oci-node-project` skill to this existing OCI application. Inspect its implementation and bring it into the project standard while preserving working public interfaces. Retain established format, authentication, and deployment choices; document necessary exceptions. Synchronize environment configuration from the code and run the relevant checks, tests, and build. Explain what changed and any remaining limitations.

## Update environment files

The short request to remember is **“Update my environment files based on code changes.”** Name the skill explicitly when useful:

> Apply the appropriate `oci-python-project` or `oci-node-project` skill. Update my environment files based on code changes. Review application code, config loaders, run scripts, container definitions, and requirements. Regenerate run/.env.example with supported inputs and concise required/optional/conditional/default explanations. Make the selected ignored local env mirror its active names, ordering, and explanations while preserving my values and intentional optional overrides. Move proven-unused local assignments to one final Defunct values section as inactive comments with their original values preserved; omit them from the example. Keep uncertain indirect consumers for review. Update and test read-only validation for local running, image build/push, and deployment as applicable. Report names and results without showing values.

If using a custom local file, name its path and use RUN_ENV_FILE consistently. Codex performs the source review and sync; ordinary application commands validate configuration without rewriting either env file. A structural checker cannot prove requiredness, SDK behavior, or live resource readiness.

## Set up container deployment

The short request to remember is **“Set me up for Container deployment to OCI.”** The expanded prompt separates preparation from running cloud operations:

> Apply the appropriate `oci-python-project` or `oci-node-project` skill. Set me up for Container deployment to OCI using OCI Container Instances and OCIR. Inspect the existing application and retain its behavior. Establish authentication, region, resource ownership, networking, image-pull access, port, health check, exposure, and whether an existing Load Balancer is needed and who owns its backends. Ask only for unresolved implementation decisions; keep real configuration values in the ignored local env rather than chat or tracked files. Generate the Dockerfile, .dockerignore, run/build-push-image.sh, and run/deploy-container-instance.sh. Keep local/build/deploy inputs in one run/.env and regenerate its example from actual consumers, preserving local values and archiving defunct settings. Validate each operation's own inputs before it runs. Document exact prerequisites, IAM requirements, image tags, rollout, health verification, rollback, and cleanup in run/README.md. Run offline tests and static checks. Prepare the workflow; do not build/push images, deploy, or change OCI resources yet.

After reviewing and configuring the generated project, follow **that application's** run/README.md for the actual commands. The setup prompt does not deploy. Live OCI validation and operations are separate actions; do not treat offline checks as evidence of a successful deployment.

## Create a reference application

Use the [reference-application prompts](reference-app-prompts.md). Each language has a **Plan** prompt and a **Build, test, and commit** prompt:

- [Python: Object Storage inventory CLI](reference-app-prompts.md#python-object-storage-inventory-cli)
- [TypeScript/Node.js: Object Storage inventory service](reference-app-prompts.md#typescript--nodejs-object-storage-inventory-service)

Start in a separate empty application repository after the updated skills are available locally. Review the plan, then build. Both examples provide an offline demo, meaningful tests, verification evidence, and a local commit; they do not push or deploy. Read-only live OCI testing is opt-in. Keep the application out of these skill repositories, then use the contribution process when it is ready for shared ownership.

## Contribute

The separate [contribution guide](../CONTRIBUTING.md) covers improving an existing repository and introducing a new application. A useful preparation prompt is:

> Read this repository's contribution guide and the OCI Codex Incubator contribution process. Help me prepare [this change/this application] for contribution. Verify the applicable tests, lint/build, environment configuration, structural checker, and documentation. Review the proposed committed files for local configuration, credentials, generated artifacts, and unrelated changes. Summarize results and limitations, prepare a focused PR description or a new-project handoff summary, and explain the next Git/GitHub steps. Do not push, open a PR, or transfer ownership yet.

Follow the guide to publish and submit the reviewed work. Organization owners decide repository admission, ownership, permissions, and licensing.
