# iteration-log_v1.0.md

# Community Service Visual Design Skill — Iteration Log

## Current Version
V1.0

## Version Stage
Moving from experimental v0.x iterations to architectural V1.x iterations

---

# I. Original Project Goal

The project originally sought to address:

How to turn “community public service information” into a reusable AI Agent Skill, so the Agent does more than generate an image and can reproduce the designer's process for community posters:

- Task understanding;
- Information selection;
- Copy organization;
- Visual direction exploration;
- Human review;
- Image processing;
- Text typesetting;
- Final delivery.

The course objective is not merely to generate posters, but to:

Embed design expertise into a repeatable workflow with clear boundaries that can be inspected and verified.

---

# II. Early Core Problems

Problems exposed by the earliest versions included:

- Human Gates being skipped;
- Unstable output formats;
- Receiving only a PDF when PNG was requested;
- The Agent leaving empty placeholders when input information was limited;
- The Agent failing to proactively add public-facing copy that could reasonably be generated;
- Posters looking more like explanatory pages;
- Users being unable to judge visual directions from text descriptions alone;
- No mechanism for handling scene images that did not match the task;
- Repeated use of the same daytime community image;
- A tendency toward scientific, PowerPoint-style, and stacked-card designs.

These problems drove the continuous v0.x iterations.

---

# III. v0.1 — Basic Human Gates and Information Safety

## Main Goals

Have the Agent:

- Avoid jumping directly to the final image;
- Distinguish generatable content from facts that must not be invented;
- Ensure final PNG delivery;
- Confirm information before designing.

## Main Changes

Established three Human Gates:

- Gate 01: Content confirmation;
- Gate 02: Visual direction;
- Gate 03: Final review.

Also divided input into:

### Content That May Be Proactively Generated

For example:

- General public reminders;
- Suggested actions;
- Subheadings;
- Short public-facing messages;
- Module titles.

### Facts That Must Not Be Invented

For example:

- Times;
- Locations;
- Phone numbers;
- Organizations;
- People's names;
- URLs;
- QR code destinations.

## New Problem Discovered

Gate 02 still consisted only of text directions.

Users could not directly see the differences between directions.

---

# IV. v0.2 — Visualizing Gate 02

## Main Changes

Required Gate 02 to provide more than text alone.

It must generate:

- 3 different directions;
- 3 low-fidelity PNGs;
- Side-by-side comparisons when necessary.

## Test Task

“Community Convenient Repair and Secondhand Swap Day.”

## Test Results

The workflow could run through successfully.

However, the direction previews showed:

- A scientific research style;
- An information-board feel;
- A small image proportion;
- Insufficiently bold headlines;
- Relatively conservative colors.

The user had to manually tell Codex to:

- Refer more closely to style;
- Increase image proportions;
- Use more distinct color jumps;
- Enlarge headlines;
- Create more community atmosphere.

These manual corrections were subsequently incorporated into the Skill.

---

# V. v0.3 — Community Friendliness and the Resource System

## Main Goal

Turn manual visual corrections into default rules.

## Additions

- Community friendliness by default;
- Avoid scientific research styling;
- Higher priority for style references;
- fonts / icons / logos / templates;
- raw-task;
- Automatic Brief drafts;
- README;
- Codex startup prompts.

## User Feedback

The user noted:

The instructor might not provide a standard Brief in the final test.

The Skill must therefore support:

Natural-language task → Agent automatically organizes the Brief.

This laid the foundation for later prioritizing conversational input.

---

# VI. v0.4 — Scene Image Adaptation Mechanism

## Main Problem

The previous workflow relied too heavily on a fixed community image.

New questions included:

- Can a daytime community image be used for a nighttime event?
- Can a sunny image be used for heavy-rain / overcast-rainy themes?
- What if there is no image?
- What if the image does not match the task's meaning?

## Changes

Added image suitability judgments:

- A: Directly suitable;
- B: Suitable with controlled modifications;
- C: Unsuitable.

Allowed modifications:

- Daytime → nighttime;
- Sunny → overcast/rainy;
- Color temperature;
- Lighting;
- Saturation.

Also emphasized:

Do not change spatial structure without a reason.

---

# VII. v0.5 — Theme Semantic Elements

## Background

