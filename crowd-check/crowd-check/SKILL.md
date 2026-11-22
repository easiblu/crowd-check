---
name: "crowd-check"
description: "Crowd Check: simulate user testing of a UX or UI design (mobile or desktop) with a panel of 200 personas across four tech-skill groups of 50, using a chosen testing method. Use for persona test, user test, usability simulation, 'test this design/URL with users', or crowd check."
---

# Crowd Check

Run a simulated usability test of a design or live page with a fixed panel of 200 personas (four groups of 50), then report what broke, for whom, and what to fix, with a fix task and ready-to-use prompt for every issue.

The value of this skill comes from the personas behaving differently from each other and from the designer. A run where everyone completes the task and says nice things is a failed run. Stay strictly inside each persona's knowledge and habits.

Simulated users are a fast way to find likely problems before real testing. They are not evidence of real behaviour. Report findings as hypotheses to validate, never as measured results.

## 1. Set up the run

Every run starts with a short intake in two rounds, using the question tool when the session has one. Ask the scenario first, on its own, because who the users are and what they want shapes the task, the objective and the method you propose next. Then ask the remaining questions together in a second round. Do not start simulating until the primary objective is confirmed. Skip a question only when the request already answers it; if the request already gives the scenario, go straight to round 2. In an unattended run, pick the most likely answers, state them at the top of the report and carry on.

**Round 1: Scenario.**

1. **Scenario.** Ask who the users are, where they arrive from and what they want, for example: saw an ad and wants to make a card for a friend, or runs a small website and is opening the dashboard for the first time. Look at the design first and offer two or three realistic scenarios as options, with free text allowed. Personas are given this motive only. Never tell a persona which button to press; the test is whether the design leads them to it.

**Round 2: Everything else.** Base the options you offer on the scenario chosen in round 1.

2. **What is being tested.** A design in Claude (a Design artifact or artifact link, or screens attached in chat) or a live/staging URL. Usually clear from the request; ask only if it is not.
3. **The task.** A concrete goal that fits the scenario, with a clear end state, for example: find a birthday gift under 30 and get to the payment step. If no task is given, propose two or three realistic ones and confirm. Never test the page in general.
   - **Primary objective.** Ask which single action or outcome matters most, naming the exact element where possible, for example: users press the Create free now button. This is the success measure for the whole run. If the answer is vague, look at the design, propose two or three candidate objectives that fit the scenario and have the designer pick one. Ask the task and the primary objective as one question when they go together.
   - **Secondary objectives (optional).** Up to two other things worth tracking, such as noticing the price or opening the menu.
4. **Device.** Mobile, desktop, or both. Default: both.
5. **Method.** Ask which testing method they want to run. Offer the methods in section 2, each with a one-line description, and mark the one recommended for their situation using the chooser in section 2. Default: Unmoderated task test. For Card sorting and Tree testing, the task becomes the items to sort or find, and the primary objective becomes the item or destination that matters most. For Survey, 1:1 interview and Focus group, also ask for any questions the designer wants included.
6. **Panel size.** Default to Quick.

| Panel size | Personas | Use for |
|---|---|---|
| Quick | 8 personas, 2 per group, rotate picks between runs | Early drafts, fast checks |
| Standard | 40 personas, 10 per group, mixing core and extended, rotate picks between runs | Regular design reviews |
| Group | All 50 from one group | Questions about one audience |
| Full | All 200, 50 per group, run group by group | Pre-handoff or pre-launch review |
| Stress | The 20 lowest tech scores plus personas with an access or device limitation, up to 50 | Finding the floor of the design |
| Re-test | Only personas who failed or struggled last time | Checking a fix |

Whenever a panel size uses fewer than all personas, sample evenly across the four groups. Respect each persona's listed device. A phone-only persona is never run on desktop. If the test is desktop only, skip phone-only personas and say so.

## 2. Testing methods

Ask which method to use as part of the intake. Recommend one based on what the designer has and what they want to learn:

- A structure or list of pages, no screens yet: Card sorting or Tree testing.
- Wireframes or a clickable prototype: Prototype test.
- Two or three design options: Preference test, or A/B and multivariate when they want a winner on the primary objective.
- A finished design or live URL: Unmoderated task test (default) or Moderated task test.
- Their design and a competitor's: Competitor study.
- The same test repeated over time: Benchmark.
- A journey on mobile and desktop: Multichannel, or Omnichannel when one journey crosses devices.
- Opinions and reasons more than behaviour: Survey, 1:1 interview or Focus group, always run after a task so the heatmaps exist.

Methods can be combined, for example an Unmoderated task test followed by a Survey. Every method reports both numbers (completion, funnel, scores) and the reasons behind them. Simulated numbers show direction, not statistical proof; say so in the report.

### Unmoderated task test (default)

Each persona works through the task alone, thinking aloud, with no help. Run exactly as in section 4. Use it for most design checks.

### Moderated task test

As above, but a simulated moderator asks neutral follow-up questions at key moments: after a wrong turn, after a long pause, at the primary objective, and at the end. Questions never hint at the answer: ask what they expected to happen, never whether they saw a particular button. When a persona fails three attempts at a step, the moderator may give one neutral prompt; record it as an assist and count the task as Completed with assist, not Completed.

- Extra output: answers to each probe question, grouped by theme, and the number of assists per group.

### Prototype test

For wireframes and prototypes. Personas are told they are using a concept and some parts may not work. When they tap something with no linked screen, record what they expected to happen instead of stopping silently. Judge layout, wording and flow rather than visual polish, unless the prototype is high fidelity.

- Extra output: a list of unlinked taps with the outcome each persona expected, which shows what users assume each element does.

### Competitor study

The same task on the designer's product and one competitor, never more than two experiences per persona. Alternate which product each persona sees first. The live URL safety rules in section 3 apply to the competitor too.

- Extra output: side-by-side scorecard and heatmaps, where the competitor wins, where ours wins, and patterns worth learning from.

### Benchmark

The same tasks, personas and metrics every time, so runs can be compared. The first run picks the persona set and the report lists their IDs; later runs reuse exactly that set instead of rotating. Every benchmark run ends with the Survey questions.

- Extra output: a UX score made of average SUS (0 to 100), completion rate and average SEQ, per group and overall, plus a machine-readable results block (JSON) at the end of the report. On later runs, ask for the previous report or its results block and show the change per metric and per group.

### Preference test

Personas see two or three design options, never more, in alternating order. For each they first do a five-second glance (what is this, what would you press), then choose the one they prefer and say why, covering look, clarity, trust and whether it makes them want to do the primary objective.

- Extra output: preference share per group, top reasons, and attention heatmaps for each option on the same colour scale. Preference is not performance: flag any case where the preferred option did worse on the task.

### A/B and multivariate

The same personas run the task on each variant: two for A/B, three or more for multivariate. Alternate the order across personas. Most useful when variants differ in one element.

- Extra output: primary objective reach rate per variant and group, a head-to-head table per persona, and a recommended winner with the reason and who each variant is worse for. State that a real A/B test on live traffic is needed to confirm conversion.

### Multichannel

The same task on mobile and desktop, plus tablet if provided. Each persona runs on every device they own; phone-only personas run mobile only.

- Extra output: a scorecard per device, issues unique to one device, and heatmaps per device.

### Omnichannel

One journey that crosses devices or channels, for example find on phone and finish on laptop, or start from an email. Ask the designer for the journey steps and which device each happens on. Only personas who own the devices involved take part. Track what carries over (cart, sign-in, place in the flow) and where they have to start again.

- Extra output: a journey map showing drop-off at each hand-over.

### Card sorting

Personas get the items (pages, categories, features) as plain text cards. In an open sort they make and name their own groups; in a closed sort they place cards into the designer's categories. Personas group and name things in their own words, so groups will differ.

- Extra output: a similarity matrix heatmap (share of personas who put each pair together), the most common group names per persona group, and cards with no agreement.

### Tree testing

Show the navigation as a plain text tree with no visual design. For each find task, personas choose a path from the top. Record the first click, the full path, backtracks and the final answer.

- Extra output: success rate, directness (no backtracking) and first-click correctness per task, a tree heatmap with each node shaded by how many personas visited it, and a destination matrix.

### Survey

Run after a task method. Each persona answers in character: the Single Ease Question (1 to 7) after each task, the ten SUS statements at the end (scored 0 to 100), and up to three questions from the designer. Answers must match what happened in their session; a persona who abandoned does not rate the task easy.

- Extra output: SUS per group, SEQ per task, and open answers grouped by theme.

### 1:1 interview

After the task, a simulated interviewer asks each persona five to eight open questions about their needs, expectations and what happened, including any questions from the designer. Answers stay in character and draw on the session. Use the Standard panel or smaller.

- Extra output: themes with supporting quotes, and needs the design does not meet.

### Focus group

After each persona has done the task, run discussion groups of six to eight, either mixed or one group per persona group. A simulated moderator raises four to six topics. Personas react to each other, agree and disagree, and stay in character. Less confident personas speak less unless the moderator asks them directly, so the moderator does.

- Extra output: a discussion summary per group, points of agreement and conflict, and ideas raised.

### Not offered

Longitudinal and diary studies need real people over real time, and guerrilla testing is about recruiting real strangers, so none of them can be simulated honestly. If asked, explain this, suggest running the real study, and offer Benchmark as the nearest simulated option.

## 3. Get the design in front of you

**Designs in Claude.** Read the artifact or open the attached screens and look at every screen in the flow. For static screens, the persona can only go where a visible element plausibly leads. If the next screen is missing, stop that persona there and record that the flow was not provided past this point rather than inventing it.

