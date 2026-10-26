# Design rationale and evidence

Updated 26 October 2026. Status: an experimental architecture informed by personal use, with limited implementation checks.

[Architecture](../architecture.md) defines how the kit works. This document explains why its choices are worth trying, how research relates to them, and what could justify revising them. It is optional background, not required reading for every operations session.

The design grew out of personal use; the research connections below were assembled afterwards. They motivate mechanisms and questions. They do not establish that this particular architecture improves cognition or outperforms simpler alternatives.

## What the evidence means

Keep four things distinct:

- **Design intent:** a property we want, such as understandable user control.
- **Hypothesis:** a proposed mechanism, such as a sparse orientation layer making current state easier to recover.
- **Implementation evidence:** an observed behaviour in a specified setup.
- **User-outcome evidence:** a measured effect on people's work, understanding or experience. This is not yet established for the public kit.

## 1. Separate representation from orientation

**Design pressure.** Context and ideas accumulate, but only some need reliable current visibility. Treating every note as something to act on risks turning a personal world into an undifferentiated task list.

**Choice and hypothesis.** Keep rich context in Bedrock and a sparse set of links and commitment records in Netherite. The hypothesis is that a small current view improves recovery without forcing the wider context into a fixed taxonomy.

**Research connection.** Bergman, Beyth-Marom and Nachmias propose organising personal information around the user's own topics, importance and context [R2]. This is a design approach, not an experiment validating our split. Liu et al. found position-sensitive retrieval performance in the language models and tasks they tested [R5]. That motivates checking context selection; it does not establish the same failure rate for today's models or prove that sparse Markdown views solve it.

**Trade-off and revision trigger.** Links and current views require maintenance. Cross-layer links must preserve project context rather than scatter related material. If a flat collection with one index yields equally accurate recovery with less upkeep, simplify the separation. Neither source establishes that Bedrock must be flat or that two cognitive layers are optimal.

## 2. Give project execution its own workspace

**Design pressure.** Detailed plans, source material and artifacts can grow much faster than an orientation view should.

**Choice and hypothesis.** Keep execution detail and evidence in project workspaces; let Netherite point to their controls. The hypothesis is that this keeps current commitments legible while allowing each project to use its own tools and structure.

**Basis and trade-off.** This is an engineering judgment about information ownership, not a research-established cognitive decomposition. It adds navigation and risks conflicting state. Keep commitment state canonical in Netherite and execution evidence canonical in workspace controls. If people or agents repeatedly need both copies to interpret one fact, consolidate the fact and improve the link. A small project may need only a README and one control.

## 3. Use guided planning and explicit handoffs

**Design pressure.** Starting work can require reconstructing what was decided, where work stopped and how to proceed. The process itself can become another task to manage.

**Choice and hypothesis.** Let the agent carry the review sequence, bounded work routine and handoff. Separate planning decisions from execution, while allowing explicit overrides and urgent changes. Hypothesise that a saved result, blocker and next action reduce reconstruction and repeated process negotiation.

**Research connection.** Risko and Gilbert review cognitive offloading, including its benefits, costs and dependence on metacognitive judgments [R1]. Offloading record maintenance could help, but may also transfer effort into checking the agent. Trafton et al. found faster resumption when participants could prepare before an interruption in a laboratory task [R3]. Extending that finding to written agent handoffs across days is our hypothesis; their study did not test it.

**Trade-off and revision trigger.** Writing and verifying handoffs costs time. Count that cost as well as time saved on resumption. Simplify the procedure if an ordinary project note performs as well. A weekly review cadence, particular session length and rigid strategy day are not validated by these sources.

## 4. Delegate process while keeping substantive control visible

**Design intent.** The user should retain meaningful control over commitments and direction while the agent handles routine filing and task coordination.

**Choice and hypothesis.** Make proposals, approvals, evidence and parked ideas distinguishable. Permit task management within approved scope; expose consequential changes and allow inspection and correction. Hypothesise that this provides useful assistance without requiring constant file management.

**Research connection.** Horvitz's mixed-initiative principles address uncertainty about user goals, the cost of unnecessary dialogue, direct invocation/termination, and opportunities to refine automated results [R4]. These principles inform our interaction design; they do not demonstrate that our instructions preserve agency in an LLM system.

**Trade-off and revision trigger.** Repeated confirmations can defeat the purpose of assistance. Honour authority already given, and test whether users can understand and correct a mistaken decision without learning the whole architecture. Readable files and approval language are affordances, not evidence of agency or enforced access controls.

## 5. Start with inspectable Markdown and portable procedures

**Choice and basis.** Use files, links and ordinary skill instructions because file-capable agents can read and edit them without a custom runtime. This is an implementation choice that keeps the prototype understandable and adaptable; it is not a claim that Markdown is a superior memory system.

