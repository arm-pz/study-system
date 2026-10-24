# study-system

An agent skill that builds the system around one skill you are trying to acquire. It decomposes the skill into the components that actually matter, orders them into a roadmap with gates you can test yourself against, designs a deliberate-practice routine with a feedback source you can reach alone, sets a review schedule you adjust from observed recall, audits the assumptions that are quietly wrong, and gives a mastery verdict that is allowed to say you are not ready yet. It does not teach the topic; it hands that to `topic-primer`.

Install: `npx skills add arm-pz/study-system --skill study-system`

Ask it things like:

- "I want to get good at SQL for my reporting work. I can do basic selects, I get about four hours a week."
- "Make me a revision schedule for my certification exam, six weeks out, I keep forgetting the networking bits."
- "Every tutorial I finish I can't redo from scratch. What am I missing?"
- "Am I actually ready to take on platform work, or am I fooling myself?"

## What you get

| Mode | Output |
|---|---|
| `system` (default) | One file: breakdown, roadmap with gates, practice routine, review schedule, exercises, open gaps |
| `breakdown` | Component map: the minimum viable set, one observable proof each, what to defer and what that costs |
| `roadmap` | Ordered stages with dependency reasons, a gate per stage, and the assumption each rests on |
| `models` | The model set for the subject, with what each makes cheaper and where each misleads |
| `expert-thinking` | Practitioner decision rules as a drillable checklist |
| `feynman-test` | Explain-it-back protocol and the seam where your account broke |
| `practice` | Session design: target, difficulty band, feedback source, reps, error log, band-moving rule |
| `exercises` | Application exercises from your own context, each with success criteria |
| `gap-audit` | Gap register: the gap, the evidence, the likely cause, the first fix, the owner |
| `schedule` | Starting review ladder plus the recall-driven rule for lengthening or resetting intervals |
| `mastery` | Rubric verdict per component, evidence, missing piece, what could not be judged, re-test |

## Not for

Being taught the topic itself concept by concept (use `topic-primer`), career positioning, promotion and negotiation (use `career-track`), or a curriculum written for a class or cohort rather than one learner (use `course-builder`, in arm-pz/caffeinity-skills). Sourced research about a field is `research-brief`'s job, and polishing the prose of notes you already wrote is `wordsmith`'s. It also will not quote you a learning-science statistic or an hours-to-fluency figure it does not have; estimates come as ranges with the assumption attached.

## Install

```
npx skills add arm-pz/study-system --skill study-system
```

Or copy `skills/study-system/` into your agent's skills directory (`.claude/skills/`, `.agents/skills/`, `.cursor/skills/` or `.qoder/skills/`). With Claude Code plugins, `.claude-plugin/plugin.json` makes the repo installable as a plugin; add it to your marketplace repo as an entry pointing at `arm-pz/study-system`.

## Structure

```
study-system/
├── .claude-plugin/
│   └── plugin.json
├── LICENSE
├── README.md
├── skills/
│   └── study-system/
│       ├── SKILL.md              # intake, modes, output shape, quality bar, handoffs
│       └── references/
│           ├── system-design.md  # decomposition, roadmap order, practice, review timing
│           └── assessment.md     # gap audit, evidence rules, mastery rubric
└── tests/
    └── test-prompts.md           # trigger, implicit, near-miss and boundary cases
```