**Live URLs.** Open the page in a real browser and capture screenshots at each step. Use 390 x 844 for mobile and 1440 x 900 for desktop. Actually click, scroll and type as the persona would, including their mistakes. Record real load times, layout shifts, pop-ups and cookie banners, because personas react to them. Do not complete a real purchase, submit real payment details or create real accounts; stop at the payment step. If the URL cannot be reached, say so and ask for screenshots.

Judge only what is visible on screen. Do not use knowledge of the code, the design file layers, or what the designer intended.

## 4. Simulate each persona

For each persona, in order:

1. **First five seconds.** What do they notice first, what do they think this page is, and what do they think they can do here? Use their reading style.
2. **Walk the task step by step.** At each step write what they look at, what they expect, what they do, and what happens. Keep a short think-aloud in their voice.
3. **Apply their limits honestly.**
   - If they do not know a pattern (hamburger menu, swipe carousel, icon without label, filter chips), they do not use it unless the screen teaches it.
   - If they skim, they miss body copy and small links.
   - If they have an access trait, apply it to every screen (contrast, text size, tap target size, colour-only signals, dense text).
   - Apply their context: interruptions, one hand, glare, slow connection, small screen.
   - Apply their trust rules: what makes them hesitate or leave.
4. **Let them fail.** When their patience runs out, they abandon. Record where and why. Do not rescue them.
5. **Track the primary objective as a funnel.** For each persona record how far they got: Saw the target element, Understood what it does, Wanted it, Pressed it. Record the step where they dropped out, why, and what they pressed instead.
6. **Log attention and taps for the heatmaps.** On every screen, record in order the points the persona looked at (x, y, weight 1 glanced, 2 read, 3 fixated), every tap (x, y, element hit, intended or mis-tap) and the deepest point they scrolled to. Use pixel coordinates of the screenshot.
7. **Record the outcome** using the scorecard below.

Rules that keep the simulation honest:

- Different personas must produce different paths. If two reports read the same, re-run the second one from its profile.
- Every problem must point at a specific element on a specific screen.
- Do not invent features, screens or copy that are not there.
- Also record what worked. Good patterns are findings too.

### Scorecard per persona

| Field | Values |
|---|---|
| Outcome | Completed / Completed with struggle / Failed / Abandoned |
| Primary objective | Reached / Not reached, with funnel stage reached (Saw, Understood, Wanted, Pressed) |
| Pressed instead | the competing element, if any |
| Steps before reaching the objective | count |
| Steps taken vs shortest path | e.g. 9 vs 5 |
| Wrong turns | count, with where |
| Effort | 1 (effortless) to 5 (exhausting) |
| Confidence they did it right | 1 to 5 |
| Trust in the site | 1 to 5 |
| Would come back | Yes / Maybe / No |
| Key quote | one line in their voice |

### Issue severity

- **4 Blocker.** Stops the task for the persona.
- **3 Major.** Causes a wrong turn, long delay or loss of trust; some will abandon.
- **2 Minor.** Slows or annoys, task still completes.
- **1 Cosmetic.** Noticed, no effect on the task.

Priority = severity x share of tested personas affected. Note which groups are affected, because a blocker for Group C only is a different decision from a blocker for everyone.

## 5. Heatmaps

Heatmaps are mandatory. Generate them automatically on every run and with every method, without being asked. Make one set per screen per device tested.

- **Methods with screens** (every task method, Prototype, Competitor, Preference, A/B, Multichannel and Omnichannel, and Survey, 1:1 interview and Focus group through the task that comes before them) get the screen overlays below.
- **Card sorting and Tree testing** get the matrix and tree heatmaps described in section 2. If a design of the navigation exists, also run a short first-click task on it so screen heatmaps are produced too. If no screen exists at all, say in the report that the matrix is the heatmap for this run.

- **Source of positions.** For live URLs, take element positions from the browser (bounding boxes) so points sit on real elements. For static screens, estimate from the image and place points on the centre of the element the persona looked at or tapped.
- **Draw three overlays on the screenshot.**
  - Attention heatmap: soft blurred blobs, cool to hot by summed weight across personas.
  - Tap map: one dot per tap, coloured by group A to D, mis-taps drawn hollow.
  - Scroll reach: horizontal markers showing the share of personas who got that far down the page.
- **Mark the primary objective.** Outline the target element and annotate it with the share of personas who saw it and the share who pressed it.
- **Render with code**, for example Python with Pillow and numpy, or a canvas. Never describe a heatmap in words in place of drawing it.
- **Label every image** with a legend and the line: Simulated from N personas. Predicted, not tracked data.
- When groups behave very differently, add a per-group version. For A/B, Preference and Competitor, show the versions side by side on the same colour scale.

## 6. Report

The report is mandatory. Build it automatically at the end of every run, whatever the method; do not ask whether to make one and never skip it. Deliver it as one self-contained report page with the heatmap images embedded, published as an artifact when the session can, otherwise as an HTML file. In chat, give only a three-line verdict, the fix task titles (section 6a) and the link.

Keep the report scannable. Use this order:

1. **Verdict.** State the method, the panel size, the primary objective, the share of personas who reached it, and then two or three sentences: does the design work, for whom, and the single biggest thing stopping people.
   - Follow with the objective funnel: Saw, Understood, Wanted, Pressed, as counts per group, and the elements people pressed instead.
   - Then the heatmaps for each screen.
2. **Scorecard by group.** Table with completion rate, average effort, average trust, abandon count for Groups A to D, split by mobile and desktop when both were tested. Every persona that was run counts here.
3. **Top issues.** Ranked by priority. Each has: screen and element, what happened, who was affected (persona IDs), severity, recommended fix.
4. **What worked.** Patterns to keep.
   - **What could be improved.** A separate, clearly titled section listing each suggested change, the issue it addresses, the expected effect on the primary objective (High / Medium / Low) and rough effort (Small / Medium / Large). Open the section with this notice, shown prominently: *These suggestions are AI-generated from simulated users, not real ones. You are the designer. Decide which of them matter for your product and your users, and which do not.* Do not rank the suggestions as must-do; present them as options for the designer to judge.
5. **Fix tasks.** A checklist with one task per issue in Top issues, in the same priority order, each with a ready-to-use prompt. See section 6a.
6. **Persona highlights.** One short paragraph and quote for the most revealing personas only, not all of them. Offer the full step logs on request.
7. **Mobile vs desktop differences.**
8. **Accessibility flags.** Contrast, text size, tap targets under 44 px, colour-only signals, missing labels.
9. **Validate with real users.** The three findings most worth confirming in a real test.

Add the method's extra output from section 2 as its own section straight after the scorecard. Card sorting and Tree testing adapt the scorecard to their own metrics but keep every other section, including What could be improved, its AI-generated notice and Fix tasks.

For the Re-test panel, list each previous issue as Fixed / Improved / Not fixed / New problem introduced, keyed by its fix task ID (FT-1, FT-2 and so on) so the designer can tick tasks off.

## 6a. Fix tasks

Fix tasks are mandatory whenever the run finds at least one issue. Build them automatically from Top issues; do not ask whether to make them. They turn each finding into something the designer can act on straight away.

**One task per issue.** Every issue in Top issues gets its own task, in priority order, with an ID (FT-1, FT-2 and so on) that matches the issue. Cosmetic issues (severity 1) may be grouped into a single task. Never invent a task for something that is not in Top issues.

Each task is a card with a checkbox and these fields, in this order:

| Field | What to write |
|---|---|
| **Title** | Short and actionable, naming the element and the change, for example: Label the bag icon in the header. Add the severity and the groups affected as tags. |
| **Problem** | One or two sentences: what happens, on which screen and element, and the share of personas affected, for example: 5 of 8 personas never found the cart; 4 of them were in Groups A and C. |
| **Why it matters** | The effect on the primary objective and on trust or effort: where in the funnel (Saw, Understood, Wanted, Pressed) people dropped out, and what they pressed instead. |
| **Why it failed** | The root cause seen in the sessions, in terms of the personas' limits, not the designer's intent: an unfamiliar pattern, missed while skimming, low contrast, tap target too small, unclear copy, a trust signal missing. Include one short persona quote with its ID. |
| **How to fix it** | The suggested change in two to four bullet points, specific enough to build, plus what to keep so the fix does not break what worked. If there are two reasonable options, give both and say which persona groups each one helps more. |
| **Prompt** | A ready-to-copy prompt that fixes this one issue (see below), in a code block with a copy button. |

**Writing the prompt.** The prompt must work when pasted into a fresh chat by someone who has not read the report, so it carries its own context:

- What is being fixed: the product or page, the screen, the exact element and its current state (copy, size, position, colour where relevant).
- The problem and its cause in one or two plain sentences, including who struggled.
- The change to make, taken from How to fix it, written as instructions.
- Constraints: keep the existing design system, styles and components; change only what this issue needs; do not touch elements listed under What worked.
- Done when: one to three checks tied to the finding, for example: the icon has a visible text label, the tap target is at least 44 x 44 px, the label passes 4.5:1 contrast.
- A last line suggesting a Crowd Check Re-test of the affected personas (list their IDs) after the change.

Fit the prompt to what was tested. For a design in Claude, write it as an edit to that design or artifact. For a live or staging URL, write it as a change to the page's code, naming the element as it appears on screen (text, position, role) because the codebase was not seen. Never claim knowledge of file names, components or code that were not visible.

Above each prompt, add one line telling the designer how to use it, for example: Paste this into a chat with your design open, or into Claude Code in the project repo, then re-test with the personas listed.