The user discovered:

Merely changing a photo's weather / time of day does not always express the event theme.

For example:

A nighttime scene alone does not sufficiently convey “cinema” for a movie night.

## Additions

Theme semantic element levels:

- Level 0: None;
- Level 1: A few high-value elements;
- Level 2: A limited thematic system.

For example:

A movie night may include:

- A projection screen;
- Star-like dots;
- String lights.

However, the user may explicitly refuse them.

The Agent must not secretly reintroduce them afterward.

---

# VIII. v0.5 Comprehensive Test: Community Movie Night Under the Stars

This test became an important validation.

## Successes

The Agent could:

- Organize content from raw-task;
- Analyze a daytime scene image;
- Convert it into a night scene;
- Add theme semantic elements;
- Stop at Gates;
- Generate three low-fidelity directions;
- Generate full Chinese and English drafts.

## Manual User Revisions

The user further requested:

- More layered colors;
- Less rigid typography;
- Main headlines that were not always extremely heavy;
- A projection screen integrated into realistic scene relationships;
- String lights and support structures to improve scene credibility.

## Assessment at This Stage

The workflow itself had become relatively stable.

The main question began shifting from:

“Will the Agent execute the process?”

to:

“What aesthetic will the Agent produce by default?”

---

# IX. v0.6 — visual-preferences and Anti-Cardification

## Additions

Formally introduced:

`visual-preferences.md`

To store long-term aesthetic preferences.

Also added:

- Poster First;
- Anti-Cardification;
- Typography-led;
- Image-led;
- Editorial Graphic;
- First Focus Test;
- Blur Test;
- No-Box Test;
- Poster-vs-Document Test.

## Settling the Font Choices

Following discussion, the strategy gradually converged on lightweight fonts:

- Microsoft YaHei;
- Smiley Sans;
- LXGW WenKai;
- Noto Sans / Serif only if present in the environment.

The user did not want to download large amounts of data for two large Noto fonts.

Subsequent rules therefore made clear:

Noto is not a task dependency.

---

# X. v0.6 → v0.7: Artistic Lettering and Highly Saturated Palettes

## New Font Feedback

The user wanted to allow the Agent to:

- Avoid relying entirely on font libraries;
- Generate artistic lettering as images.

This led to:

- Artistic treatment of short main headlines;
- Prioritizing conversion of real text to paths;
- Character-by-character proofreading of generative artistic lettering;
- No unreliable generative text for times, phone numbers, locations, and similar information.

## New Palette Feedback

After providing new poster references, the user noted that previous results had:

- Low saturation;
- Closely spaced hues;
- Insufficient color jumps;
- A lack of comfortable, modern, highly saturated character.

The user also suggested that scene images themselves could be:

- Color-adjusted;
- Darkened;
- Brightened;
- Hue-shifted;
- Stripped of distracting colors;

to support text contrast.

---

# XI. v0.7 — Image Tone and Palette Jump

## Additions

Gate 01 began to include:

- Image hue suggestions;
- Brightness suggestions;
- Saturation suggestions;
- Contrast suggestions;
- Multiple palette directions.

Added:

Palette Jump Test.

## Goal

Stop treating a palette merely as:

“A blue template with a few lighter and darker variations.”

Instead, express:

- High saturation;
- Distinct color jumps;
- Modernity;
- Comfort.

---

# XII. v0.7 Test: Community Lawn Music and Picnic Day

This test used:

- No formal Brief;
- raw-task;
- An extremely short Codex startup prompt.

The purpose was to verify:

Whether the Skill could actually run independently of complex startup prompts.

## Results

The process still worked.

However, Gate 02 revealed clear visual problems:

### 1. Three Differently Named Directions with the Same Underlying Structure

Common structure:

- Title at the top;
- A complete rectangular photo in the middle;
- A large explanation area at the bottom.

### 2. Obvious Information Zoning

It still resembled:

“A designed community announcement.”

### 3. Colors Remained Conservative

Even with blue, green, orange, and other colors:

Overall hue relationships remained safe.

### 4. Scene Images Still Functioned as Rectangular Content Modules

They did not truly become:

- Backgrounds;
- Full-bleed images;
- Layers;
- Key visuals.

---

# XIII. v0.8 — Composition Families and Graphic Poster Mode

