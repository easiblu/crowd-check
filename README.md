# Crowd Check

**Simulated usability testing for mobile and desktop designs, as a Claude skill.**

Crowd Check runs your design or live page past a panel of 200 simulated users with very different levels of tech skill. It tells you who reached your main goal, where the others got stuck, and what you could change. Every run produces heatmaps and a full report.

<img width="1280" height="728" alt="telegram-cloud-photo-size-5-6052956565297371789-y" src="https://github.com/user-attachments/assets/c737fa5e-439b-45be-ab7e-2e70178b979e" />


> [!IMPORTANT]
> Crowd Check simulates users. Its results are predictions, not measured behaviour. Use it to find likely problems early and cheaply, then confirm the important findings with real people before making big decisions.

---

## Contents

- [What you get](#what-you-get)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick start](#quick-start)
- [How a run works](#how-a-run-works)
- [Choosing a testing method](#choosing-a-testing-method)
- [Choosing a panel size](#choosing-a-panel-size)
- [The persona panel](#the-persona-panel)
- [Reading the report](#reading-the-report)
- [Example prompts](#example-prompts)
- [Tips for useful results](#tips-for-useful-results)
- [Limitations](#limitations)
- [Customising the skill](#customising-the-skill)
- [FAQ](#faq)
- [Repository layout](#repository-layout)

---

## What you get

| | |
|---|---|
| **200 personas** | Four groups of 50, from first-time online shoppers to developers |
| **14 testing methods** | Task tests, prototype tests, A/B, preference, competitor, benchmark, card sorting, tree testing, surveys, interviews, focus groups and more |
| **Heatmaps, every run** | Attention heatmap, tap map and scroll reach for each screen and device |
| **Report, every run** | Verdict, goal funnel, scores by group, ranked issues, what worked, accessibility flags and suggested improvements |
| **Mobile and desktop** | Mobile at 390 × 844, desktop at 1440 × 900 |
| **Two kinds of input** | Designs in Claude (artifacts or uploaded screens) or live and staging URLs |

---

## Requirements

- A Claude plan where skills are available: the Claude apps (web, desktop, Cowork) or Claude Code.
- **For live URLs:** browser access in your Claude environment, such as Cowork, Claude in Chrome, or Claude Code with a browser tool. Without it, upload screenshots instead.
- **For heatmaps:** code execution, so Claude can draw the overlays. This is on by default in Cowork and Claude Code; in the web app, turn on code execution under Settings > Capabilities.

---

## Installation

### Option A: Claude apps (claude.ai, desktop, Cowork)

1. Download or clone this repository.
2. Zip the `crowd-check` folder so the zip contains `crowd-check/SKILL.md`:
   ```bash
   zip -r crowd-check.zip crowd-check
   ```
3. In Claude, open **Settings > Capabilities > Skills** and upload `crowd-check.zip`.
4. Make sure the skill is switched on.

### Option B: Claude Code

Install for your user account:

```bash
git clone https://github.com/<your-username>/crowd-check.git
cp -r crowd-check/crowd-check ~/.claude/skills/
```

Or install for a single project, so everyone working on it gets the skill:

```bash
mkdir -p .claude/skills
cp -r crowd-check/crowd-check .claude/skills/
```

Restart Claude Code. The skill loads automatically when a request matches it.

### Updating

Pull the latest version, then repeat the steps above. In the Claude apps, delete the old skill before uploading the new zip.

---

## Quick start

1. Open a chat with the skill switched on.
2. Give Claude a design (upload screens, or link a Claude artifact) or a URL.
3. Say what you want to test:

   ```
   Run a Crowd Check on https://example.com.
   Goal: users press "Create free now".
   Mobile and desktop, quick panel.
   ```

4. Answer any setup questions Claude asks.
5. Get the verdict in the chat, plus a link to the full report with heatmaps.

A Quick run with 8 personas on a short flow usually takes a few minutes.

---

## How a run works

```
Intake  →  Simulation  →  Heatmaps  →  Report
```

### 1. Intake

Claude asks about anything your request doesn't already cover, in one round:

| Question | Example answer |
|---|---|
| What is being tested? | A Claude artifact, uploaded screens, or a URL |
| The task | "Find a birthday card and get to checkout" |
| **Primary objective** | "Users press the Create free now button" |
| Scenario | "Saw an Instagram ad, wants a card for a friend" |
| Secondary objectives (optional) | "Notices the price", "Opens the menu" |
| Device | Mobile, desktop or both (default: both) |
| Method | See [Choosing a testing method](#choosing-a-testing-method) (default: Unmoderated task test) |
| Panel size | See [Choosing a panel size](#choosing-a-panel-size) (default: Quick) |

The **primary objective** is the success measure for the whole run. Personas are only told the scenario, never which button to press, because the point is to see whether your design leads them there.

### 2. Simulation

Each persona, in character:

- takes a five-second first look and says what they think the page is;
- works through the task step by step, thinking aloud;
- is held to their real limits: unfamiliar icons, small tap targets, low contrast, skimming, slow connections, distrust;
- is allowed to struggle, fail and abandon.

Every persona is tracked through the **goal funnel**: Saw, Understood, Wanted, Pressed.

### 3. Heatmaps (always produced)

For every screen and device:

- **Attention heatmap:** where personas looked, cool to hot.
- **Tap map:** every tap, coloured by persona group, with mis-taps shown hollow.
- **Scroll reach:** how far down the page each share of personas got.
- **Goal marker:** your primary objective outlined, with the share who saw it and the share who pressed it.

Card sorting and tree testing get grid or tree heatmaps instead. Every heatmap is labelled as predicted, not tracked.

### 4. Report (always produced)

A single report page with the heatmaps embedded, published as a Claude artifact where possible, otherwise as an HTML file. See [Reading the report](#reading-the-report).

---

## Choosing a testing method

Not sure which one to pick? Claude recommends one during intake based on what you have.

| You have... | Use |
|---|---|
| A finished design or live URL | **Unmoderated task test** (default) or **Moderated task test** |
| Wireframes or a clickable prototype | **Prototype test** |
| Two or three design options | **Preference test**, or **A/B and multivariate** if you want a winner on your goal |
| Your design and a competitor's | **Competitor study** |
| A test you want to repeat over time | **Benchmark** |
| A journey across mobile and desktop | **Multichannel** or **Omnichannel** |
| A list of pages or categories to organise | **Card sorting** |
| A navigation structure to check | **Tree testing** |
| Questions about opinions and reasons | **Survey**, **1:1 interview** or **Focus group** (always run after a task) |

<details>
<summary><strong>What each method does</strong></summary>

| Method | What personas do | Extra output |
|---|---|---|
| Unmoderated task test | Complete the task alone, thinking aloud | Standard report |
| Moderated task test | Same, with neutral follow-up questions and at most one hint | Probe answers, number of hints given |
| Prototype test | Use a concept, saying what they expected when links are missing | List of expected outcomes for unlinked taps |
| Competitor study | Do the same task on your product and one competitor | Side-by-side scores and heatmaps |
| Benchmark | Same personas, tasks and metrics on every run | UX score (SUS, completion, SEQ), JSON results, change since last run |
| Preference test | Glance at two or three options for five seconds each, then pick one | Preference share and reasons, flagged where preference beats performance |
| A/B and multivariate | Do the task on each variant | Goal reach per variant, head-to-head table, recommended winner |
| Multichannel | Do the same task on each device they own | Scorecard and issues per device |
| Omnichannel | Do one journey across devices | Journey map with drop-off at each hand-over |
| Card sorting | Group cards (open sort) or place them into your categories (closed sort) | Similarity matrix heatmap, common group names |
| Tree testing | Find items in a text-only menu tree | Success, directness, first-click accuracy, tree heatmap |
| Survey | Answer SEQ, SUS and your own questions in character | SUS by group, SEQ by task, themed answers |
| 1:1 interview | Answer five to eight open questions | Themes with quotes, unmet needs |
| Focus group | Discuss in groups of six to eight | Summary, agreements, conflicts, ideas |

</details>

Longitudinal studies, diary studies and guerrilla testing aren't offered, because they need real people over real time. Use Benchmark as the nearest simulated option.

Methods can be combined: for example, *"Unmoderated task test, then a survey."*

---

## Choosing a panel size

| Panel size | Personas | Best for |
|---|---|---|
| **Quick** (default) | 8 (2 per group) | Early drafts, fast checks |
| **Standard** | 40 (10 per group) | Regular design reviews |
| **Group** | 50 (one group) | Questions about one audience |
| **Full** | 200 | Pre-handoff or pre-launch review |
| **Stress** | Up to 50 lowest-tech or access-limited | Finding where the design breaks |
| **Re-test** | Personas who failed last time | Checking a fix |

> [!TIP]
> Start with Quick while designing, use Standard for reviews, and save Full for the final check. Full runs take a long time and use a lot of usage.

---

## The persona panel

| Group | Who | Age | Tech score (1–10) | Personas |
|---|---|---|---|---|
| **A** | Low-tech millennials, mostly phone-only, lost outside a few familiar apps | 30–44 | 2–4 | 50 |
| **B** | Everyday users who know browsers and online shopping basics | 27–48 | 5–6 | 50 |
| **C** | Educated, capable seniors who are unfamiliar with digital conventions | 61–78 | 1–3 | 50 |
| **D** | Tech-fluent Gen Z with no patience for friction | 18–29 | 8–10 | 50 |

Personas 1–10 in each group have full profiles with a voice line. Personas 11–50 have compact profiles with the same fields: name, age, job, tech score, device, skills, behaviour and what trips them up.

The panel deliberately includes accessibility needs (colour blindness, low vision, hand tremor, dyslexia, screen reader use) and real-world conditions (one-handed use, glare, slow data, shared devices, English as a second language).

**Example persona:**

> **C4. Giovanni Russo, 74, retired literature professor.** Tech 2. Laptop.
> Reaches every site by typing its name into a search engine. Can't tell adverts from content, and doesn't recognise unlabeled icons.
> Trips on: icon-only navigation, sponsored blocks, abbreviations.
> *"What is the little bag for?"*

---

## Reading the report

| Section | What it tells you |
|---|---|
| **Verdict** | Method, panel size, your goal, how many reached it, and the biggest blocker |
| **Goal funnel** | Saw, Understood, Wanted, Pressed by group, plus what people pressed instead |
| **Heatmaps** | Attention, taps and scroll reach for each screen |
| **Scorecard by group** | Completion, effort, trust and abandons for groups A–D, by device |
| **Method results** | The extra output for the method you chose |
| **Top issues** | Screen, element, what happened, who was affected, severity (1–4), suggested fix |
| **What worked** | Patterns to keep |
| **What could be improved** | Suggested changes with expected impact and effort |
| **Persona highlights** | The most revealing sessions, with quotes |
| **Mobile vs desktop** | Differences between devices |
| **Accessibility flags** | Contrast, text size, tap targets under 44 px, colour-only signals, missing labels |
| **Validate with real users** | The three findings most worth confirming with real people |

**Severity scale:** 4 Blocker · 3 Major · 2 Minor · 1 Cosmetic. Priority is severity multiplied by the share of personas affected.

> [!NOTE]
> The **What could be improved** section is AI-generated from simulated users. You are the designer: decide which suggestions matter for your product and users, and which don't.

---

## Example prompts

**Quick check of a live page**
```
Crowd Check https://staging.example.com/pricing
Goal: users press "Start free trial". Mobile only, quick panel.
```

**Prototype on uploaded screens**
```
Here are 5 screens of our onboarding prototype. Prototype test,
standard panel. Goal: users finish the profile step.
```

**Choosing between two designs**
```
Preference test on these two hero designs, then an A/B on the goal
"press Create your card". Standard panel, desktop and mobile.
```

**Seniors only**
```
Run Group C on our checkout. Goal: users reach the payment step.
Desktop.
```

**Navigation structure**
```
Tree test this menu structure with the standard panel.
Find tasks: "Wedding invitations", "Track my order", "Gift cards".
```

**Benchmark over time**
```
Benchmark run on the homepage, goal "Create free now", standard panel.
Here's last month's report for comparison.
```

**Check a fix**
```
Re-test the personas who failed last time on the updated checkout.
```

---

## Tips for useful results

- **Give one clear goal.** "Users press Create free now" gives a sharper result than "see if the page works".
- **Describe a realistic scenario.** Where users come from changes what they look for.
- **Share the whole flow.** With static screens, personas stop where the screens stop.
- **Use staging for live tests.** Crowd Check never buys, pays or creates accounts, but staging keeps test traffic out of your analytics.
- **Rotate personas.** Quick and Standard pick different personas each run, so repeated runs widen coverage.
- **Treat numbers as direction.** A 40 % goal rate from 8 simulated personas is a signal, not a statistic.

---

## Limitations

- Personas are simulations based on written profiles. They can't fully reproduce real emotion, context or randomness.
- Results from static screens depend on Claude's reading of the image; live URLs give more accurate positions.
- Heatmaps are predicted from simulated attention, not eye tracking or click analytics.
- Large runs (Full, 200 personas) take a long time and use a lot of usage.
- The panel describes general online shoppers. If your audience is specialised (clinicians, B2B buyers, children's parents only), say so and Claude will suggest additional personas.

---

## Customising the skill

Everything lives in [`crowd-check/SKILL.md`](crowd-check/SKILL.md):

| To change... | Edit section |
|---|---|
| Intake questions or defaults | 1. Set up the run |
| Testing methods | 2. Testing methods |
| Live URL viewport sizes and safety rules | 3. Get the design in front of you |
| Simulation rules and scorecard | 4. Simulate each persona |
| Heatmap style | 5. Heatmaps |
| Report sections and the AI notice | 6. Report |
| Personas | 7. The persona panel |

**Adding a persona:** copy the format of an extended persona (for example A11) and keep its age and tech score inside the group's range so the groups stay balanced.

---

## FAQ

**Does it replace real user testing?**
No. It's a fast first pass for catching likely problems before you spend time and money on real participants.

**Can it test Figma files?**
Export the frames as images and upload them, or share them as a Claude artifact. Figma links aren't a supported input yet.

**Will it buy things or sign up on my live site?**
No. It stops at the payment step and never enters payment details or creates accounts.

**Why do I get different results each run?**
Quick and Standard rotate which personas take part, and the simulation isn't deterministic. For comparable runs, use Benchmark, which reuses the same personas.

**Can I run it without being asked questions?**
Yes. Put the task, goal, device, method and panel size in your first message. In unattended or scheduled runs, Claude picks sensible defaults and lists them at the top of the report.

---

## Repository layout

```
.
├── README.md
└── crowd-check/
    └── SKILL.md      # The skill: method, rules and the 200-persona panel
```