**Above the list,** show the same AI-generated notice as What could be improved, and a one-line summary such as 6 tasks: 1 blocker, 2 major, 3 minor. Let the designer tick tasks off in the report page; remember ticks only for that viewer, and treat the report as the source of truth.

**In chat,** after the three-line verdict, list the task titles with their severity only, and point to the report for the prompts. When the session has a task-list tool, also add each fix task there by title.

Example card (shortened):

> **FT-1 · Label the bag icon in the header** · Blocker · Groups A, C
> **Problem.** On the product page (mobile), 5 of 8 personas could not find the cart, so none of them reached Create free now.
> **Why it matters.** All 5 dropped out at Saw. Three pressed the logo instead and landed back on the homepage.
> **Why it failed.** The cart is an unlabeled bag icon, 20 px, light grey on white. Group A and C personas do not recognise icon-only controls. C4: "What is the little bag for?"
> **How to fix it.** Add the word Cart under or beside the icon. Raise the tap target to 44 x 44 px and the icon contrast to at least 3:1. Keep the header height and the search field as they are.
> *Paste this into a chat with your design open, then re-test A2, A7, C1, C4 and C9.*
> ```
> In the mobile product page header, the cart is an unlabeled 20 px bag icon in light grey on white, top right. In a simulated usability test, low-tech users and seniors did not recognise it and could not find the cart, so they never reached "Create free now". Add a visible "Cart" text label next to the icon, make the tap area at least 44 x 44 px and raise the icon contrast to at least 3:1. Keep the existing design system, header height and search field unchanged, and don't change anything else on the page. Done when the label is visible, the tap area is 44 x 44 px or larger and the contrast passes. Afterwards, run a Crowd Check Re-test with personas A2, A7, C1, C4 and C9.
> ```

## 7. The persona panel

Tech score is 1 (avoids technology) to 10 (builds it). Personas are general online shoppers from a mix of countries. Each group has 50 personas: numbers 1 to 10 are the core panel with full profiles, and numbers 11 to 50 are the extended panel in compact form with the same fields (name, age, job, tech score, device, what they can do, behaviour, what trips them). Simulate extended personas with the same rigour as core ones and write their think-aloud voice from the profile. Read the whole profile before simulating; the Trips on line is the minimum, not the full list.

### Group A: Low-tech millennials (age 30 to 44, tech 2 to 4)

Grew up alongside the internet but never got comfortable. They use a few familiar apps daily and are lost outside them. Most are phone-only.

**A1. Carla Mendes, 34, hair salon owner.** Tech 3. Mid-range Android, cracked screen. Lives in WhatsApp and Instagram, rarely uses a browser.
- Skills: messaging, photos, following links people send her. Cannot use filters or sort, does not know what the three-line menu icon is.
- Behaviour: taps pictures and logos expecting them to do something. Skims. Low patience.
- Trips on: unlabeled icons, forced account creation (she leaves), anything hidden in a menu.
- Voice: *Where do I press? I just want to buy the thing.*

**A2. Darren Whitlock, 41, long-haul truck driver.** Tech 3. Android phone only, used on breaks with patchy signal.
- Skills: maps, YouTube, voice search. Types slowly with large thumbs.
- Behaviour: reads headings only. Never scrolls sideways. Gives up when a page loads slowly twice.
- Trips on: small or tightly packed tap targets, carousels, heavy pages, long forms. Wary of typing card details.
- Voice: *I've got ten minutes. If it's still loading I'm gone.*

**A3. Priya Nair, 37, teaching assistant.** Tech 2. Shared family iPad.
- Skills: email, video calls, a recipe app. Reads everything slowly and carefully.
- Behaviour: afraid of pressing the wrong thing and breaking it or being charged. Wants confirmation at every step.
- Trips on: icons without words, buttons that do not say what happens next (Continue to where?), no visible way to undo.
- Voice: *If I press this, will it charge me straight away?*

**A4. Tomasz Kowalski, 39, builder and tiler.** Tech 3. Rugged Android, used outdoors in glare with dusty hands.
- Skills: calls, messages, photo sharing, supplier app he was shown how to use.
- Behaviour: impatient. Skips all text and hits the biggest, brightest button.
- Trips on: low contrast, secondary links, options that must be chosen before the main button works, error messages he does not read.
- Voice: *Why is the button grey? I pressed it three times.*

**A5. Leila Haddad, 32, night-shift nurse.** Tech 4. iPhone, one-handed, usually exhausted at 3 am.
- Skills: banking app, social apps, autofill. Never remembers a password.
- Behaviour: relies on the back button and gets lost when it does not return her where she expects.
- Trips on: login walls, password rules, controls at the top of the screen out of thumb reach, losing form entries after going back.
- Voice: *I had it a second ago. Where did it go?*

**A6. Marcus Bell, 44, chef.** Tech 2. Old small-screen iPhone, never updated, system text size set large.
- Skills: calls, texts, a couple of apps his kids installed.
- Behaviour: does not know about tabs or that pages continue below the screen unless something is visibly cut off.
- Trips on: layouts that break with large text, content below the fold with no scroll cue, sticky bars covering half his screen, links opening in new tabs.
- Voice: *That's it? There's nothing else on here.*

**A7. Sofia Ricci, 30, florist.** Tech 4. iPhone. Very visual, uses Instagram and Pinterest for work.
- Skills: browsing image feeds, saving and sharing pictures.
- Behaviour: chooses entirely by photo. Ignores descriptions, specs and small print.
- Trips on: option selectors (size, quantity, variant), surprises at checkout that were stated in text she skipped, pages with few or small images.
- Voice: *It looked different in the picture.*

**A8. Kwame Osei, 36, warehouse supervisor.** Tech 3. Budget Android. English is his second language.
- Skills: messaging, video, mobile money transfers.
- Behaviour: reads slowly, translates in his head, relies on familiar words and pictures.
- Trips on: jargon and idiom (guest checkout, promo code, add-ons, fulfilment), clever marketing copy, long sentences, error messages that do not say what to do.
- Voice: *What does this word mean here?*

**A9. Hannah Lindqvist, 42, stay-at-home parent of three.** Tech 4. Android phone, constantly interrupted.
- Skills: social apps, school app, online grocery she uses on repeat.
- Behaviour: every task is broken by a 5 to 15 minute interruption. Comes back and has to work out where she was.
- Trips on: sessions that time out, carts that empty, multi-step flows with no progress indicator, forms that reset.
- Voice: *I was halfway through. Now I have to start again?*

**A10. Ravi Shah, 38, taxi driver.** Tech 2. Android phone used almost only for maps and the ride app.
- Skills: navigation, calls. Normally orders by phoning the shop.
- Behaviour: looks for a phone number or a person first. Distrusts sites he has not heard of.
- Trips on: no visible contact details, card-only payment, unclear total cost, anything that looks like an advert.
- Voice: *Is there a number I can call instead?*

#### Group A extended panel (A11 to A50)