## Main Changes

Gate 02 evolved from “style names” to “composition families.”

Including:

- Typography Poster;
- Hero Background Poster;
- Graphic Composition Poster.

Also added a hard constraint:

If all three drafts contain:

- A title at the top;
- An image section in the middle;
- An explanation at the bottom;

the result counts as a failure.

## No-Image Mode

Formally strengthened:

Graphic Poster Mode.

If no community image is available:

Do not automatically add a photorealistic scene.

Instead use:

- Color blocks;
- Circles;
- Stars;
- Arrows;
- Paths;
- Icons;
- Simplified figures;
- Simplified buildings;
- Large headlines.

## Multiple-Image Mode

Began discussing:

- Hero Image;
- Supporting Images;
- Collage;
- Filmstrips;
- Graphic masks.

---

# XIV. Optimizing the style Folder

The user initially placed around 9 reference images in style.

Gate 02 runtime increased noticeably.

The user suspected:

- The network;
- Model load;
- Or too many reference images.

The specific cause could not be confirmed.

However, from the perspective of Skill structure:

9 images increase:

- Visual analysis workload;
- Context volume;
- The cost of reconciling styles;
- The risk of averaging aesthetics.

## Initial Proposal

A proposal was made to divide style into:

- color;
- composition;
- typography;
- graphic-language.

## User Feedback

The user explicitly pointed out:

Real reference images usually include all of:

- Color;
- Composition;
- Typography;
- Image treatment;

making strict classification difficult.

The user did not want to change how they managed inspiration images for the Skill.

## Final Changes

style became:

An overall visual reference pool.

The only recommendation to the user was:

Reduce it themselves to their 4–5 favorite images.

No longer require:

- Classification;
- Special naming;
- One function per image.

The Agent is responsible for synthesis.

---

# XV. Testing Someone Else's Skill

The user received another community poster Skill root directory and wanted to test it with their own Codex.

Feedback after testing:

## Useful Aspects

That Skill:

- Could generate images directly after information confirmation;
- Had strong artistic quality;
- Did not require as many intermediate layout / PDF constraints as the current Skill;
- Could call relevant reference images for different community service scenarios;
- Changed its layout approach when the service type changed.

## Limitations or Aspects Unsuitable for Direct Adoption

Its interaction leaned toward:

Asking only one question at a time.

The user felt:

Although clear, this would:

- Extend task duration;
- Require too many interaction rounds.

Additionally:

Having image generation handle all text directly:

Although artistically strong,

posed higher accuracy risks for:

- Phone numbers;
- Times;
- Addresses;
- Small Chinese text.

The decision was therefore:

Do not directly replace the existing Skill.

Instead:

Keep this project's original Skill as the foundation and absorb the other Skill's operational strengths.

This became the main reason for moving from v0.x to V1.x.

---

# XVI. Why Move Directly from v0.8 to V1.0?

This change was no longer just another visual rule.

It simultaneously changed:

- User input methods;
- Gate 01 interaction;
- Scenario reference mechanisms;
- Task state management;
- Image upload flow;
- Palette decision flow;
- The relationship between image generation and precise typesetting.

Therefore, v0.9 was not used.

The project formally entered:

V1.0.

---

# XVII. V1.0 Architectural Upgrade 1: Conversation First

## Previous Logic

Users needed to understand for themselves:

- Where raw-task belonged;
- Where the brief belonged;
- Where community scene images belonged.

## User Feedback

The user considered this too cumbersome for ordinary users.

For a truly reusable Skill:

Users should not have to learn the project file structure first.

## V1.0 Changes

Start from conversational input by default.

For example:

“Make a community pet-friendly day poster.”

The Agent automatically identifies existing information.

Users only need to:

- Click;
- Fill in answers;
- Upload images;

at the Gates.

The filesystem recedes into the background.

---

# XVIII. V1.0 Architectural Upgrade 2: Gate 01 Changes from a Report to a Dynamic Questionnaire

## Problems in v0.x

Gate 01 output grew increasingly long.

It included:

- Known information;
- AI suggestions;
- Missing facts;
- Scene image analysis;
- Palettes;
- Semantic elements;
- Visual direction;
- Image treatment suggestions.

The user had to:

