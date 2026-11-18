# OCI Codex Incubator

This organization is a place to build, share, and contribute OCI projects with Codex. Start new OCI-backed Python or Node.js projects with our standard skills, then bring your improvements back to the community.


## Common prompts

| Task | Prompt or guide |
| --- | --- |
| Create an application | [Plan, then build](../docs/prompts.md#plan-an-application) |
| Update an existing application | [Apply the standard](../docs/prompts.md#update-an-existing-application) |
| “Update my environment files based on code changes” | [Environment sync prompt](../docs/prompts.md#update-environment-files) |
| “Set me up for Container deployment to OCI” | [Container setup prompt](../docs/prompts.md#set-up-container-deployment) |
| Create a reference app | [Python and Node.js reference prompts](../docs/reference-app-prompts.md) |
| Contribute | **[Contribution process](../CONTRIBUTING.md)** and [preparation prompt](../docs/prompts.md#contribute) |

The [prompt guide](../docs/prompts.md) contains copyable requests and explains where to run them. Use application prompts in the application repository, with the appropriate skill installed.

## Projects and contribution

See the [project catalog and roadmap](../docs/projects.md) for supported projects, maturity, ownership, and next contributions. Read the [contribution guide](../CONTRIBUTING.md), [security policy](../SECURITY.md), and [licensing guidance](../docs/licensing.md). After planning a regular application, you can also use the [Python and Node.js reference-application prompts](../docs/reference-app-prompts.md) to generate independent examples with verification evidence.

## Start an OCI Python project

Clone the [OCI Python Project Standard](https://github.com/oci-codex-incubator/oci-python-project-skill) and link the included skill into Codex:

```bash
git clone https://github.com/oci-codex-incubator/oci-python-project-skill.git
cd oci-python-project-skill
mkdir -p ~/.codex/skills
ln -s "$PWD/skills/oci-python-project" ~/.codex/skills/oci-python-project
```

The symbolic link keeps your local skill current when you pull updates in the cloned repository. If `~/.codex/skills/oci-python-project` already exists, inspect and update that installation instead of overwriting it.

Open a new Codex task after installing the skill, then create an empty repository for your project:

```bash
mkdir my-oci-project
cd my-oci-project
git init
codex
```

The Python skill guides implementation choices and includes documentation and a structural checker. Before considering a project complete, run its `uv` setup, tests, linting, and the included `check_project.py` checker. For OCI Container Instances, it generates a shared `run/.env` and separate image build/push and deployment scripts, with network and Load Balancer ownership documented for the project. Start with the planning workflow below so the skill has a clear, reviewed context file to follow.

## Start an OCI Node.js project

Clone the [OCI Node.js Project Standard](https://github.com/oci-codex-incubator/oci-node-project-skill), then link the included skill into Codex:

```bash
git clone https://github.com/oci-codex-incubator/oci-node-project-skill.git
cd oci-node-project-skill
mkdir -p ~/.codex/skills
ln -s "$PWD/skills/oci-node-project" ~/.codex/skills/oci-node-project
```

The symbolic link keeps your local skill current when you pull updates in the cloned repository. If `~/.codex/skills/oci-node-project` already exists, inspect and update that installation instead of overwriting it.

Open a new Codex task after installing the skill, then create an empty repository for your project:

```bash
mkdir my-oci-node-project
cd my-oci-node-project
git init
codex
```

The Node.js skill adds or validates the project contract, operational documentation, `check`, `test`, `build`, and safe `clean` commands, and the included `check-project.mjs` structural checker. For an OCI container deployment, it first requires an explicit deployment plan and scripts that operate only on named, pre-existing OCI network and Load Balancer resources. Start with the planning workflow below so the skill has a clear, reviewed context file to follow.

## Project Planning

Before asking Codex to build, make a short plan with goals, decisions, and context. This gives the project a shared starting point: who it serves, the outcome it should deliver, the chosen presentation and logic shape, OCI boundaries, and the questions that still need an answer.

Read the [project planning guide](../docs/project-planning.md). It explains how to separate presentation, application logic, and OCI integration; compare Python and Node.js options by purpose and team skill set; and create a `PROJECT_PLAN.md` context file. Do not put credentials, private keys, tokens, or real OCI identifiers in that file.

**Start with a planning prompt, not an implementation prompt.**

### For a Python project

> Help me plan an OCI Python project before building it. The goal is to help a team that inventories Object Storage buckets understand what they own and act on stale data. The primary users are cloud operators who work from a terminal during weekly reviews. We need Object Storage access, local config-file authentication for development, and instance-principal authentication after deployment. Create `PROJECT_PLAN.md`, recommend the smallest suitable project shape, list trade-offs and open questions, and do not implement it yet.

### For a Node.js project

> Help me plan an OCI Node.js project before building it. The goal is to help a team safely browse and use Object Storage PAR links. The primary users are support and operations staff who need a desktop workflow and local file selection. The application calls OCI through PAR HTTPS URLs, and the team is strongest in TypeScript. Create `PROJECT_PLAN.md`, recommend the smallest suitable presentation and logic shape, list trade-offs and open questions, and do not implement it yet.


## Codex Execution

When the plan is correct, ask Codex to build from it:

> Read `PROJECT_PLAN.md` and build the project it describes. Apply the `oci-python-project` or `oci-node-project` skill as appropriate. Preserve the plan's decisions and constraints, ask before making a material architecture or OCI deployment change, and document any necessary exception. Regenerate the environment example from current code and mirror its active structure in the real env while preserving local values. Move proven-unused local assignments into one final Defunct values section as inactive comments, and validate configuration before the selected run/build/deploy operation.

When Codex is done, either check the built project's `README.md` or ask it how to run the project.  It is
likely that some setup is required from the terminal, such as Python or Node.js runtimes.  You can ask
Codex how to set those up too if you get stuck.

### Read approval prompts before accepting

Codex asks for approval before actions that can change your computer, repository, cloud resources, or external services. Those prompts are intentional safety checkpoints, not routine buttons to click through.

Before approving, read the proposed command or action and confirm its target, scope, and expected effect. In particular, pause for actions that install software, create or change OCI resources, publish or delete data, modify Git history, or send information outside your computer. If the request is unclear or broader than you expected, decline it and ask Codex to explain or narrow the action first.

## Contribute

Read the separate **[contribution guide](../CONTRIBUTING.md)** for the complete process:

1. Improve an existing project in a branch or fork and submit a focused pull request, or build a new application in your personal repository.
2. Run tests, lint/build, environment validation, and the appropriate structural checker; include verification evidence and review files for local configuration or generated artifacts.
3. For a new project, agree on maintainers, visibility, licensing, and handoff with an organization owner, then transfer or push to the approved organization repository as the guide describes.

Reference applications follow the same process. Use the [contribution-preparation prompt](../docs/prompts.md#contribute) when you want Codex to help get the work ready for review.
