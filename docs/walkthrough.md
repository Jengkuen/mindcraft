# Worked example: plan, work, stop and resume

This is a fictional, illustrative scenario and a manual check. It is not a transcript of a completed user trial. Run it in a disposable personal instance if you want to inspect the resulting records.

## 1. Set up and propose a bounded project

After following either setup guide, tell the agent:

```text
Use this fictional scenario: I'm writing a one-page reading note about
an article. I have 45 minutes today. Propose a small project and one
workstream for a draft with a summary, two questions and one application.
Don't publish or send anything. I will provide the article when needed.
```

The agent should propose a reading-note project, a draft workstream, the next action and a stopping condition. It should not mark the proposal active merely because it created files. Article content and a wider personal mission are not yet known.

## 2. Approve and save a plan

```text
I approve the reading-note workspace and the draft workstream with that
scope. Allocate today's 45 minutes to it. Start by making an outline.
```

The agent should save the project and workstream as approved, link the workspace control, and record the allocation. A reasonable task is to create headings for summary, questions and application. It must not fabricate a summary of an article it has not read.

Expected records:

| Record | Purpose |
| --- | --- |
| `netherite/README.md` | Register the project |
| `netherite/projects/reading-note.md` | Record active workstream and current management task |
| `workspaces/reading-note/README.md` | Link the operating view and control |
| `workspaces/reading-note/draft.md` | Define the agreed boundary, state, checkpoint and handoff |
| `workspaces/reading-note/note.md` | Hold the outline artifact |
| `netherite/current-week.md` | Record the approved allocation and latest handoff pointer |

Filenames may vary if the links remain coherent. Add a Bedrock context document only if there is wider context worth retaining; do not write an artificial biography to complete a chain.

## 3. Capture without redirecting

```text
Park this idea: maybe turn the reading note into a podcast later.
No deadline. Keep going with the note.
```

The agent should save an ingest entry. It should not add a podcast workstream, change the approved allocation, or start producing a podcast.

## 4. Stop before the whole project is done

```text
Stop here. Save the outline and where to resume. We haven't read the
article yet, so the next step needs its text. Don't close the workstream.
```

The handoff should identify the outline artifact, the missing article and the next action. The workstream remains active; completing the outline task does not close it. The agent should not record 45 minutes of actual work merely because 45 minutes was allocated.

## Check recovery

Open a fresh conversation or launch Pi again from the same personal instance:

```text
Read AGENTS.md. Where were we? Recover the current plan, next action,
stopping point and any parked ideas from files. Don't change the plan.
```

Check that it recovers the approved reading-note scope and allocation, the outline, the missing article, and the parked podcast idea without activating it. It should say that the article must be supplied before a grounded summary can be written.

Inspect the records if the answer differs. Check whether the wrong instance was selected, a write failed, a handoff was incomplete, or the agent skipped a relevant file. Repair the smallest cause and repeat recovery. Static link checks cannot establish this behaviour.

For real use, try the same loop with one actual task. At the next review, ask what helped, what created friction and what one change is worth making. A successful demonstration alone does not establish lower cognitive effort over time.
