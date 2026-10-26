---
name: mindcraft-setup
description: Set up or recover a personal Mindcraft instance for a file-capable agent. Use for first setup, onboarding, choosing an instance folder, or repairing a partial setup. Keep the public kit separate from personal records and start with one useful workflow.
---

# Set up Mindcraft

## Establish access and destination

Resolve the kit root from this skill's location: two directories above this file's parent. Read its `AGENTS.md` and `architecture.md`. If invoked inside an existing personal instance, use its live records; do not initialise it again unless explicitly asked.

Use a separate destination outside the public kit. Honour a path already supplied by the user. Otherwise propose a sibling named `my-mindcraft` and ask for the location only if the choice cannot be resolved safely. Inspect an existing destination before writing. Never overwrite an existing instance, unrelated files or a Git repository with blank templates.

Verify that the agent can read the kit and write to the destination using a small temporary probe, then remove the probe. If access is unavailable, report the precise gap and show the relevant setup guide. Do not claim persistence based on a chat response or repository link alone.

## Create a self-contained instance

For a new empty destination:

1. Copy the kit's `README.md`, `AGENTS.md`, `architecture.md`, `LICENSE`, `skills/`, `starter/` and `docs/` into it. These are readable procedures and templates, not live state. Do not copy `.git/`, local harness configuration, credentials or transcripts.
2. Copy the contents of `starter/` into the instance root. This creates live `bedrock/`, `netherite/` and `workspaces/`. Keep `starter/` itself blank as a reference.
3. Verify the entry point, all three state directories and the skill paths. Resolve subsequent paths against the new instance, even if the shell is still in the kit.
4. Do not initialise a remote, publish the instance or install global skills. Use the files directly. Copy the kit's `.gitignore` only if useful; it is an extra guard for the public kit, not a backup policy for personal records.

For a partially existing destination, inspect each item, preserve user data, and restore only missing infrastructure needed to proceed. If conflicting records require a substantive decision, explain the conflict instead of choosing silently. An existing personal system may be linked and adapted; do not migrate its history wholesale without scope from the user.

## Start with one real piece of work

Ask only what is missing to support the user's current request: what outcome they want, any real deadline, and what they can reasonably give it. Ask for timezone only when needed for dated planning or clock times; do not use the host timezone as a proxy.

Record known constraints in the appropriate place. Leave unknowns unknown. Do not require filling `bedrock/identity.md`, adopting a long-term goal or revealing sensitive background before useful work can start.

Use the strategy procedure at `../mindcraft-strategy/SKILL.md` to propose a bounded project/workstream if needed. An explicit user instruction may already approve its scope; otherwise obtain the substantive decision before marking it active. Draft files and an approved weekly plan are different states.

## Finish setup

Save the agreed starting state, next action and unresolved review position in the personal instance. Verify reads after writes. Tell the user where the instance lives and how to return: start a fresh session, read its `AGENTS.md`, and recover the plan and stopping point from files.

Distinguish completed file setup from untested workflow reliability. Do not report the fresh-session recovery check as passed until it has actually been performed.
