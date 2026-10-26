# Mindcraft

**Open infrastructure for personal cognitive work. Bring your own model and agent harness.**

Mindcraft gives a file-capable AI agent a small architecture and a set of procedures for working with you over time. Use it to recover context, think through priorities, carry work across sessions, and keep decisions and evidence in records you can inspect and change.

The first workflow is simple: agree a plan, do a bounded piece of work, save what happened, and resume in a fresh session.

## Start here

Download this repository using GitHub's **Code → Download ZIP**, then extract it, or clone it:

```sh
git clone https://github.com/Jengkuen/mindcraft.git
```

Give your agent this instruction, replacing both paths:

```text
Read /absolute/path/to/mindcraft/AGENTS.md.
Set up my personal Mindcraft instance at /absolute/path/to/my-mindcraft,
outside the downloaded repository. Start with one real piece of work.
```

The agent needs permission to read the kit and write to the destination. It will check access, create the personal instance, and help you define one useful starting point. You do not need to fill in a life inventory or learn the folder structure first.

- [ChatGPT Work mode: setup and use](docs/chatgpt-work.md)
- [Pi: setup and use](docs/pi.md)
- [Worked example and recovery check](docs/walkthrough.md)

## Use it through conversation

| Say | The agent helps you |
| --- | --- |
| “Help me plan my week.” | Review actual commitments, choose outcomes and agree a realistic plan |
| “I have 45 minutes. Help me get started.” | Recover context and choose a concrete next action with a finish condition |
| “Park this idea: …” | Capture the idea without changing your current plan |
| “Stop here and save where we are.” | Record the result, unfinished work and next action |
| “I'm back. Where were we?” | Recover the latest state from files, even in a new conversation |
| “Show me what changed.” | Explain the saved changes and link to the relevant records |

These are ordinary requests, not commands you have to memorise. Mindcraft supplies procedures; it does not run a background service.

## What is underneath

| Component | Responsibility |
| --- | --- |
| **Bedrock** | Represent your world: context, ideas, experience and understanding in a flexible graph of Markdown documents |
| **Netherite** | Keep the small set of goals, commitments and current work that need reliable visibility easy to navigate |
| **Workspaces** | Hold project execution: plans, working materials, evidence, artifacts and handoffs |

The agent maintains these structures during normal use. You should be able to inspect them without having to manage the filing yourself. You still own the substantive decisions: what matters, what to commit to, and when a direction should change.

See [the architecture](architecture.md) for the structure, [design rationale and evidence](docs/design-rationale.md) for hypotheses, research connections and proposed comparisons, and [the agent contract](AGENTS.md) for authority and navigation.

## What is in this repository

- `AGENTS.md`: the portable entry point for an agent.
- `architecture.md`: the design and a minimal record contract.
- `skills/`: setup, strategy, and operations procedures in the Agent Skills format.
- `starter/`: blank personal records, with no pre-approved projects or goals.
- `docs/`: setup guides and one worked example.

Setup creates a self-contained personal copy of this kit without its Git history, then places the starter's three state directories at that copy's root. Keep that instance separate from this public repository. Its personal records are yours; using Mindcraft does not require publishing them.

## Current status

This is an experimental reference kit extracted from a personally used system. The underlying approach has been iterated through personal use. This public starter's usefulness for other people, its effect on cognitive effort, and its reliability across models remain to be established.

Initial checks on 26 October 2026 covered local links, skill metadata, native skill loading in Pi 1.2.0, and agent-led setup followed by recovery in a fresh agent session using a disposable fictional instance. Full interactive testing in the ChatGPT and Pi interfaces remains outstanding.

The [dated check record](docs/evidence/2026-10-26-smoke-check.md) preserves the scenario, recovery response and limitations. These checks establish a working example, not a measured cognitive benefit or superiority over simpler approaches.

It requires an agent that can follow linked instructions and read and write files. Native skill support is optional. A chat that can only read a repository link cannot maintain a durable instance. Different models and harnesses may follow the procedures differently; use the recovery check before relying on them.

Markdown provides inspectability and portability, not automatic privacy, backup or reliable memory. Your chosen agent and model provider determine where content is processed. Back up your personal instance independently; avoid editing it from two agents at once.

## Contribute

Try the worked example, then use Mindcraft for one real workflow. Issues or pull requests describing a concrete failure, expected behaviour and a small reproducible example are useful. Use fictional or deliberately redacted records when sharing examples.

## License

[MIT](LICENSE).