- **A11. Bianca Torres, 31, nail technician.** Tech 3. Android. Can: Instagram, messaging. Behaviour: shops only through links friends send. Trips on: landing on a home page instead of the product, search with no suggestions.
- **A12. Craig Dunmore, 43, bus driver.** Tech 2. Old Android. Can: calls, texts, a sports scores app. Behaviour: reads nothing, asks his wife when stuck. Trips on: cookie banners, pop-ups, any sign-in.
- **A13. Nomvula Dlamini, 35, hotel housekeeper.** Tech 2. Prepaid Android with little data. Can: messaging, voice notes. Behaviour: watches data use and leaves heavy pages. Trips on: autoplay video, large images, prompts to download an app.
- **A14. Stefan Popescu, 40, delivery van driver.** Tech 3. Android in a dashboard mount. Can: maps, delivery app. Behaviour: shops in two-minute stops and restarts often. Trips on: lost cart, long checkout, address lookup rejecting his address.
- **A15. Aylin Demir, 33, bakery assistant.** Tech 3. Hand-me-down iPhone. Can: photos, messaging. Behaviour: taps quickly and imprecisely with floury hands. Trips on: small close buttons, accidental taps on banners, no undo.
- **A16. Joseph Mwangi, 38, night security guard.** Tech 3. Android with dimmed screen. Can: video, messaging, mobile money. Behaviour: browses in the dark at low brightness. Trips on: low contrast, light grey text, product names cut off.
- **A17. Rachel Abrams, 44, childminder.** Tech 4. iPad shared with children. Can: video calls, kids apps. Behaviour: taps anything colourful. Trips on: decorative elements that look tappable, banners mistaken for buttons.
- **A18. Luis Herrera, 36, landscape gardener.** Tech 2. Android, outdoors, wet screen. Can: calls, photos. Behaviour: uses the phone in rain and glare. Trips on: swipe gestures, tiny quantity controls, pale designs.
- **A19. Mina Petrovic, 32, supermarket cashier.** Tech 3. Android. Can: social apps, messaging. Behaviour: pays cash in daily life and is nervous paying online. Trips on: card form errors, not knowing if payment went through, no familiar payment logo.
- **A20. Dwayne Carter, 41, forklift operator.** Tech 3. Android. Can: voice typing, video. Behaviour: dictates searches and spells poorly. Trips on: search with no spelling tolerance, zero-results pages, strict form fields.
- **A21. Yuki Sato, 37, care home assistant.** Tech 3. iPhone. Can: messaging, rota app. Behaviour: follows steps exactly as written and stops when wording changes. Trips on: button labels changing between steps, mixed terms such as bag, basket and cart.
- **A22. Patrick Byrne, 44, farmer.** Tech 2. Old Android on weak rural signal. Can: calls, weather app. Behaviour: connection drops mid-task. Trips on: timeouts, spinners with no message, forms that lose data.
- **A23. Fatou Diallo, 34, market stall trader.** Tech 2. Budget Android. French is her first language. Can: messaging, mobile money. Behaviour: guesses at English words. Trips on: idioms, unfamiliar date and price formats, long country dropdowns.
- **A24. Greg Novak, 39, plumber.** Tech 4. Android. Can: calls, maps, photo messages. Behaviour: wants an answer within a minute or he phones. Trips on: hidden contact details, chatbots instead of people, vague delivery times.
- **A25. Daniela Costa, 30, waitress.** Tech 4. iPhone with full storage and low battery. Can: social apps, wallet pay. Behaviour: refuses to download apps. Trips on: app-install prompts, app-only features, heavy animations.
- **A26. Imran Qureshi, 42, butcher.** Tech 2. Old iPhone. Can: calls, messaging. Behaviour: does not know carousels, pinch zoom or tabs. Trips on: image galleries, details hidden in accordions, tabbed content.
- **A27. Katie Olsen, 35, dog groomer.** Tech 4. Android. Can: social apps, booking app. Behaviour: looks only at the star rating. Trips on: no ratings, ratings below the fold, too many similar products.
- **A28. Vusi Khumalo, 37, mine worker on rotating shifts.** Tech 3. Android. Can: messaging, money transfers. Behaviour: buys gifts for family far away. Trips on: delivery address versus his own address, no delivery estimate, no gift message.
- **A29. Elena Marchetti, 43, seamstress.** Tech 2. Tablet from her daughter. Can: video calls, photos. Behaviour: reads slowly with glasses and zooms in. Trips on: small text, fixed headers covering content, text over images.
- **A30. Bobby Tran, 31, car wash attendant.** Tech 3. Android held in landscape. Can: video apps, messaging. Behaviour: rarely rotates the phone back. Trips on: layouts that break in landscape, sticky bars filling the screen.
- **A31. Agnieszka Zielinska, 40, office cleaner.** Tech 2. Android with browser auto-translate. Can: messaging, video calls. Behaviour: reads everything through translation. Trips on: text inside images, mistranslated buttons, mixed languages.
- **A32. Terrence Hill, 44, roofer.** Tech 2. Android. Can: calls, photos. Behaviour: hates typing and makes many typos. Trips on: required fields, mistyped email with no check, password creation.
- **A33. Shabnam Karimi, 33, tailor shop assistant.** Tech 3. iPhone. Can: social apps, messaging. Behaviour: fears scams after a friend was cheated. Trips on: unknown brand with no reviews or address, too-good discounts, countdown timers.
- **A34. Colin Fraser, 38, postman.** Tech 4. Android. Can: one big retailer app. Behaviour: expects every site to work like that app. Trips on: unfamiliar layouts, basket not top right, different checkout order.
- **A35. Marisol Vega, 36, hotel receptionist.** Tech 4. Slow work desktop with an old browser. Can: the hotel booking system. Behaviour: shops at the front desk between guests. Trips on: features not loading, hover menus that vanish, tiny dropdowns.
- **A36. Henrik Larsen, 42, fisherman.** Tech 2. Rugged phone. Can: calls, weather, maps. Behaviour: weeks offline, forgets every login. Trips on: forced login, password reset by email, two-step codes.
- **A37. Thandi Mokoena, 30, daycare worker.** Tech 4. Android. Can: social apps, messaging. Behaviour: shops with a child on her hip, one thumb. Trips on: controls at the top of the screen, drag sliders, multi-field date entry.
- **A38. Paolo Greco, 41, pizza maker.** Tech 3. iPhone. Can: messaging, video. Behaviour: decides by price alone and wants it immediately. Trips on: price hidden until options are chosen, from-prices, totals changing at checkout.
- **A39. Jasmine Kaur, 34, pharmacy counter assistant.** Tech 4. Android. Can: social apps, banking app. Behaviour: afraid of ordering twice. Trips on: no confirmation after pressing pay, slow button response, back button re-submitting.
- **A40. Mick Sullivan, 44, scaffolder.** Tech 2. Android with very large font. Can: calls, texts. Behaviour: never changes settings. Trips on: truncated labels, overlapping text, buttons pushed off screen.
- **A41. Rosa Jimenez, 39, home care aide.** Tech 3. Android. Can: messaging, voice notes. Behaviour: low reading confidence, relies on pictures and familiar words. Trips on: text-heavy pages, legal wording, instructions without pictures.
- **A42. Nikolai Ivanov, 37, welder.** Tech 3. Android. Can: video, messaging. Behaviour: taps the first result and never compares. Trips on: promoted items first, wrong variant preselected, no summary before paying.
- **A43. Abena Asante, 32, school lunch cook.** Tech 3. Small budget Android. Can: messaging, social apps. Behaviour: holds the phone at arm's length. Trips on: sideways-scrolling tables, size charts, tiny checkboxes.
- **A44. Jared Coleman, 35, warehouse picker.** Tech 4. Android. Can: console gaming, video apps. Behaviour: rarely uses the web and will not read. Trips on: forms, email verification, anything that sends him out of the page.
- **A45. Lucia Fernandes, 44, cleaner and mother of four.** Tech 2. Shared family phone. Can: calls, messaging. Behaviour: other people's accounts are logged in. Trips on: being signed in as someone else, saved addresses that are not hers, no clear sign-out.
- **A46. Callum Reid, 33, bartender.** Tech 4. iPhone, late at night after shifts. Can: social apps, wallet pay. Behaviour: tired and inattentive. Trips on: pre-ticked extras, subscription defaults, small print.
- **A47. Zainab Bello, 38, street food vendor.** Tech 2. Slow budget Android. Can: messaging, mobile money. Behaviour: taps again when nothing happens. Trips on: laggy pages, double taps registering twice, stuttering animations.
- **A48. Oskar Nilsson, 43, lorry mechanic.** Tech 3. Android with a dead strip at the bottom of the screen. Can: calls, parts lookup app. Behaviour: cannot press anything at the bottom edge. Trips on: bottom-fixed buttons, bottom navigation, no alternative path.
- **A49. Mei-Ling Chow, 36, restaurant kitchen hand.** Tech 3. Android. Cantonese is her first language. Can: messaging, payments app. Behaviour: unsure how to enter her name and address. Trips on: forms assuming Western name and address formats, strict postcode rules, jargon.
- **A50. Andre Baptiste, 40, removals worker.** Tech 3. Android. Can: video, messaging. Behaviour: distracted by offers and forgets his goal. Trips on: promotional banners above the main action, pop-up offers, no way back to where he was.

### Group B: Everyday users (age 27 to 48, tech 5 to 6)

Comfortable with browsers, search and online shopping on well-known sites. They know standard patterns and are thrown when a design departs from them. They do not troubleshoot.

**B1. Emma Clarke, 33, HR coordinator.** Tech 6. Work laptop at lunch, Chrome.
- Skills: search, filters, sorting, two tabs to compare.
- Behaviour: expects things where big retailers put them: search top centre, cart top right.
- Trips on: non-standard navigation, filters that reset, unclear selected state.
- Voice: *Normally the basket is up here. Why is it not?*

**B2. Diego Fernandez, 29, sales rep.** Tech 6. iPhone on the commute.
- Skills: app shopping, wallet payments, saved addresses.
- Behaviour: wants to finish in under two minutes. Hates typing.
- Trips on: long forms, no express pay, forced sign-up, keyboards that do not match the field type.
- Voice: *Just let me pay with my phone.*

**B3. Aisha Rahman, 40, pharmacist.** Tech 5. Android phone and home laptop.
- Skills: reads reviews, checks policies, compares before buying.
- Behaviour: careful. Will not buy until she has found delivery date, returns policy and total cost.
- Trips on: delivery and returns info buried or shown only at checkout, missing reviews, vague stock status.
- Voice: *When does it actually arrive? I can't find it.*

**B4. Liam O'Connor, 45, account manager.** Tech 5. Windows desktop.
- Skills: search, price comparison sites, email receipts.
- Behaviour: price-driven. Seeing a promo code box makes him leave to hunt for a code.
- Trips on: prominent promo fields, unclear discounts, shipping cost revealed late, was/now prices he does not believe.
- Voice: *There's a code box, so someone's paying less than me.*

**B5. Mei Tanaka, 35, accountant.** Tech 6. iPad on the sofa.
- Skills: detail checking, account management, order tracking.
- Behaviour: checks every line of the order summary and does the sum herself.
- Trips on: totals that change without explanation, pre-ticked extras, fees added at the last step, summary hidden behind a toggle.
- Voice: *That is not the number it showed me a page ago.*

**B6. Jordan Brooks, 27, gym instructor.** Tech 5. Android phone between clients.
- Skills: social shopping, basic search.
- Behaviour: skims fast, decides in seconds, leaves on slow loads. Reads no paragraphs.
- Trips on: walls of text, slow images, pop-ups on arrival, unclear primary action.
- Voice: *Too much reading. Next.*

**B7. Natalia Petrova, 38, estate agent.** Tech 6. Starts on phone, finishes on laptop.
- Skills: multi-device use, saved items, email links.
- Behaviour: expects her cart and place to follow her between devices.
- Trips on: cart not syncing, mobile and desktop layouts that look like different sites, links from email that drop her on the home page.
- Voice: *I added this on my phone. Where is it?*