Read the entire report and then reply item by item.

Test feedback described:

Complex, difficult-to-understand interaction.

## New User Goal

Gate 01 should resemble:

“Wenjuanxing,” an online questionnaire service.

The user wanted:

- Mouse clicks;
- Single selection;
- Multiple selection;
- Input fields;
- Image uploads;
- Recommended options.

Instead of:

Reading option labels and then typing “A / B / C.”

## V1.0 Approach

Prioritize:

Native clickable UI.

If unsupported by the environment:

Generate an HTML form.

Only if both are unavailable:

Fall back to a structured text questionnaire.

---

# XIX. V1.0 Gate 01 No Longer Collects Everything at Once

This was a new requirement further emphasized by the user.

## Undesired Behavior

After the user fills out one large form:

The Agent assumes every issue is resolved and immediately continues working.

## Desired Approach

Staged, dynamic branching.

Gate 01 was therefore divided into:

- Gate 01.1A;
- Gate 01.1B;
- Gate 01.2.

However, these still belong to the same Human Gate.

No fourth Human Gate is added.

---

# XX. Gate 01.1A — Basic Facts

Collect only:

- Theme;
- Audience;
- Time;
- Location;
- Registration;
- Contact details;
- Output specifications;
- Whether images will be uploaded.

At this stage:

Ask only about facts.

Do not discuss in advance:

- How to modify images;
- Whether images are suitable;
- Whether to change to a night scene;
- Palette;
- Collage;
- Visual direction.

## Reason

For example:

The user has just said:

“I will upload 1 scene image.”

The Agent has not actually seen it yet.

Asking in advance:

“Should it be darkened / changed to nighttime / stylized?”

has no basis.

Therefore:

Move to the next assessment only after the image is actually uploaded.

---

# XXI. Gate 01.1B — Chinese and English Copy Confirmation

The user further pointed out:

Gate 01 cannot merely confirm facts.

One of the project's original greatest strengths:

Was better control over text and information.

V1.0 must therefore retain:

Chinese and English copy confirmation.

## How It Works

Once sufficient basic facts are available:

The Agent automatically generates:

- Chinese copy;
- English copy, if required by the task.

Then offers choices:

- Confirm all;
- Revise Chinese;
- Revise English;
- Shorten further;
- Make the copy more engaging for public communication;
- Custom revisions.

## Important Rule

Until Chinese and English copy is confirmed:

Do not enter Gate 01.2.

## Why It Matters

If visual design comes first:

Later changes to headline length, English length, or the number of service items:

Cause substantial layout rework.

Lock copy first, then design.

---

# XXII. Gate 01.2 — Images, Palette, and Visuals

Only after copy confirmation:

Enter actual visual decision-making.

## 0 Images

Default:

Graphic Poster Mode.

## 1 Image

After upload:

First assess:

- Meaning;
- Composition;
- Whitespace;
- Suitability as a hero image.

Then ask the user:

- Whether color adjustments are allowed;
- Whether cropping is allowed;
- Whether stylization is allowed;
- Whether day/night or weather changes are allowed.

## Multiple Images

First analyze:

- Recommended hero image;
- Recommended supporting images.

Then let the user select:

- Hero + Supporting;
- Collage;
- Filmstrip;
- Multi-window;
- Hero image only.

---

# XXIII. V1.0 Moves Palette Selection to the User at Gate 01.2

Previously, specific color combinations had gradually accumulated in visual-preferences.

The user further proposed:

The final palette should still be selected by the user at Gate 01.

## New Rule

Based on:

- The current task;
- Service category;
- Scenario references;
- Images;
- style;

the Agent dynamically generates 3–4 palette directions.

The user clicks to select.

## Changes to visual-preferences

No longer permanently fix:

A particular task to blue and yellow;
A particular task to green and white.

Instead, fix only:

- A tendency toward high saturation;
- Distinct color jumps;
- Modernity;
- Comfort;
- Avoidance of scientific gray-blue.

Specific hues depend on the task.

---

# XXIV. V1.0 Scenario Reference Library

An important mechanism adopted from testing another Skill:

Choosing different references by service scenario.

New recommended directories:

- health-and-free-clinics;
- elderly-care;
- children-education;
- policy-awareness;
- community-activities;
- environmental-protection;
- volunteer-services;
- emergency-services;
- general.

