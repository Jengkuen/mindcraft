# The Mindcraft architecture

Mindcraft separates two needs: faithfully representing a complicated personal world, and keeping that world navigable enough to act within it. Project execution has its own substrate so neither cognitive layer becomes a project repository.

For the motivation, research connections, trade-offs and evaluation proposals behind these choices, see [Design rationale and evidence](docs/design-rationale.md). This file remains the operational reference; the rationale is optional background.

## Bedrock: representation

Keep context, experience, understanding, questions and ideas in a flat graph of Markdown documents and links under `bedrock/`. The world can be dense, uneven and incomplete. Its representation need not be globally tidy.

Use meaningful filenames and links. Split or consolidate when doing so improves understanding or retrieval. A subject earns a Netherite entry only when reliable rediscovery, monitoring or action matters. Context alone creates no commitment.

## Netherite: orientation

Keep `netherite/` deliberately small and current. Connect identity to goals, goals to projects, projects to workstreams and workstreams to current tasks. Leave missing links unknown rather than manufacturing a grand purpose for every task.

- `README.md`: the entry point and complete registry of tracked projects, with links and current status.
- `goals.md`: only goals the user has adopted; link to grounding in Bedrock where useful.
- `current-week.md`: the current plan, approval status, saved review position and latest handoff pointer.
- `ingest.md`: ideas and proposed changes awaiting review, not active tasks.
- `projects/<project>.md`: one operating view per tracked execution project, created when needed.

Record a project's desired outcome, status, relevant deadline, Bedrock context and workspace link. Under `## Workstreams`, use a heading per workstream and a nested `#### Tasks` section for the current management tasks. Link each workstream to its workspace control. Those controls own detailed plans and evidence.

Use explicit states such as proposed, active, waiting, paused and closed, with a date and basis when they change. A file's existence proves no approval. Before claiming to have reviewed all tracked workstreams/tasks, follow every project in the registry and inspect those sections. This does not constitute reviewing every atomic workspace task.

## Workspaces: execution

Keep plans, implementation details, working materials, source repositories, outputs and handoffs under `workspaces/<project>/`, or link to an existing external workspace. Workspaces are not a third cognitive layer.

Each execution workspace needs a README linking to its Netherite project and controls for its active workstreams. Each control defines:

- Objective and approval boundary, including any named checkpoints.
- Current state and supporting evidence.
- Next action and next checkpoint.
- Exit condition, known dependencies and latest handoff.

Use a single control for a small workstream; split it only when useful. Handoffs record date, actual result, evidence, unfinished work and the next concrete action with a finish condition. Record elapsed time only when known. Evidence in a workspace can prompt a commitment review; it cannot silently rewrite a commitment.

## The first workflow

Strategy reviews actual commitments and capacity, then agrees bounded outcomes. Operations recovers the plan and evidence, supports one action, saves the outcome and leaves a handoff. The ingest queue holds ideas without interrupting that flow. Work updates understanding; changed understanding may prompt deliberate strategy review.

The agent carries the sequence and records. The user owns substantive decisions and can override the process. The [agent contract](AGENTS.md) defines authority; each skill implements its part of the loop. Strategy/operations are conversational procedures, independent of a harness's own “plan” or “build” modes.

## Inspectable underneath, quiet during use

Show choices, evidence, uncertainty and progress in the user's language. Do not require them to select a folder for every thought or remember where a planning review stopped. Offer the records when they want to inspect or change the system.

Keep one canonical source for each kind of information. Bedrock holds meaning and wider context; Netherite holds commitment state; workspace controls hold execution detail. Weekly records point to outcomes rather than duplicating complete task histories.

## Portability and limits

The kit uses ordinary Markdown, relative links and small `SKILL.md` procedures. No database, embeddings, custom runtime, Obsidian installation or model-specific API is required. Native skill loading is optional; direct reading is the baseline.

Model independence is a design goal, not a reliability claim. File access, instruction following, context selection and actual write verification remain necessary. Saved files do not guarantee a model will retrieve the right information. Instruction boundaries need to be tested and remain subject to harness permissions.

The personal instance contains a snapshot of the kit and separate live state directories at its root. To update the kit, compare changes to instructions, skills and guides deliberately; never replace live `bedrock/`, `netherite/` or `workspaces/` with starter templates. Keep personal data out of public contribution commits.