**Trade-off and revision trigger.** Files do not enforce schemas, access boundaries or consistency between concurrent writers. Retrieval and maintenance still depend on the agent. Introduce an index, database or stronger validation when observed failures justify it. One successful recovery between two agent contexts does not establish portability across models or harnesses.

## Evidence available today

The [dated check record](evidence/2026-10-26-smoke-check.md) describes the inputs, observed recovery and limitations for the initial version.

| Check | Observation | Limit |
| --- | --- | --- |
| Static links and skill metadata | Local checks passed | Does not establish useful retrieval or instruction following |
| Native Pi skill loading | Pi 1.2.0 loaded all three skills without diagnostics | No full interactive Pi/model workflow was tested |
| Fictional setup, outline, capture and stop | One agent created an instance and saved an open workstream, outline, handoff and parked idea | One scripted scenario with explicit scope and authority |
| Fresh-agent recovery | A second context recovered the scope, missing article, time allocation and parked idea without writes | Same authoring environment; no model/harness comparison or repeated-run estimate |

Personal use supplied the design motivation. It has not produced a systematic baseline comparison, measured cognitive-effort improvement or evidence of benefit to other users. No experiment above establishes the superiority of the architecture's component split.

## Proposed comparisons

These are candidate protocols, not scheduled work or reported results. Start with the smallest comparison that tests an actual uncertainty.

| Question | Comparison | Observe; reason to reconsider |
| --- | --- | --- |
| Does the separation earn its upkeep? | Layered records versus a flat folder plus one index, using matched facts and the same authority/workflow instructions | Recovery errors, stale-state mistakes, file reads and maintenance time; simplify if the baseline performs as well at lower cost |
| Do structured handoffs help? | Matched task histories with and without an explicit result/blocker/next-action handoff | Correct next action, time to resume and total write/check/recovery effort; shorten the handoff if it adds cost without benefit |
| Does guided strategy/operations help the person? | Comparable real work sessions with the procedures versus ordinary agent chat, counterbalancing order | Time to first useful action, clarification/correction effort, task quality and user-reported friction; revise if the routine adds burden or obscures the user's reasons |
| Does portability hold? | Repeat a fixed fictional fixture in separately recorded model/harness combinations | Setup success, correct recovery, ability to correct a stale record, and scope violations; narrow compatibility claims to observed configurations |

Before a comparison, specify the expected facts, scoring rules and what difference would matter. Keep model, harness, prompts, tool access and context budget fixed where possible; record exceptions. Reset sessions and counterbalance cases to reduce carryover. Report all attempts and failures, including human corrections, rather than selecting a good transcript.

For personal trials, also ask whether the user can explain the chosen outcome and change an incorrect record. These are practical checks, not validated measures of agency. Increased output or a pleasant conversation alone does not establish increased cognitive capability.

## References

- **[R1]** Risko, E. F., & Gilbert, S. J. (2016). *Cognitive Offloading*. Trends in Cognitive Sciences, 20(9), 676–688. [DOI](https://doi.org/10.1016/j.tics.2016.07.002) · [Author manuscript](https://discovery.ucl.ac.uk/id/eprint/1508770/1/gilbert_TiCS_OFFLOADING_RPS.pdf). Review and conceptual framework.
- **[R2]** Bergman, O., Beyth-Marom, R., & Nachmias, R. (2003). *The user-subjective approach to personal information management systems*. Journal of the American Society for Information Science and Technology, 54(9), 872–878. [DOI](https://doi.org/10.1002/asi.10283) · [Author manuscript](https://www.tau.ac.il/education/muse/publications/81.pdf). Design approach.
- **[R3]** Trafton, J. G., Altmann, E. M., Brock, D. P., & Mintz, F. E. (2003). *Preparing to resume an interrupted task: effects of prospective goal encoding and retrospective rehearsal*. International Journal of Human-Computer Studies, 58, 583–603. [DOI](https://doi.org/10.1016/S1071-5819(03)00023-5) · [Author-hosted paper](https://gregtrafton.com/papers/preparing.to.resume.pdf). Human laboratory experiment.
- **[R4]** Horvitz, E. (1999). *Principles of mixed-initiative user interfaces*. Proceedings of CHI '99, 159–166. [DOI](https://doi.org/10.1145/302979.303030) · [Author's institutional publication page](https://www.microsoft.com/en-us/research/publication/principles-mixed-initiative-user-interfaces/). Design principles illustrated with a scheduling system.
- **[R5]** Liu, N. F., et al. (2024). *Lost in the Middle: How Language Models Use Long Contexts*. Transactions of the Association for Computational Linguistics, 12, 157–173. [Paper and metadata](https://aclanthology.org/2024.tacl-1.9/) · [DOI](https://doi.org/10.1162/tacl_a_00638). Experiments on multi-document question answering and key-value retrieval in the models evaluated.