## Difference from style

### style
The user's long-term aesthetic.

### scenarios
Visual tone and information organization for specific service categories.

Use both together.

## What Is Not Copied

Do not hard-code:

“Emergency = red”
“Environmental protection = green”
“Elderly care = orange.”

Scenario routing affects:

- Information organization;
- Composition language;
- Graphic expression;
- Visual tone.

Palette is still dynamically decided at Gate 01.2.

---

# XXV. A New Rendering Problem in V1.0

Comparison with another Skill revealed:

Advantages of direct image generation:

- Strong overall unity;
- Strong artistic quality;
- Unified borders, headlines, and graphics.

Advantages of this project's previous approach:

- Accurate text;
- Reliable times / phone numbers;
- Controllability;
- Stable bilingual output.

However, the user pointed out:

Simply using:

“Half generated image + half PDF text”

would create a new visual disconnect.

---

# XXVI. A Typical Disconnection Example Raised by the User

For example:

- A bubble frame is generated as an image;
- The bubble has a hand-drawn, artistic appearance;
- Yet its subheading suddenly uses ordinary Microsoft YaHei.

The result:

Visually resembles:

Text pasted on afterward.

Likewise:

- A highly artistic main headline;
- A bottom information area that looks entirely like Word;

also undermines the overall poster character.

Therefore:

Do not simply divide the page into “images / text.”

---

# XXVII. V1.0 Architectural Upgrade 3: Component Integrity

Formally introduced:

The component integrity principle.

## Core Idea

Wherever possible, complete a visual component using one consistent design logic.

For example:

A bubble should consider together:

- Contour;
- Fill color;
- Icon;
- Heading;
- Body text.

If text must be precise:

The entire component may be:

Designed consistently in SVG / HTML / Canvas.

Instead of:

Merely pasting text onto a generated image afterward.

---

# XXVIII. V1.0's Three Text Categories

## Type A: Critical Facts

Includes:

- Times;
- Phone numbers;
- Dates;
- Addresses;
- Organizations;
- Registration methods;
- QR code instructions;
- URLs.

Must be precise.

## Type B: Structural Information

Includes:

- Event highlights;
- Module titles;
- Service items;
- Labels.

Treatment depends on the containing component.

## Type C: Expressive Text

Includes:

- Main headlines;
- Subheadings;
- Slogans;
- Keywords.

May receive artistic treatment.

---

# XXIX. Reduced Role of PDF in V1.0

In earlier versions:

PDF / HTML / SVG could be relatively prominent intermediate steps.

New user feedback:

Excessive reliance on PDF constraints:

Weakens the overall artistic quality of image generation.

## V1.0 Redefinition

Use PDF only for:

- Printing;
- Vector output;
- Precise layout archiving.

If the final task requests only PNG:

PDF is no longer the default visual stage.

---

# XXX. The Role of Gate 02 in V1.0

Gate 02 remains.

However, continue strengthening:

“Choose by looking at images.”

Do not require the user to read lengthy direction descriptions.

There must be:

- Image A;
- Image B;
- Image C.

The three images should directly demonstrate differences in:

- Composition;
- Color;
- Image use;
- Information density;
- Headline expression.

The user primarily chooses visually.

---

# XXXI. Gate 03 Remains

Retain the final check.

Reason:

Even if copy has been locked at Gate 01:

Final rendering may still contain:

- Misaligned typography;
- Image occlusion;
- Overlong English;
- Artistic lettering errors;
- Incorrectly typeset phone numbers;
- Disconnected images and text.

Gate 03 must therefore remain responsible for:

Reviewing the final rendered posters.

---

# XXXII. New Meaning of the Three Gates in V1.0

## HUMAN GATE 01
Not “reading a report.”

Instead:

Gradually complete the task definition.

Internally includes:

- 01.1A Basic facts;
- 01.1B Copy confirmation;
- 01.2 Visuals and assets.

## HUMAN GATE 02
The user views three actual direction previews.

Selects a visual direction.

## HUMAN GATE 03
Reviews the final Chinese and English posters.

---

# XXXIII. V1.0 User Experience Goal

Previous experience:

