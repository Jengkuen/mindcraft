# Use Mindcraft through Pi

Pi is an agent harness with file tools and support for Markdown skills. Mindcraft uses those capabilities without adding a custom extension or runtime.

## Setup

1. Install Pi using its [official quickstart](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/quickstart.md). If using npm, the current package is:

   ```sh
   npm install -g --ignore-scripts @earendil-works/pi-coding-agent
   ```

   Check the upstream guide for current Node.js requirements and installation options. Older instructions may use the former `@mariozechner` package name.

2. Download/extract Mindcraft, or clone it:

   ```sh
   git clone https://github.com/Jengkuen/mindcraft.git
   cd mindcraft
   pi
   ```

3. In Pi, use `/login` to configure a supported provider and `/model` to select a model if needed. Use whatever supported model meets your needs; Mindcraft does not require a particular provider.
4. Give Pi this prompt, replacing the destination with an actual path outside the kit:

   ```text
   Read AGENTS.md. Set up my personal Mindcraft instance at
   /absolute/path/to/my-mindcraft, outside this repository.
   Start with one real piece of work.
   ```

5. Once setup is saved, exit Pi and start a fresh session from the personal instance:

   ```sh
   cd /absolute/path/to/my-mindcraft
   pi
   ```

   Read any project trust prompt and grant trust only if you intend to use these instructions. Then ask: “Read AGENTS.md and recover our current plan, next action and stopping point.” Verify the answer against the saved decisions.

## Everyday use

Launch Pi from your personal instance. Pi supports project `AGENTS.md` discovery, but explicitly asking it to read that file is a useful recovery step if it misses the intended workflow.

Use ordinary language: “Plan my week,” “I have 45 minutes,” “Park this idea,” or “Save where we stopped.” The entry point tells Pi which skill to read. No skill registration is needed for this baseline.

For optional native skill commands, launch Pi from the personal instance with the three skill directories explicitly supplied:

```sh
pi --skill ./skills/mindcraft-setup \
   --skill ./skills/mindcraft-strategy \
   --skill ./skills/mindcraft-operations
```

You can then explicitly invoke `/skill:mindcraft-strategy` or `/skill:mindcraft-operations`, followed by your request. Those commands are conveniences; the same procedures work by directly reading their files. See Pi's [skills guide](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/skills.md) and [CLI reference](https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/cli.md).

## Switching harnesses or models

Point the next agent at the same personal instance and its `AGENTS.md`. The continuity comes from the files, not from copying a chat transcript. Use the [recovery check](walkthrough.md#check-recovery) after switching. Avoid simultaneous writers to the instance.

Pi controls tool access, provider authentication and session storage. Mindcraft's authority rules are instructions to the agent, not enforced permissions. Calendar, email and publishing integrations are optional and require separate setup and user authority.

Installation and resource-loading instructions were checked against upstream Pi documentation and a local Pi 1.2.0 installation on 26 October 2026. The full interactive workflow still needs user testing in your chosen model/provider configuration.