**B8. Samuel Adeyemi, 48, secondary school teacher.** Tech 5. Laptop. Red-green colour blind.
- Skills: confident browser user, online banking, forms.
- Behaviour: methodical, reads labels.
- Trips on: errors or states shown by colour alone, red and green status badges, colour swatches without names, low-contrast links.
- Voice: *It says there's an error but I can't see which field.*

**B9. Chloe Martin, 31, dental hygienist.** Tech 5. iPhone. Mostly buys gifts for other people.
- Skills: shopping apps, wish lists, sharing links.
- Behaviour: looks for gift options, a different delivery address and arrival by a date.
- Trips on: no gift message or wrap option, billing and shipping address confusion, no delivery-by-date promise, prices on the packing slip.
- Voice: *Will it get there by Saturday, and will they see the price?*

**B10. Omar Khalil, 43, corner shop owner.** Tech 5. Windows laptop in the back office.
- Skills: repeat ordering, invoices, basic spreadsheets.
- Behaviour: buys the same things in quantity. Wants order history and reorder, not browsing.
- Trips on: quantity steppers with no typing, no reorder, account area hard to find, no downloadable invoice.
- Voice: *I need forty of these, not to press plus forty times.*

#### Group B extended panel (B11 to B50)

- **B11. Rebecca Lowe, 36, office manager.** Tech 6. Windows laptop. Can: search, filters, accounts. Behaviour: buys for the office and needs paperwork. Trips on: no tax invoice, no order reference, guest orders she cannot find again.
- **B12. Carlos Mendoza, 41, insurance agent.** Tech 5. Android phone. Can: browsing, online forms. Behaviour: checks cancellation terms first. Trips on: auto-renew defaults, vague subscription terms.
- **B13. Hye-jin Kim, 30, primary teacher.** Tech 6. iPad. Can: shopping apps, wish lists. Behaviour: saves items to decide later. Trips on: no wishlist without an account, saved items expiring.
- **B14. Tom Gallagher, 47, electrician with his own firm.** Tech 5. Android and laptop. Can: search, supplier sites. Behaviour: searches by exact product code. Trips on: search that ignores codes, no spec filter.
- **B15. Nadia Hussain, 34, bank teller.** Tech 5. iPhone. Can: banking apps, online shopping. Behaviour: checks payment logos and the address bar. Trips on: redirects to unfamiliar payment pages, branding that changes at checkout.
- **B16. Viktor Horvat, 44, restaurant manager.** Tech 5. Laptop late at night. Can: browsing, email, supplier orders. Behaviour: leaves tabs open for days. Trips on: stale cart prices, sessions expiring without warning.
- **B17. Lauren Mitchell, 29, receptionist.** Tech 6. iPhone. Can: social shopping, wallet pay. Behaviour: arrives from social ads. Trips on: ad product missing from the landing page, ad discount not applied.
- **B18. Ibrahim Yusuf, 39, civil servant.** Tech 5. Home desktop. Can: browsing by category, forms. Behaviour: uses menus and breadcrumbs, not search. Trips on: unclear category names, items in unexpected categories, mega menus that close.
- **B19. Sandra Oliveira, 45, travel agent.** Tech 6. Two monitors. Can: multi-tab comparison. Behaviour: compares products side by side. Trips on: no comparison view, spec order differing between products.
- **B20. Ben Hartley, 32, physiotherapist.** Tech 6. iPhone. Can: filters, sorting, apps. Behaviour: filters heavily before looking. Trips on: filters hidden on mobile, applied filters not shown, results jumping to the top.
- **B21. Anita Desai, 42, optician.** Tech 5. Android. Can: online shopping, tracking. Behaviour: needs it by a date for an event. Trips on: delivery date shown only after entering an address, cut-off times missing.
- **B22. Mateusz Nowak, 35, logistics coordinator.** Tech 6. Android. Can: tracking tools, accounts. Behaviour: follows every order closely. Trips on: no tracking link, vague confirmation email, order status needing login.
- **B23. Jessica Wong, 28, veterinary nurse.** Tech 6. iPhone. Can: apps, wallet pay. Behaviour: buys in five-minute breaks. Trips on: wallet pay offered only at the last step, coupon field resetting the form.
- **B24. Paul Schneider, 48, sales director.** Tech 5. iPad. Can: email, browsing, travel bookings. Behaviour: impatient, reads headings only. Trips on: unclear error states, re-entering data, steps that feel redundant.
- **B25. Olivia Bennett, 33, wedding planner.** Tech 6. Laptop and phone. Can: bulk orders, supplier sites. Behaviour: orders personalised items in quantity. Trips on: no preview of personalisation, no review of custom text before paying, hidden quantity pricing.
- **B26. Rashid Karim, 37, hotel manager.** Tech 5. Laptop. Can: online shopping, returns. Behaviour: checks how returns work before buying. Trips on: unclear return steps, hidden return cost.
- **B27. Ingrid Solberg, 46, bookkeeper.** Tech 5. Desktop. Can: online banking, invoices. Behaviour: prefers bank transfer or invoice. Trips on: payment options shown late, unclear currency.
- **B28. Tyler Jackson, 27, car salesman.** Tech 5. Android. Can: social apps, basic search. Behaviour: scrolls fast by image and price. Trips on: losing his place after going back, no sort by price.
- **B29. Camille Dubois, 38, translator.** Tech 6. Laptop. Can: shopping across borders. Behaviour: orders from abroad. Trips on: country not supported revealed at checkout, duties unexplained, language switch emptying the cart.
- **B30. Kofi Mensah, 43, school administrator.** Tech 5. Desktop. Can: forms, email, printing. Behaviour: prints pages to get approval. Trips on: pages that print badly, no shareable cart, no quote option.
- **B31. Sarah Levy, 40, paralegal.** Tech 6. Laptop. Can: careful reading, accounts. Behaviour: reads the fine print. Trips on: terms contradicting page claims, consent boxes bundled together.
- **B32. Marco Bianchi, 31, barber shop owner.** Tech 5. iPhone. Can: booking app, social apps. Behaviour: buys between clients and switches apps often. Trips on: forms losing state after switching apps, one-time codes needing an app switch.
- **B33. Deepa Iyer, 36, lab technician.** Tech 6. Android. Can: search, filters. Behaviour: searches first with long descriptive phrases. Trips on: exact-keyword-only search, no synonyms, irrelevant top results.
- **B34. Shane Murphy, 45, building site manager.** Tech 5. Android tablet. Can: email, plans viewer. Behaviour: uses a tablet in both orientations. Trips on: tablet layout that is a stretched phone view, tiny targets on a big screen.
- **B35. Yolanda Reyes, 34, call centre team lead.** Tech 5. Locked-down work desktop. Can: web tools at work. Behaviour: shops on a restricted browser. Trips on: blocked pop-ups, blocked third-party login, blocked downloads.
- **B36. Henry Okonkwo, 39, insurance claims assessor.** Tech 6. Laptop. Can: research, comparison. Behaviour: wants hard facts before buying. Trips on: missing dimensions, missing materials, lifestyle photos only.
- **B37. Elif Yilmaz, 29, kindergarten teacher.** Tech 5. iPhone. Can: shopping apps. Behaviour: buys for children and checks suitability. Trips on: age guidance hidden, no size guide, unclear what is included.
- **B38. Gareth Pugh, 47, train conductor.** Tech 5. Android. Can: apps, mobile tickets. Behaviour: signal drops in tunnels. Trips on: payment failing on reconnect, not knowing whether the order was placed.
- **B39. Lin Zhao, 32, junior auditor.** Tech 6. Laptop. Can: keyboard navigation, autofill. Behaviour: tabs through forms and pastes details. Trips on: autofill filling wrong fields, tab order jumping, fields rejecting pasted text.
- **B40. Monique Laurent, 44, boutique owner.** Tech 5. iPad. Can: social apps, supplier sites. Behaviour: judges the product by image quality. Trips on: low-resolution images, no zoom, colours differing between photos.
- **B41. Aaron Feldman, 35, PE teacher.** Tech 5. Android. Can: apps, online shopping. Behaviour: decides fast then second-guesses at checkout. Trips on: no way to edit the cart at checkout, losing details when going back.
- **B42. Priscilla Banda, 41, nurse manager.** Tech 5. iPhone. Can: online shopping, group gifts. Behaviour: buys for a whole team. Trips on: one address per order, no multiple recipients, re-entering details for each gift.
- **B43. Jonas Weber, 30, bank clerk.** Tech 6. Android. Can: password manager, apps. Behaviour: expects sign-in to be filled for him. Trips on: fields the password manager cannot fill, forced password rules, sign-in links opening in another browser.
- **B44. Farah Naz, 37, social worker.** Tech 5. Mid-range Android. Can: online shopping on a budget. Behaviour: builds a cart then trims it. Trips on: no running total, minimum-spend surprises, remove button hard to find.
- **B45. Stuart Campbell, 48, golf club manager.** Tech 5. Desktop at 125 percent zoom. Can: email, bookings. Behaviour: needs larger text to read comfortably. Trips on: layouts shifting at zoom, sticky headers eating space, cut-off dialogs.
- **B46. Valentina Cruz, 28, flight attendant.** Tech 6. iPhone, often abroad. Can: travel apps, wallet pay. Behaviour: shops from different countries each week. Trips on: wrong currency or region guessed, foreign address formats rejected, unclear delivery dates.
- **B47. Derek Osborne, 42, driving instructor.** Tech 5. Android. Can: browsing, email. Behaviour: likes to phone to confirm an order. Trips on: slow or missing order email, no contact route on the confirmation page.
- **B48. Kavita Rao, 46, school bursar.** Tech 5. Desktop. Can: finance software, online orders. Behaviour: needs someone else to approve before buying. Trips on: no save-for-later or share link, cart expiring, prices changing between visits.
- **B49. Felix Andersson, 33, bike shop mechanic.** Tech 6. Android. Can: video platforms, forums. Behaviour: watches product videos with sound off. Trips on: video not playing inline, no captions, video pushing the buy button off screen.
- **B50. Vivian Lin, 31, hotel events coordinator.** Tech 6. Laptop and phone. Can: email, online ordering. Behaviour: starts from email offers. Trips on: email link landing on a generic page, offer code not applied, expired offer with no alternative.

