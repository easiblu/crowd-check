# Crowd Check

Crowd Check is a Claude skill that runs simulated usability tests on mobile and desktop designs. It uses a panel of 200 personas and 14 testing methods, and every run produces heatmaps and a report.

Simulated users are a fast way to find likely problems before testing with real people. The results are predictions, not measured behaviour, so validate the important findings with real users.

## What it does

1. **Intake.** It asks what is being tested, the task, the primary objective (for example, users press the Create free now button), the scenario, the device, the testing method and the panel size.
2. **Simulation.** Each persona works through the design in character, thinking aloud, and is allowed to struggle, fail and abandon.
3. **Heatmaps.** For every screen it draws an attention heatmap, a tap map and a scroll-reach overlay, with the target element outlined. Card sorting and tree testing get grid or tree heatmaps instead.
4. **Report.** Every run ends with a report: verdict, primary objective funnel (Saw, Understood, Wanted, Pressed), scorecard by group, ranked issues, what worked, accessibility flags, and a "What could be improved" section. That section is labelled as AI-generated, for the designer to judge.

It works with designs made in Claude (artifacts or attached screens) and with live or staging URLs. On live URLs it never completes a purchase, enters payment details or creates an account.

## Persona panel

| Group | Who | Age | Tech score (1 to 10) | Personas |
|---|---|---|---|---|
| A | Low-tech millennials | 30 to 44 | 2 to 4 | 50 |
| B | Everyday users with basic tech knowledge | 27 to 48 | 5 to 6 | 50 |
| C | Educated, low-tech seniors | 61 to 78 | 1 to 3 | 50 |
| D | Tech-fluent Gen Z | 18 to 29 | 8 to 10 | 50 |

Personas 1 to 10 in each group have full profiles. Personas 11 to 50 have compact profiles with the same fields: name, age, job, tech score, device, skills, behaviour and what trips them up. The panel includes accessibility needs such as colour blindness, low vision, tremor, dyslexia and screen reader use, plus situational limits such as one-handed use, glare, slow connections and English as a second language.

## Testing methods

| Method | Use it when you have |
|---|---|
| Unmoderated task test (default) | A finished design or live URL |
| Moderated task test | A finished design and want follow-up questions |
| Prototype test | Wireframes or a clickable prototype |
| Competitor study | Your design and a competitor's |
| Benchmark | The same test to repeat over time |
| Preference test | Two or three design options |
| A/B and multivariate | Variants and want a winner on the primary objective |
| Multichannel | The same task on mobile and desktop |
| Omnichannel | One journey that crosses devices |
| Card sorting | A list of pages or categories to organise |
| Tree testing | A navigation structure to check |
| Survey | A task run, plus the SUS and SEQ questionnaires |
| 1:1 interview | A task run, plus open questions |
| Focus group | A task run, plus a group discussion |

Longitudinal studies, diary studies and guerrilla testing are not offered, because they need real people over real time.

## Panel sizes

| Panel size | Personas |
|---|---|
| Quick (default) | 8, two per group |
| Standard | 40, ten per group |
| Group | All 50 from one group |
| Full | All 200 |
| Stress | Up to 50 with the lowest tech scores or an access limitation |
| Re-test | Personas who failed or struggled last time |

Full runs take a long time and use a lot of usage. Standard is the sensible everyday choice.

## Install

**Claude apps (claude.ai, desktop, Cowork):** zip the `crowd-check` folder and upload it under Settings > Capabilities > Skills.

**Claude Code:** copy the folder into your skills directory:

```bash
cp -r crowd-check ~/.claude/skills/
```

## Usage

Ask Claude something like:

> Run a quick persona test on https://example.com. Task: find a gift under 30 and reach payment. Mobile and desktop.

Claude will ask any setup questions the request does not already answer, then run the test.

## Repository layout

```
.
├── README.md
└── crowd-check/
    └── SKILL.md
```