1. User prepares files;
2. User understands directories;
3. User starts Codex;
4. User reads a lengthy Gate 01;
5. User answers item by item;
6. Agent designs.

V1.0 goal:

1. User says one sentence;
2. Clicks through the basic questionnaire;
3. Confirms Chinese and English copy;
4. Drags images directly into the conversation when needed;
5. Clicks image treatment and palette options;
6. Views 3 direction previews;
7. Chooses one;
8. Views the final PNG.

---

# XXXIV. V1.0 Root Directory Changes

## No Longer Emphasized

- `input/raw-task/`
- `input/brief/`
- `input/images/`

These may remain as compatibility paths, but are no longer the default entry point.

## Added / Strengthened

- `references/scenarios/`
- `workspace/current-task/`
- `output/directions/`
- `output/drafts/`
- `output/final/`

---

# XXXV. Changes to V1.0 visual-preferences

Upgraded from:

“Specific colors + specific style rules”

to:

“A global aesthetic baseline.”

Fixed for the long term:

- Poster-first;
- A tendency toward high saturation;
- Distinct color jumps;
- Background-led composition;
- Asymmetry;
- Image/text integration;
- Avoiding announcement-page aesthetics;
- Avoiding scientific research styling;
- Avoiding cards by default;
- Component integrity.

No longer fixed:

A requirement that every task use particular specific color groups.

---

# XXXVI. Currently Known V1.0 Risks

Still requiring testing:

## 1. Clickable Form Compatibility

Different Codex / Agent environments may offer different levels of support for:

- Native buttons;
- HTML forms;
- File upload interactions.

Fallbacks must therefore remain.

## 2. Whether Gate 01 Becomes Too Fragmented

Although not all questions are asked at once:

Also avoid:

A separate turn for every minor question.

Target:

3–6 related questions per round.

## 3. Text Accuracy in Image Generation

Artistic main headlines may still contain incorrect characters.

Proofreading is mandatory.

## 4. Stability of Component-Level Hybrid Rendering

Test whether:

- Precise text components;
- Generative backgrounds;
- Artistic headlines;

can actually integrate.

## 5. Whether the Scenario Reference Library Slows Analysis

Limit reading to:

The most relevant scenario each time.

Do not scan the entire library.

---

# XXXVII. Recommended Follow-Up V1.0 Test Tasks

Future testing should cover:

## Test A: 0 Images
Validate:

Graphic Poster Mode.

## Test B: 1 Image
Validate:

Image semantic assessment + stylization permissions.

## Test C: Multiple Images
Validate:

Hero + Supporting / collage.

## Test D: High-Accuracy Text
For example:

First-aid services, consultation phone numbers, and numerous times and locations.

Validate:

Precise typesetting of critical facts.

## Test E: Strong Artistic Headlines
Validate:

Component integration of artistic lettering and structural text.

## Test F: Different Service Scenarios
Test consecutively:

- Emergency services;
- Children;
- Community events;
- Policy.

Validate:

Whether scenario references actually change layouts rather than merely changing colors.

---

# XXXVIII. V1.0 Stage Summary

The essence of V1.0 is not:

“Making the old Skill more complicated.”

Rather, the opposite:

Move complexity inside the Agent.

The user-facing process becomes simpler:

**Conversation → click → upload → view images → choose.**

While retaining the control designers actually need:

- Factual accuracy;
- Copy confirmation;
- Palette selection;
- Image treatment permissions;
- Human Gates;
- Three-direction comparison;
- Bilingual proofreading;
- Final review.

---

# XXXIX. The Core Change from v0.x to V1.0

It can be summarized as:

## v0.x
“Teach the Agent to follow a design process for community posters.”

## V1.0
“Let ordinary users use this design process naturally, while truly integrating generative visuals with precise design.”

---

# XL. Current Project Status

As of V1.0:

## Workflow Capabilities
Already relatively mature:

- Task understanding;
- Human Gates;
- Copy generation;
- Factual safety;
- Image adaptation;
- Style references;
- Scenario references;
- Bilingual output;
- PNG output.

## Current Focus
Moving into:

- Interaction experience;
- Component integration;
- Scenario differentiation;
- Balancing visual artistry and information accuracy.

This marks the project's formal transition from the “functional prototype stage” to the “usability and design quality integration stage.”