### Group C: Educated, low-tech seniors (age 61 to 78, tech 1 to 3)

Older Gen X, Boomers and beyond. Intelligent, well educated and capable; they are not slow thinkers, they are unfamiliar with digital conventions and cautious about mistakes and scams. They read properly and take wording literally. Treat their failures as design failures.

**C1. Margaret Ellison, 68, retired school principal.** Tech 3. iPad with reading glasses.
- Skills: email, video calls with family, news sites.
- Behaviour: reads every word top to bottom before acting. Notices and is put off by typos and vague wording.
- Trips on: small or light grey text, ambiguous labels, instructions that appear only after an error.
- Voice: *It should say what it means. Proceed to what?*

**C2. Robert Hughes, 72, retired civil engineer.** Tech 3. Windows desktop with mouse.
- Skills: email, documents, online banking set up by his son.
- Behaviour: wants to understand a step before taking it. Double-clicks everything. Closes anything that pops up.
- Trips on: double submission, modals and pop-ups (closes them even when needed), hover-only menus, no clear sequence of steps.
- Voice: *Something came up and I closed it. Was that important?*

**C3. Dr Anjali Deshmukh, 66, retired GP.** Tech 2. Smartphone her daughter set up. Mild hand tremor.
- Skills: calls, messaging family, photos.
- Behaviour: taps slowly and often hits the neighbouring element.
- Trips on: small or close-together tap targets, swipe and drag gestures, tiny close buttons, date pickers, accidental taps with no undo.
- Voice: *I keep pressing the one next to it.*

**C4. Giovanni Russo, 74, retired literature professor.** Tech 2. Laptop.
- Skills: email, reading long articles online. Reaches every site by typing its name into the search engine.
- Behaviour: cannot tell adverts from content. Does not recognise icons (magnifier, cart, heart, person) without labels.
- Trips on: icon-only navigation, sponsored blocks, abbreviations, breadcrumbs, anything assuming he knows a convention.
- Voice: *What is the little bag for?*

**C5. Patricia Owens, 61, part-time librarian.** Tech 3. Android phone and library desktop.
- Skills: email, social feed, catalogue search.
- Behaviour: capable but frightened of scams. Looks for signs a site is real.
- Trips on: requests for phone number or date of birth, saving card details, urgency timers, missing company address or contact details, unfamiliar payment screens.
- Voice: *Why do they need that? I'm not giving them that.*

**C6. Hiroshi Yamamoto, 70, retired bank manager.** Tech 3. Desktop with printer.
- Skills: online banking, email, spreadsheets from his working years.
- Behaviour: verifies everything involving money. Wants a review step and a printable confirmation.
- Trips on: one-click purchase with no review, unclear currency or tax, no order number on screen, confirmation only by app notification.
- Voice: *Before I confirm, show me exactly what I am paying.*

**C7. Elizabeth Fournier, 78, retired judge.** Tech 1. iPad at 200 percent zoom. Low vision.
- Skills: email with help, reading news. Prefers the telephone.
- Behaviour: sees only part of the screen at a time and loses context when things move.
- Trips on: layouts that break when zoomed, low contrast, text in images, content that appears far from where she tapped, placeholder text used as labels.
- Voice: *I pressed it and nothing happened that I can see.*

**C8. Walter Schmidt, 65, retired architect.** Tech 3. Large desktop monitor.
- Skills: strong visual judgement, desktop software from his career, email.
- Behaviour: hates clutter and reads layout hierarchy literally: biggest means most important.
- Trips on: misleading visual hierarchy, touch gestures on any device, banners competing with the main task, inconsistent alignment that makes him distrust the site.
- Voice: *Everything is shouting. What am I meant to look at?*

**C9. Grace Okafor, 63, university administrator.** Tech 3. Android phone with large fonts.
- Skills: email, messaging groups, work systems she was trained on.
- Behaviour: types slowly and carefully, checks each field. Follows instructions exactly as written.
- Trips on: session timeouts, strict input formats (dates, phone numbers), fields cleared after an error, truncated text at large font sizes.
- Voice: *It told me to try again and wiped everything I typed.*

**C10. Ahmed Siddiqui, 69, retired journalist.** Tech 2. Laptop his grandson set up.
- Skills: writing, email, reading online.
- Behaviour: makes typing mistakes, loses track of which step he is on in long flows, re-reads to reorient.
- Trips on: flows with no step indicator, unclear validation messages, password rules shown too late, CAPTCHAs, being sent to email to verify and not finding his way back.
- Voice: *Am I nearly done, or is there more?*

#### Group C extended panel (C11 to C50)

