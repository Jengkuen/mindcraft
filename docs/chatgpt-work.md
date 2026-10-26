# Use Mindcraft through ChatGPT Work mode

Use a Work mode session with access to local files. This guide assumes your app can read a chosen folder and write to a persistent local destination. Availability and interface labels may differ. Opening a GitHub link or attaching a file to an ordinary chat does not establish that access.

## Setup

1. Download and extract [Mindcraft](https://github.com/Jengkuen/mindcraft), or clone it. Keep it separate from your personal records.
2. Open a Work mode session with the extracted folder available. Choose a separate local destination for your personal instance and make it writable to that session. Use the app's folder/access controls where available.
3. Give the agent the following prompt, using actual absolute paths:

   ```text
   Read /absolute/path/to/mindcraft/AGENTS.md.
   Set up my personal instance at /absolute/path/to/my-mindcraft.
   First check that you can read the kit and write to that destination.
   Start with one real piece of work; keep my personal records outside the public repo.
   ```

4. Let the agent verify access and guide the setup conversation. It should ask about a concrete outcome and constraints, then distinguish proposals from commitments you approve. It should not require a comprehensive personal profile.
5. In a fresh Work mode conversation with the personal folder available, check recovery:

   ```text
   Read /absolute/path/to/my-mindcraft/AGENTS.md.
   Recover our current plan, next action and stopping point from the saved files.
   Tell me what is still undecided.
   ```

Verify that the answer matches what you agreed. This tests saved state rather than relying on the previous chat transcript.

## Everyday use

Start subsequent conversations in the personal instance, or explicitly name its absolute path and ask the agent to read its `AGENTS.md`. Do not assume the app automatically discovers that file or carries instructions between conversations.

- “Help me plan my week. Resume any unfinished review.”
- “I have 45 minutes. Help me work on the agreed next step.”
- “Park this idea: …”
- “Stop here. Save what happened and where to resume.”
- “What did you change? Show me the records.”

You do not need to install Mindcraft as an app plugin or personal skill. The entry point routes the agent to the Markdown skills directly.

## Files, persistence and access

Use the local instance as the canonical record and verify writes there. Chat history and saved personal context are supplementary. If your Work mode environment offers a separate file library or artifact store, make clear that Mindcraft state is being maintained in the named local instance.

If the agent can read but cannot write, it should explain that limitation and show the proposed edits without claiming they were saved. Reopen the folder with write access or move to a suitable session before treating the workflow as durable.

If a new conversation cannot find the plan, check that it is reading the personal instance rather than the kit's blank `starter/` records. Confirm the folder is still available; if the app uses temporary storage, move the instance to persistent storage and back it up.

Local files can still be sent to the selected model provider as context. Your ChatGPT settings and environment govern processing and retention; Mindcraft adds no privacy guarantee or local-model execution.
