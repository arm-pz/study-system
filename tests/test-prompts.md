# Test prompts

Cases for checking that `study-system` fires when it should and stays out of the way when it should not. Each row states the message, the skill that should answer, the mode it should answer with, and a pass condition you can actually check.

The honesty checks apply to every case: no invented learning-science statistic, no hours-to-fluency figure, no promise of a result, and any number must carry its assumption or be marked `unknown`.

## Clear triggers

| # | Message | Expected skill | Expected mode or command | Pass condition |
| --- | --- | --- | --- | --- |
| 1 | "I want to get good at SQL for my reporting work. I can write basic selects, I get maybe four hours a week." | study-system | `breakdown` then `roadmap` | Names components as verbs with one proof each; each stage states its dependency reason and an observable gate; no time-to-competence figure, or a range with the four-hours-a-week assumption attached |
| 2 | "Build me a revision schedule for my certification exam, six weeks out. I keep forgetting the networking bits." | study-system | `schedule`, exam variant | Ladder is labelled a starting schedule to adjust from observed recall, not a constant; the recall score moves the interval and the file says which item moved and why; daily review load is bounded by the hours given; no forgetting-curve percentage |
| 3 | "How should I actually practise guitar? I've been playing the same three songs for a year." | study-system | `practice` | Session has target, difficulty band, a feedback source the learner can reach alone, reps and an error log; band-moving rule stated; progress is not measured in minutes in seat |

## Implicit triggers

The user describes the outcome without naming the deliverable.

| # | Message | Expected skill | Expected mode or command | Pass condition |
| --- | --- | --- | --- | --- |
| 4 | "Every tutorial I finish I can't redo from scratch. What am I doing wrong?" | study-system | `gap-audit` | Names the hidden-support and familiarity-versus-recall gap types with the question that exposes them ("what was open on the screen"); does not then teach the tutorial's subject; offers the `topic-primer` handoff block for the teaching half |
| 5 | "Am I ready to take on platform work or am I fooling myself?" | study-system | `mastery` | Asks for artefacts before judging; verdict per component with quoted evidence; a "not ready" outcome is available and stated without softening adjectives; `Not judged` section present; if the real question turns out to be positioning or the promotion conversation, hands off to `career-track` |

## Near-misses

These should not end with `study-system` producing the artifact.

| # | Message | Expected skill | Expected mode or command | Pass condition |
| --- | --- | --- | --- | --- |
| 6 | "Teach me distributed systems from zero, one concept at a time." | topic-primer | `concepts` / `foundation` | study-system does not begin a lecture: outputs the `HANDOFF — study-system -> topic-primer` block and says topic-primer owns the teaching. At most it offers the plan around the teaching |
| 7 | "My manager says I need more visibility to reach senior. What should I work on this year?" | career-track | positioning and promotion plan | study-system does not produce a practice routine or roadmap as the answer; it hands off, passing only the skill gap it can see, and says career-track owns the move |
| 8 | "Write the eight-module curriculum for my evening class on Python." | course-builder | module design | study-system declines on the one-learner-versus-a-class rule and names the owner; it does not silently produce a personal roadmap addressed to a group |
| 9 | "Explain this like I'm twelve: what actually happens when a browser resolves a name?" | topic-primer | `eli5` | No explanation is written here; the handoff block appears, and the seam-finding protocol is not substituted for the teaching |
| 10 | "What's known about how teams structure a data platform? Cite sources." | research-brief | sourced brief | study-system does not assert industry facts from memory; any field claim inside a plan is marked `[unverified]` or handed to research-brief for dated sourcing |

## Boundary pairs

| Message | Should trigger | Why |
| --- | --- | --- |
| "Plan how I learn React, then teach me the first part." | study-system, then topic-primer | one builds the plan and gates, the other does the concept-by-concept teaching |
| "Teach me React hooks." | topic-primer | teaching only, no plan requested |
| "What should I learn next to get promoted?" | career-track | the decision is the career move, the syllabus is downstream of it |
| "Audit where my accounting knowledge is wrong, then drill me until it isn't." | study-system, then topic-primer | gap audit belongs here; the drilling that supplies new instruction belongs to the teaching skill |
| "Make a revision plan for the whole cohort before the June exam." | course-builder | a class, not one learner |
| "I want to learn Spanish, where do I even start?" | topic-primer | first contact with a subject; no plan was asked for. This pair was added by the tune pass because the old trigger wording, "wants to learn or get good at something", pulled this message here |
| "Six weeks into Spanish and nothing sticks. Sort out my routine." | study-system | retention, routine and a gap audit around a skill already in progress |

## Notes on running these

- Checked by hand against the descriptions of `topic-primer` and `course-builder` (arm-pz/caffeinity-skills, re-pointed 2026-10-24 from `module-learning-path-generator`, which is not published), and the `career-track` and `research-brief` descriptions in the suite build spec: for each message, decide which skill an agent would load. `career-track` is not installed in this environment yet, so case 7 and the promotion pair were judged from its spec description only, not from its live SKILL.md.
- skill-creator's automated description-improvement loop was not run; it needs tooling that is not available here, so do not read these as automated results.
- Add a case for every boundary change, one on each side.