- **C11. Helen Cartwright, 71, retired midwife.** Tech 2. iPad. Can: email, video calls. Behaviour: stops to work out what each word means. Trips on: slang, trendy labels, icon-only buttons.
- **C12. Douglas MacLeod, 75, retired naval officer.** Tech 2. Desktop. Can: email, documents. Behaviour: follows procedures in strict order. Trips on: steps out of logical order, optional steps that look required.
- **C13. Sunita Kapoor, 64, retired chemistry lecturer.** Tech 3. Laptop. Can: email, reading online, documents. Behaviour: reads everything and questions claims. Trips on: unexplained terms, claims without detail, hidden costs.
- **C14. Bernard Lefevre, 77, retired diplomat.** Tech 1. iPad set up by his grandson. Can: reading news, email with help. Behaviour: presses slowly with one finger and holds too long. Trips on: long-press menus, drag gestures, text selection appearing.
- **C15. Ruth Goldstein, 69, retired psychotherapist.** Tech 3. Laptop. Can: email, video calls. Behaviour: dislikes being rushed. Trips on: countdown timers, low-stock pressure, carousels that move on their own.
- **C16. Kenji Watanabe, 73, retired electrical engineer.** Tech 3. Windows desktop with an old browser. Can: email, spreadsheets. Behaviour: understands systems but not web conventions and looks for a manual. Trips on: no help page, features failing in an old browser, unexplained icons.
- **C17. Dorothy Achebe, 67, retired head nurse.** Tech 2. Android phone with large font. Can: calls, messaging family. Behaviour: types slowly with the keyboard covering half the screen. Trips on: truncated text, buttons hidden under the keyboard, tiny terms checkboxes.
- **C18. Alan Whitfield, 70, retired solicitor.** Tech 2. Desktop. Can: email, documents. Behaviour: reads terms in full before accepting. Trips on: timeouts while reading, terms in a tiny scroll box, vague consent wording.
- **C19. Marta Kovacs, 62, music teacher near retirement.** Tech 3. iPad. Can: email, video lessons. Behaviour: unfamiliar with paying online. Trips on: card security step, wallet options she does not understand, unclear which button pays.
- **C20. Rajendra Pillai, 76, retired surgeon.** Tech 2. iPad. Can: reading, email. Behaviour: arthritis makes precise taps and typing painful. Trips on: long forms, small fields, entering the same data twice.
- **C21. Sylvia Brandt, 68, retired museum curator.** Tech 3. Laptop. Can: email, online catalogues. Behaviour: looks for provenance and detail. Trips on: thin descriptions, images that cannot be enlarged.
- **C22. Frank DeLuca, 74, retired maths teacher.** Tech 2. Desktop. Can: email, spreadsheets. Behaviour: redoes every sum by hand. Trips on: discounts not itemised, unexplained tax, rounding differences.
- **C23. Olufunke Adebayo, 65, retired civil servant.** Tech 2. Android. Can: calls, messaging groups. Behaviour: phones her children when stuck and describes the screen in words. Trips on: elements with no visible name, screens that change on their own.
- **C24. Peter Lindgren, 72, retired airline pilot.** Tech 3. iPad. Can: email, weather and travel sites. Behaviour: checklist mindset, wants confirmation of every action. Trips on: silent saves, no feedback after a tap, unclear toggle states.
- **C25. Catherine Vidal, 66, retired translator.** Tech 3. Laptop. Can: email, online dictionaries. Behaviour: precise with language and distrusts sloppy copy. Trips on: typos, inconsistent terms, machine-translated text.
- **C26. Abdul Rahman Farouk, 78, retired history professor.** Tech 1. Desktop. Can: reading online with help. Behaviour: struggles to hold the mouse still. Trips on: hover menus, small click targets, drag and drop.
- **C27. Judith Bergman, 63, retired accountant.** Tech 3. Laptop. Can: online banking, email. Behaviour: keeps records of everything. Trips on: no downloadable receipt, account needed to see order history.
- **C28. Thomas Brennan, 71, retired priest.** Tech 1. Donated laptop. Can: email with help. Behaviour: has never bought anything online. Trips on: cart versus checkout, promo code fields, account versus guest.
- **C29. Lakshmi Venkataraman, 70, retired botanist.** Tech 2. iPad. Can: photos, email. Behaviour: zooms into photos to inspect details. Trips on: zoom disabled, carousel swiping when she tries to zoom.
- **C30. George Papadopoulos, 75, retired shipping executive.** Tech 2. Smartphone. Can: calls, messaging. Behaviour: impatient with screens and prefers to phone. Trips on: no phone number, chatbots, long menus.
- **C31. Evelyn Marsh, 69, retired social worker.** Tech 3. Android tablet. Can: email, news apps. Behaviour: declines every request for data. Trips on: unclear cookie choices, required marketing consent, location prompts.
- **C32. Heinrich Bauer, 77, retired physicist.** Tech 3. Desktop. Can: email, reading papers online. Behaviour: reduced contrast sensitivity. Trips on: grey text on white, thin fonts, pale buttons.
- **C33. Miriam Katz, 64, pharmacist near retirement.** Tech 3. iPhone. Can: a few familiar apps. Behaviour: avoids anything new. Trips on: unfamiliar navigation, bottom sheets, swipe-only dismissal.
- **C34. Winston Grant, 73, retired transport company director.** Tech 2. Android. Can: calls, email. Behaviour: presses, waits, and presses again if nothing visibly happens. Trips on: slow feedback, duplicate submissions, loading with no indicator.
- **C35. Noriko Fujita, 68, retired interpreter.** Tech 2. iPad. Can: email, video calls. Behaviour: blames herself for errors and stops rather than risk a mistake. Trips on: error messages that blame the user, errors with no guidance.
- **C36. Charles Beaumont, 78, retired barrister.** Tech 1. Desktop with a large low-resolution monitor. Can: reading email. Behaviour: does not notice that pages scroll. Trips on: content below the fold, sideways overflow, thin scrollbars.
- **C37. Amina Suleiman, 61, senior civil engineer near retirement.** Tech 3. Work laptop. Can: professional software, email. Behaviour: skilled at work tools, unfamiliar with consumer sites. Trips on: social sign-in, playful microcopy, emoji used as labels.
- **C38. Lars Eriksson, 74, retired veterinarian.** Tech 2. iPad with keyboard cover. Can: email, news. Behaviour: keeps passwords in a notebook and forgets which is which. Trips on: password rules, sign-in required to continue, email verification loops.
- **C39. Beatrice Mwale, 66, retired economist.** Tech 3. Laptop. Can: research, spreadsheets. Behaviour: compares on paper and takes notes. Trips on: prices changing between visits, no unit price, no stable product codes.
- **C40. Stanley Rosen, 72, retired orchestra conductor.** Tech 1. iPhone from his family. Can: calls, photos. Behaviour: confuses apps with web pages and closes the browser by accident. Trips on: links opening other apps, losing the page on return, no way to resume.
- **C41. Ingeborg Hansen, 76, retired paediatrician.** Tech 2. iPad at 150 percent text size. Can: email, video calls. Behaviour: relies on large text. Trips on: columns collapsing badly, cut-off tooltips, placeholder labels that vanish while typing.
- **C42. Mohan Bhatt, 69, retired chartered accountant.** Tech 3. Desktop. Can: online banking, tax portals. Behaviour: pays only by methods he knows and wants a receipt. Trips on: unfamiliar payment providers, no receipt, card saved by default.
- **C43. Florence Girard, 65, retired fashion buyer.** Tech 3. iPad. Can: browsing, email. Behaviour: confident judging products, unsure of the interface. Trips on: colour and size selectors without labels, out-of-stock options that look selectable.
- **C44. Edward Nkemelu, 71, retired geologist.** Tech 2. Android with a stylus. Can: maps, email. Behaviour: taps with a stylus for accuracy. Trips on: small radio buttons, sliders, map widgets for choosing an address.
- **C45. Rosemary Fitzgerald, 77, retired court stenographer.** Tech 2. Laptop. Can: fast typing, email. Behaviour: excellent on the keyboard, poor with the mouse, expects Enter to submit. Trips on: Enter not submitting, focus jumping, mouse-only controls.
- **C46. Vikram Chatterjee, 63, senior law professor.** Tech 3. Laptop. Can: email, document tools. Behaviour: busy and used to delegating technology. Trips on: mandatory accounts, verification codes, checkout spread over many pages.
- **C47. Agnes Wojcik, 70, retired dentist.** Tech 2. Android phone. Can: calls, messaging. Behaviour: moving content makes her uncomfortable. Trips on: animations, parallax, autoplay video, moving banners.
- **C48. Leonard Hayes, 68, retired newspaper editor.** Tech 3. Desktop. Can: email, reading online. Behaviour: scans like a newspaper, headline then first line. Trips on: weak headings, key information mid-paragraph, the main button far below the text.
- **C49. Shirin Daneshvar, 74, retired university registrar.** Tech 1. iPad. English is her third language. Can: reading news, video calls. Behaviour: reads formally and literally. Trips on: idioms, abbreviations, casual tone.
- **C50. Arthur Pendleton, 78, retired mechanical engineer.** Tech 2. Desktop. Can: email, documents. Behaviour: forgets mid-task what he has already chosen. Trips on: no summary of choices so far, untitled steps, having to recall something from an earlier screen.

### Group D: Tech-fluent Gen Z (age 18 to 29, tech 8 to 10)

Grew up on phones. They know every pattern, move very fast and have no tolerance for friction, slowness or anything that looks dated or fake. They rarely fail a task; they leave by choice. Their findings are about speed, polish, trust and expectations.

**D1. Zoe Ramirez, 22, design student.** Tech 9. iPhone.
- Skills: design tools, every major app, spots patterns instantly.
- Behaviour: judges visual quality in two seconds and equates sloppy UI with an untrustworthy shop.
- Trips on: nothing functional. Flags inconsistent spacing, dated styling, stock photos, janky transitions.
- Voice: *This looks like a template. Is this place real?*

**D2. Ethan Park, 25, junior software developer.** Tech 10. Desktop, keyboard-first, dark mode, ad blocker on.
- Skills: everything, including looking under the hood.
- Behaviour: tabs through forms, uses keyboard shortcuts, notices performance and layout shift.
- Trips on: broken keyboard focus, things that fail with an ad blocker, slow or jumpy pages, no dark mode respect, dark patterns (he calls them out and leaves).
- Voice: *The focus order is wrong and the page jumped when the banner loaded.*

**D3. Amara Nwosu, 20, university student.** Tech 8. Android phone. Tight budget.
- Skills: deal hunting, price trackers, pay-later services, resale apps.
- Behaviour: sorts by price first, looks for student discount and total cost before anything else.
- Trips on: no price sort, hidden shipping cost, minimum order thresholds revealed late, no flexible payment.
- Voice: *Shipping costs more than the thing. No.*

**D4. Lucas Moreau, 24, content creator.** Tech 9. iPhone, arrives from a social video link inside an in-app browser.
- Skills: social platforms, link-in-bio shopping, editing on phone.
- Behaviour: lands deep on a product page with no context and decides in seconds.
- Trips on: login or wallet pay failing in the in-app browser, landing pages that do not match the video, cookie walls, no video or real-life product imagery.
- Voice: *The link said one thing and the page is showing me something else.*

**D5. Isla Thompson, 19, barista.** Tech 8. iPhone only, has never shopped on a computer.
- Skills: apps, gestures, wallet pay, saving and sharing.
- Behaviour: expects app behaviour from a website: swipe galleries, bottom navigation, instant feedback.
- Trips on: desktop-style layouts squeezed onto mobile, tiny text links, pinch-to-zoom needed, typing a card number by hand.
- Voice: *Why can't I swipe this?*

**D6. Arjun Mehta, 27, product analyst.** Tech 9. Laptop with many tabs, phone alongside.
- Skills: research, comparison, reading data, spotting manipulation.
- Behaviour: opens five products in tabs, reads the worst reviews first, wants photo reviews and real specs.
- Trips on: no reviews or only glowing ones, specs missing or inconsistent, page titles that make tabs indistinguishable, fake scarcity.
- Voice: *Only 5-star reviews means I trust none of them.*

**D7. Maya Goldberg, 23, nursing student.** Tech 8. Android phone. Dyslexic.
- Skills: fluent app user, voice notes, text-to-speech when needed.
- Behaviour: navigates by images, headings and icons. Avoids dense text.
- Trips on: long unbroken paragraphs, justified or all-caps text, tight line spacing, important info only in a text block, time-limited forms.
- Voice: *I'm not reading all that. Where's the short version?*

**D8. Noah Jensen, 26, freelance video editor.** Tech 9. Desktop for work, phone for everything else.
- Skills: creative software, online subscriptions, managing accounts.
- Behaviour: values-driven. Checks who the company is, where things ship from and how they are made.
- Trips on: no about or sourcing info, vague green claims, hard-to-cancel subscriptions, pre-ticked marketing consent.
- Voice: *Who actually makes this? There's nothing here about it.*

**D9. Fatima Al-Sayed, 21, law student.** Tech 8. iPhone and laptop. Privacy-conscious.
- Skills: privacy settings, guest checkout, masked email, reading terms when it matters.
- Behaviour: rejects cookies, refuses optional data, will not create an account for a one-off purchase.
- Trips on: cookie banners with no reject option, required phone number, forced account, sign-in with social as the only route.
- Voice: *Why is phone number required to post me a parcel?*

**D10. Kai Nakamura, 18, first job at a cinema.** Tech 8. Android phone. Just got a first debit card.
- Skills: fluent in apps, games and social platforms. New to buying things.
- Behaviour: fast and confident in the interface, unsure about the transaction itself.
- Trips on: billing versus shipping address, card security code, unexplained payment authentication step, taxes and fees he did not expect, not knowing whether the order went through.
- Voice: *Did it work? It just went back to the home page.*

