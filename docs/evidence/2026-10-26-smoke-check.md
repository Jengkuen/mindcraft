# Initial implementation checks — 26 October 2026

This is a retrospective record of checks performed during creation of the first public kit. It documents a single scripted scenario, not a user study, controlled comparison or reliability estimate.

## Version and environment

- Kit revision: [40d0978](https://github.com/Jengkuen/mindcraft/commit/40d0978bf9b5e43be111bfa2b0ba65db2d60c59f).
- Workflow: two separately started agent contexts in the authoring environment, with the second receiving no prior conversation or expected answer.
- Model identifier, sampling settings, token use and timings were not recorded. The contexts were not launched through the ChatGPT or Pi interactive interfaces.
- Native skill loader: installed Pi 1.2.0, tested separately without a model invocation.
- Records: a disposable local instance with fictional data. The temporary fixture and full tool traces were not committed; the inputs and recovery response are preserved below. This limits independent auditing of the original run.

## Checks and observed results

1. **Kit structure:** local Markdown links resolved, all three skills passed the skill-creator metadata validator, and staged files passed Git's whitespace check.
2. **Pi loading:** Pi's installed `loadSkills` function was invoked with the three skill directories and default discovery disabled. It returned `mindcraft-setup`, `mindcraft-strategy` and `mindcraft-operations`, with an empty diagnostics list. This tests loading, not model behaviour or the full CLI.
3. **Setup/execution:** the first agent created a self-contained instance, the approved reading-note project and workstream, an outline, handoff and ingest entry. Inspection of the saved files showed the article was still missing and the workstream remained open. The 45 minutes were recorded as allocated, not elapsed.
4. **Recovery:** the second agent returned the response below. It matched the inspected files and reported no writes.

The setup agent reported verifying nine live records and 31 links. A later direct check counted 33 live-state Markdown links with none broken and confirmed the copied starter templates matched the originals. These counts used different check scopes; neither is a behavioural reliability score.

## Setup request

The following preserves the request's wording with temporary source/destination paths normalised. Use real absolute paths when repeating it.

```text
Read <kit>/AGENTS.md and use its setup procedure to create a personal
instance at <instance>. Use only this fictional scenario: I want a
one-page reading note with a summary, two questions and one application.
I have 45 minutes today. I approve creating the reading-note workspace
and its single draft workstream with that scope, and allocating those
45 minutes to it. Start by producing an outline. I haven't provided the
article yet. Park this idea: maybe turn the note into a podcast later,
no deadline. Then stop, save the outline and where to resume; don't
close the workstream. Use UTC for dates in this fictional instance.
Keep all work inside <instance> and do not use external tools, publish,
send messages, or change any other personal records. Report what was
saved and any procedural obstacles.
```

The fictional timezone was explicitly supplied. It is not a default for real users. The task supplied approval up front; it did not test whether an agent would correctly seek missing approval.

## Recovery request

```text
Read <instance>/AGENTS.md. I'm back. Where were we? Recover our current
plan, next action, stopping point and any parked ideas from the saved
files. Don't change the plan or write any files. Use only that instance
and no external tools.
```

## Recovery response

The second agent returned:

> We stopped after saving and checking the reading-note outline.
>
> - **Current plan:** Produce one page with a source-grounded summary, exactly two questions, and one application. The project and its single drafting workstream are approved and remain open.
> - **Stopping point:** The outline and handoff are saved. The full note is unfinished because the article hasn’t been supplied. The instruction to save the outline and stop was honoured.
> - **Next action:** Receive the article or relevant text, then draft and check the note. The approved allocation was 45 minutes for 26 October; elapsed time is unknown. If resuming another day, establish available time again.
> - **Parked idea:** “Maybe turn the note into a podcast later.” It has no deadline, allocation, or commitment.
>
> No broader weekly review has been conducted, and no strategy decision is pending within this approved scope. I made no changes or writes.

## Interpretation and repetition

The run demonstrates one successful path from file-based setup to a recoverable stopping point. It does not isolate which component helped, estimate failure rates, establish enforcement of authority boundaries, or measure a person's effort or understanding. The simple fixture supplied explicit instructions, authority and a clear missing dependency.

To repeat it, use the kit at the recorded revision, a new disposable destination and the setup request above. Start a second context with only the recovery request and access to that destination. Inspect the files as well as the reply. Record model/harness versions, prompts, attempts, failures and corrections. The [walkthrough](../walkthrough.md) provides an interactive variant; its conversational sequence differs from this single setup request.

Future checks should include stale/conflicting state, missing approval, failed writes, interrupted reviews, realistic context growth and repeated runs. See the [design rationale](../design-rationale.md#proposed-comparisons) for proposed comparisons; none is reported as completed here.