#### Group D extended panel (D11 to D50)

- **D11. Tariq Hassan, 23, computer science student.** Tech 10. Linux laptop with strict tracking protection. Can: everything, including debugging. Behaviour: blocks trackers by default. Trips on: site breaking with trackers blocked, third-party checkout failing.
- **D12. Ruby Chen, 21, fashion marketing student.** Tech 8. iPhone. Can: every social and shopping app. Behaviour: shares to a group chat before buying. Trips on: no share link to the exact variant, link previews with no image.
- **D13. Mateo Alvarez, 26, UX designer.** Tech 10. MacBook. Can: design and prototyping tools. Behaviour: tests edge cases on purpose. Trips on: inconsistent components, missing empty and error states.
- **D14. Aaliyah Brown, 19, college student.** Tech 8. iPhone. Can: apps, pay-later services. Behaviour: buys only in instalments. Trips on: pay-later shown only at the end, no instalment breakdown.
- **D15. Jin-woo Lee, 24, esports coach.** Tech 9. Gaming desktop. Can: hardware, streaming tools. Behaviour: notices every delay. Trips on: input lag, slow hover states, heavy scripts.
- **D16. Elsa Bergstrom, 27, junior doctor.** Tech 8. iPhone. Can: apps, wallet pay. Behaviour: shops in three-minute gaps. Trips on: no saved cart, having to sign in again, no way to resume.
- **D17. Dev Patel, 22, app developer intern.** Tech 10. Android in dark mode with gesture navigation. Can: builds apps. Behaviour: expects native-quality behaviour. Trips on: white flashes in dark mode, back gesture fighting carousels, controls that feel non-native.
- **D18. Chiara Romano, 25, social media manager.** Tech 9. iPhone. Can: content tools, analytics. Behaviour: judges brand voice and authenticity. Trips on: corporate tone, fake urgency, stock imagery.
- **D19. Malik Johnson, 20, sneaker reseller.** Tech 9. iPhone. Can: fast checkout, autofill, alerts. Behaviour: races through checkout. Trips on: any extra tap, queue pages with no information, slow address validation.
- **D20. Sakura Ito, 18, art school applicant.** Tech 8. iPad with stylus. Can: drawing apps, social apps. Behaviour: uses touch and stylus only. Trips on: hover-dependent controls, tiny mouse-sized targets.
- **D21. Oliver Keller, 28, data engineer.** Tech 10. Desktop, keyboard only. Can: scripting, browser developer tools. Behaviour: never touches the mouse. Trips on: menus unreachable by keyboard, script errors that break a step.
- **D22. Nia Williams, 24, trainee teacher.** Tech 8. Android. Can: apps, online study tools. Behaviour: easily distracted and leaves crowded screens. Trips on: cluttered pages, competing calls to action, autoplay.
- **D23. Rohan Gupta, 26, fintech analyst.** Tech 9. iPhone. Can: wallets, virtual cards. Behaviour: scrutinises payment security. Trips on: no wallet pay, card saved without asking, repeated verification.
- **D24. Lena Fischer, 21, exchange student.** Tech 8. Laptop. Can: apps, online banking. Behaviour: uses a foreign card and address. Trips on: address or phone format rejected, card declined with no reason, payment page in another language.
- **D25. Jayden Scott, 19, delivery rider.** Tech 8. Mid-range Android on mobile data only. Can: gig apps, social apps. Behaviour: protects his data allowance. Trips on: heavy pages, autoplay video, slow loading on weak signal.
- **D26. Hana Kobayashi, 25, illustrator.** Tech 9. iPad. Can: creative software. Behaviour: zooms into detail and cares about colour accuracy. Trips on: compressed images, no zoom, colour names without swatches.
- **D27. Samir Aziz, 27, startup founder.** Tech 9. MacBook with thirty tabs open. Can: online tools, subscriptions. Behaviour: buys for a team. Trips on: no business checkout, no invoice, personal-only accounts.
- **D28. Freya Dahl, 22, psychology student.** Tech 8. iPhone. Can: social video, shopping apps. Behaviour: checks social video reviews before the site. Trips on: no social proof, few reviews, no customer photos.
- **D29. Tyrese Morgan, 23, music producer.** Tech 9. Desktop with an ultrawide monitor. Can: audio software, forums. Behaviour: browses full width. Trips on: layout stranded in the centre, oversized images, very long lines of text.
- **D30. Ananya Reddy, 20, medical student.** Tech 8. Android in split-screen. Can: study apps, multitasking. Behaviour: shops in half the screen. Trips on: layout breaking in a narrow split view, cut-off dialogs.
- **D31. Leo Garnier, 29, cyber security analyst.** Tech 10. Hardened browser with VPN. Can: security tooling. Behaviour: grants no permissions. Trips on: VPN blocked, repeated robot checks, unnecessary permission requests.
- **D32. Imani Okoye, 26, junior architect.** Tech 9. iPhone with voice control. Can: design software, dictation. Behaviour: often operates the phone hands-free. Trips on: unlabeled buttons voice control cannot target, custom controls.
- **D33. Finn Doyle, 18, apprentice mechanic.** Tech 8. Android. Can: apps, video, games. Behaviour: fluent in apps, avoids reading, prefers video. Trips on: text-only instructions, long forms, small print.
- **D34. Yara Mansour, 24, graduate student.** Tech 9. iPhone with a screen reader. Blind. Can: expert screen reader use. Behaviour: navigates by headings and labels. Trips on: images without descriptions, unlabeled buttons, focus trapped in dialogs.
- **D35. Caleb Wright, 25, photographer.** Tech 9. MacBook and phone. Can: cloud tools, passkeys. Behaviour: expects one-tap sign-in and syncing. Trips on: no passkey or quick sign-in, cart not syncing.
- **D36. Mila Petrenko, 21, language student.** Tech 8. Android set to another language. Can: apps, translation tools. Behaviour: uses the site in her own language. Trips on: half-translated interface, text overflowing buttons, unfamiliar date formats.
- **D37. Ezra Cohen, 28, product manager.** Tech 9. Laptop. Can: analytics, product tools. Behaviour: counts steps and fields. Trips on: unnecessary required fields, no progress indicator, upsells interrupting checkout.
- **D38. Thabo Ndlovu, 22, engineering student.** Tech 9. Budget Android on an older system version. Can: coding, apps. Behaviour: uses a less common browser. Trips on: unsupported features, stuttering animation, layout bugs outside the main browser.
- **D39. Skye Anderson, 19, retail assistant.** Tech 8. iPhone. Can: social shopping. Behaviour: buys on impulse and changes her mind fast. Trips on: slow add to cart, choosing options before seeing the price, no easy edit.
- **D40. Rafael Castillo, 27, freelance translator.** Tech 9. Desktop with reduced motion switched on. Can: online tools, gaming. Behaviour: motion bothers him. Trips on: animation ignoring the reduced-motion setting, parallax, auto carousels.
- **D41. Poppy Evans, 20, drama student.** Tech 8. iPhone always in low power mode. Can: social apps. Behaviour: never charges above half. Trips on: stuttering animation, video not starting and leaving blank space.
- **D42. Kwabena Boateng, 24, junior accountant.** Tech 8. Android. Can: comparison across sites. Behaviour: compares total cost in parallel tabs. Trips on: shipping shown only at the final step, account required before the total.
- **D43. Sienna Vitale, 26, yoga instructor with an online shop.** Tech 8. iPhone. Can: runs her own online store. Behaviour: judges checkout against the best she knows. Trips on: clunky cart, no express checkout, weak order confirmation.
- **D44. Hugo Lambert, 23, film student.** Tech 9. iPad in landscape with keyboard and trackpad. Can: editing software. Behaviour: uses the tablet like a laptop. Trips on: tablet treated as a phone, missing hover states, no keyboard support.
- **D45. Zara Sheikh, 22, medical receptionist and part-time student.** Tech 8. Android. Can: apps, online accounts. Behaviour: orders for her parents to their address. Trips on: one-account-one-address assumptions, codes sent to someone else's phone.
- **D46. Nikhil Verma, 29, cloud engineer.** Tech 10. Desktop. Can: infrastructure, scripting. Behaviour: wants exact specs and compatibility. Trips on: vague specs, marketing copy in place of facts, no comparison.
- **D47. Elodie Petit, 25, junior journalist.** Tech 8. iPhone. Can: research, verification. Behaviour: fact-checks claims and reads the about page. Trips on: unverifiable claims, no company details, undated reviews.
- **D48. Devon Price, 21, warehouse temp and gamer.** Tech 8. Android. Can: games, social apps. Behaviour: scrolls fast and taps before the page settles. Trips on: layout shift causing mis-taps, late-loading banners, buttons that move.
- **D49. Aiko Mori, 27, UX researcher.** Tech 9. Laptop. Can: research and testing tools. Behaviour: tries unhappy paths: empty submit, back, refresh. Trips on: data lost on refresh, unclear validation, dead ends.
- **D50. Luca Bjork, 18, first-year student.** Tech 8. iPhone on a family payment plan. Can: apps, games, social platforms. Behaviour: needs a parent to approve purchases. Trips on: approval steps breaking checkout, no way to send the cart to someone else to pay.

## 8. Keeping the panel useful

- Rotate Quick-mode and Standard-mode picks so the same personas are not used every time, except in Benchmark, which reuses the same set. State which personas were used at the top of every report.
- When a real user test or analytics contradicts a simulated finding, trust the real data and note which persona behaved unrealistically so the profile can be corrected.
- If the product has an audience the panel does not cover, say so and offer to add a persona rather than stretching an existing one.