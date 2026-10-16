---
name: community-service-visual-design
version: 1.0
description: A conversational visual poster design Skill for community public services, community events, health reminders, action guides, service locations, and help-seeking information. Primarily uses conversational input, with staged interactive questionnaires in HUMAN GATE 01 to confirm basic facts, bilingual copy, scene images, palettes, and visual strategy; then generates three genuinely comparable visual directions in HUMAN GATE 02; finally produces PNG posters using a hybrid of generative visuals and component-level precise typesetting, followed by final review in HUMAN GATE 03.
---

# Community Service Information Key Visual Design Skill — V1.0

## 1. Core Goals

Transform community public services, health reminders, action guides, community events, service locations, and help-seeking information into posters with a clear visual narrative, effective public communication, and a strong design quality.

This Skill prioritizes:

- Accurate information, without inventing real dates, locations, phone numbers, organizations, QR code destinations, or other facts;
- No requirement for users to understand the project directories or manually prepare `brief.md`, `raw-task`, or `input/images/` beforehand;
- Starting tasks from conversational input by default;
- Staged, dynamically branching interactive questionnaires in HUMAN GATE 01 instead of lengthy analysis reports;
- User confirmation of Chinese and English copy before visual design begins;
- Assessing the number, suitability, and treatment of scene images only after actual upload;
- The Agent proposing palette directions based on the task and references, with the user choosing at Gate 01.2;
- Genuinely comparable visual sketches at HUMAN GATE 02, rather than text descriptions alone;
- PNG as the preferred final output;
- Integrating visual generation and precise typesetting through component integrity, avoiding an obvious disconnect from forcibly overlaying system text on generated images.

---

# 2. Default Input Method: Conversation First

## 2.1 Conversational Input Comes First

Start by default with the user's natural-language task in the current conversation, for example:

“Help me make a community pet-friendly day poster, Saturday afternoon, for resident families, in Chinese and English, 4:5.”

The Agent should extract existing information from this sentence and ask only about missing items.

## 2.2 File Input Becomes Optional

If the user proactively provides:

- A Brief;
- A raw task;
- Images;
- A logo;
- A QR code;
- Brand guidelines;
- Reference posters;

read and merge them into the current task state.

However, do not require ordinary users to place these materials in fixed folders before starting work.

## 2.3 The Agent Manages the Workspace

The Agent may maintain the following within the project:

`workspace/current-task/`

To save:

- Structured information for the current task;
- Gate 01 questionnaire results;
- Confirmed Chinese and English copy;
- Task references to user-uploaded images;
- Scenario and reference routing results;
- Visual direction records;
- Final parameters.

Users generally do not need to edit these files manually.

---

# 3. Recommended Root Directory Structure

```text
project-root/
├─ skill/
│  ├─ SKILL.md
│  ├─ references/
│  │  ├─ visual-preferences.md
│  │  ├─ style/
│  │  └─ scenarios/
│  │     ├─ health-and-free-clinics/
│  │     ├─ elderly-care/
│  │     ├─ children-education/
│  │     ├─ policy-awareness/
│  │     ├─ community-activities/
│  │     ├─ environmental-protection/
│  │     ├─ volunteer-services/
│  │     ├─ emergency-services/
│  │     └─ general/
│  └─ assets/
│     ├─ fonts/
│     ├─ icons/
│     ├─ logos/
│     └─ templates/
├─ workspace/
│  └─ current-task/
│     ├─ task-spec.md
│     ├─ gate01/
│     └─ uploads/
├─ output/
│  ├─ directions/
│  ├─ drafts/
│  └─ final/
└─ logs/
```

Notes:

- `references/style/`: Keep around 4–5 of the user's favorite overall style references as a shared aesthetic reference pool;
- `references/scenarios/`: Keep a few relevant reference posters by community service scenario to vary information organization and visual tone;
- `assets/`: Fonts, icons, logos, and templates that can actually be used directly;
- `workspace/`: The Agent's workspace, with no user maintenance required;
- `output/`: Direction drafts, intermediate drafts, and final files.

---

# 4. Reference Priority

When conflicts arise, priority from highest to lowest is:

1. Explicit user requirements in the current turn;
2. Choices already approved at HUMAN GATES;
3. Factual content supplied by the user;
4. `visual-preferences.md`;
5. `references/scenarios/` matched to the current task;
6. `references/style/`;
7. Skill defaults.

Do not override user-confirmed content to imitate a reference image.

---

# 5. Scenario Reference Routing

## 5.1 Purpose

Automatically select more relevant community service visual references based on task meaning, giving different service scenarios distinct information organization and visual tones instead of using the same layout for every task.

## 5.2 Basic Categories

Route by task meaning to:

- health-and-free-clinics: Free clinics, health consultations, physical examinations, health screenings, etc.;
- elderly-care: Respect for elders, senior living, classes for older adults, age-friendly services, etc.;
- children-education: Parent-child activities, children's events, picture books, children's crafts, etc.;
- policy-awareness: Policy explanations, social insurance, fraud prevention, public administrative service guides, etc.;
- community-activities: Markets, movie nights, music, secondhand swaps, neighborhood events, etc.;
- environmental-protection: Waste sorting, reuse of old items, community cleanups, greening, etc.;
- volunteer-services: Volunteer recruitment, public-interest activities, neighbor-to-neighbor assistance, etc.;
- emergency-services: First aid, fire safety, disaster prevention, extreme heat, heavy rain, typhoons, etc.;
- general: When classification is unclear or multiple scenarios overlap.

## 5.3 Usage Rules

- Prioritize the scenario references most relevant to the current task each time;
- Use scenario references to inspire information organization, visual tone, graphic language, and layout rhythm;
- Do not mandate a particular color for a particular scenario;
- Specific palettes are still proposed dynamically at Gate 01.2 and selected by the user;
- Do not mechanically copy scenario references;
- If a task spans two categories, both may be read, but avoid reading large numbers of irrelevant references at once.

---

# 6. Style Reference Pool

`skill/references/style/` is the overall aesthetic reference pool.

Recommend keeping 4–5 posters the user genuinely likes.

Do not require:

- Each image to serve only one function;
- Classification by color / composition / typography;
- Special naming;
- An explanation for each image.

The Agent should synthesize recurring visual tendencies across images, such as:

- The extent to which the background leads;
- Headline scale;
- Color energy;
- Asymmetry;
- Image/text overlap;
- Distributed information;
- Use of graphic elements;
- Relationships between whitespace and density.

Do not average the style into a safe, conservative result merely to combine all references.

---

# 7. Three HUMAN GATES

The number of Gates remains fixed at three:

- HUMAN GATE 01: Confirm the task and visual prerequisites;
- HUMAN GATE 02: Select a visual direction;
- HUMAN GATE 03: Review the final rendered poster.

HUMAN GATE 01 contains:

- Gate 01.1A: Basic facts and task information;
- Gate 01.1B: Chinese and English copy generation and confirmation;
- Gate 01.2: Asset, palette, and visual strategy confirmation.

Do not enter Gate 02 before all of Gate 01 is complete.

---

# 8. HUMAN GATE 01.1A — Basic Facts Questionnaire

## 8.1 Goal

Collect only the basic facts essential to establishing the task. Do not discuss palette, stylization, image suitability, or visual composition at this stage.

## 8.2 Automatically Inventory Existing Information First

First identify from the current conversation and supplied materials:

- Event / service name;
- Theme;
- Target audience;
- Time;
- Location;
- Organizer / service provider;
- Participation method;
- Registration method;
- Contact details;
- Output language;
- Output aspect ratio;
- Output dimensions / resolution;
- Whether community scene images will be supplied;
- Other essential facts.

Do not ask again about information already clear.

## 8.3 Question Presentation

Prioritize native clickable selection controls supported by the runtime, such as:

- Radio buttons;
- Multiple-selection buttons;
- Dropdown options;
- Clickable cards;
- Text input fields;
- File upload controls.

If the runtime has no native clickable form capability:

1. Prefer generating a lightweight interactive HTML form in `workspace/current-task/gate01/`;
2. If the HTML form cannot actually be interacted with either, fall back to a structured text questionnaire;
3. Do not pretend controls are clickable buttons when they cannot actually be clicked.

## 8.4 Questionnaire Organization Principles

- Combine similar information into one question group;
- Present 3–6 questions genuinely needed at the current stage at a time;
- Provide 2–4 recommended options per question;
- Retain reasonable options such as custom / do not display yet / provide later;
- Do not require users to read a lengthy report;
- Dynamically generate the next group of questions based on the user's answers;
- Gate 01.1A does not require collecting everything at once.

## 8.5 Ask Only About Intended Scene Image Count

At this stage, confirm only:

- No community scene images;
- Planning to upload 1 image;
- Planning to upload multiple images;
- Undecided.

Before images are uploaded, do not ask in advance about:

- Darkening;
- Recoloring;
- Day/night conversion;
- Task suitability;
- Collage;
- Stylization.

Leave all of these to Gate 01.2.

---

# 9. HUMAN GATE 01.1B — Chinese and English Copy Generation and Confirmation

## 9.1 Trigger

Once Gate 01.1A has obtained enough basic facts to generate copy, the Agent automatically organizes the poster copy.

If the user requests:

- A Chinese version: Generate Chinese copy;
- An English version: Generate English copy;
- One version in each language: Generate Chinese and English copy separately.

## 9.2 Copy Source Layers

### A. Factual Copy Provided by the User

Preserve faithfully, for example:

- Time;
- Location;
- Phone numbers;
- Organization names;
- Registration method;
- Addresses;
- Actual service offerings.

Do not change facts without authorization.

### B. Promotional Copy Suggested by the Agent

May proactively generate:

- Main headline refinements;
- Subheadings;
- Slogans;
- Event highlights;
- Short calls to action;
- Friendly reminders;
- Module titles;
- Concise public-facing explanations.

Make clear to the user that these are Agent suggestions.

## 9.3 Copy Confirmation Interface

Prefer clickable forms / selection controls offering:

- Confirm all and continue;
- Chinese needs revision;
- English needs revision;
- Shorten both versions further;
- Make both versions more engaging for public communication;
- Keep factual information and rewrite only promotional copy;
- I will edit / add content myself.

If the user chooses to revise one language:

- Continue working only on that language;
- Keep the other language locked;
- Confirm again after revision.

## 9.4 Copy Lock Rules

The following must be achieved:

- Chinese copy confirmed;
- English copy confirmed, if the task requires English;

before Gate 01.1 can end.

During the visual stage, do not add, remove, or rewrite locked key copy without authorization.

If secondary copy must be condensed for layout, explicitly explain this and obtain user agreement at Gate 01.2 or later.

---

# 10. HUMAN GATE 01.2 — Asset, Palette, and Visual Strategy Confirmation

Gate 01.2 must start after copy confirmation.

Its questions must branch dynamically based on the number of images actually supplied.

## 10.1 Case A: 0 Community Scene Images

If the user explicitly declines to upload, or no usable community scene images are ultimately available:

Enter Graphic Poster Mode by default.

Prioritize:

- Large color blocks;
- Circles;
- Stars;
- Arrows;
- Paths;
- Icons;
- Simplified figures;
- Simplified buildings;
- Abstract lawns / neighborhoods;
- Large headlines;
- Geometric or hand-drawn visual elements.

Do not revert simply because there are no photographs to:

- An explanatory page on a white background;
- PowerPoint information blocks;
- An ordinary noticeboard.

### Confirm at Gate 01.2

- Pure graphic poster / more restrained editorial poster / more lively illustrated graphic direction;
- Information density;
- Dynamic palette direction;
- Whether to add scenario-related graphic elements;
- Whether artistic headline treatment is allowed.

## 10.2 Case B: 1 Community Scene Image

After actual upload, the Agent first analyzes:

- Whether it matches the task's meaning;
- Whether time / weather matches;
- Whether the subject suits a background;
- Whether there is room for text overlay;
- Whether visual noise is present;
- Whether it suits use as a Hero Image.

Only then generate the Gate 01.2 questionnaire.

### Treatment Permissions for User Confirmation

May offer:

- Largely preserve the original image;
- Allow brightness / contrast adjustments;
- Allow hue / saturation adjustments;
- Allow partial cropping / blur / masking;
- Allow weather / day-night changes;
- Allow more pronounced stylization;
- Allow graphic overlays;
- Let the Agent choose a reasonable scope based on the direction.

Do not make major changes to scene meaning without user approval.

## 10.3 Case C: Multiple Community Scene Images

The Agent first evaluates:

- Theme fit;
- Composition;
- Sharpness;
- Whitespace;
- Potential for text overlay;
- Visual noise;
- Tonal consistency.

Then recommend to the user:

- 1 Hero Image;
- 0–2 supporting images.

Also offer clickable choices:

- Hero + Supporting Images;
- Collage first;
- Filmstrip / multi-window;
- Graphic masks;
- Use only the best hero image;
- User designates the hero image.

If using multiple images, explain how to unify:

- Color temperature;
- Saturation;
- Contrast;
- Cropping;
- Graphic language.

---

# 11. Dynamic Palette Selection at Gate 01.2

The user must choose the palette, but the Agent dynamically generates the options for the current task.

Do not present the same fixed colors for every task.

## 11.1 The Agent Generates 3–4 Palette Directions

Each direction should include:

- A short name;
- Visual character;
- Main hue relationships;
- Why it suits this task;
- Whether it suits the current scene image.

Examples may include:

- Highly saturated hue jumps;
- Modern comfort;
- Warm friendliness;
- High-contrast warning;
- Fresh natural colors;
- Nighttime neon;
- Automatic Agent judgment.

## 11.2 Palette Principles

General preferences:

- Relatively high saturation;
- Distinct hue jumps;
- Modern;
- Comfortable;
- Avoid scientific blue-gray;
- Avoid only slight variations within similar hues across all colors.

However, specific colors must be determined jointly by:

- The current task;
- Scenario category;
- Scenario references;
- style references;
- Uploaded images;
- User choice.

---

# 12. Gate 01 Completion Conditions

Gate 01 may end only after:

- Sufficient basic facts are available;
- The user has decided whether to supply / omit / provide later any missing essential facts;
- Chinese copy is confirmed;
- English copy is confirmed, if needed;
- The scene image strategy is confirmed;
- Uploaded images' semantic suitability and treatment permissions are confirmed;
- Palette direction is confirmed;
- Information density is confirmed;
- Visual direction is confirmed;
- Necessary semantic elements are confirmed.

The Agent then writes the complete internal results to:

`workspace/current-task/task-spec.md`

Show the user only a concise confirmation summary, without a lengthy analysis report.

---

# 13. HUMAN GATE 02 — Visual Direction Selection

## 13.1 Actual Visual Images Are Required

Gate 02 must not provide only textual descriptions of directions.

Output 3 comparable low- or medium-fidelity visual sketch PNGs.

Purpose:

- Compare compositions;
- Compare colors;
- Compare image/text relationships;
- Compare scene image use;
- Compare artistic quality.

Text may be temporarily simplified, but must not contain obvious gibberish or meaningless placeholders.

## 13.2 Three Directions Should Vary by Image Count

### Tasks with 0 Images

The three directions may be selected from these composition families:

- Typography-led;
- Graphic Composition;
- Editorial / Icon-led;
- Illustration-led.

At least one direction must build a complete visual entirely through color blocks, graphics, and text, rather than a plain background plus information boxes.

### Tasks with 1 Image

The three directions may follow these approaches:

- Hero Background;
- Hybrid Overlay;
- Image + Typography;
- Cropped Editorial.

All three drafts must not simply be “rectangular photo + text at the bottom.”

### Tasks with Multiple Images

The three directions may follow these approaches:

- Hero + Supporting;
- Collage;
- Editorial Multi-window;
- Layered / Masked Composition.

Do not merely change the order of image placement.

## 13.3 Role of Scenario References

At Gate 02, read the matching `references/scenarios/` and overall `style/` references.

Scenario references determine:

- Information organization;
- Visual tone;
- Layout tendencies;
- Graphic language.

Overall style determines:

- The design character the user has long preferred;
- Color energy;
- Poster character;
- Background/headline relationships.

## 13.4 Gate 02 Output

Output:

- Direction A PNG;
- Direction B PNG;
- Direction C PNG;
- A very short explanation of differences.

Then stop and wait for the user to:

- Choose one;
- Specify revisions and then choose;
- Reject all and request new directions.

Do not automatically proceed to the full draft.

---

# 14. V1.0 Rendering Core: Component-Level Hybrid Rendering

## 14.1 Stop Coarsely Splitting the Page into Half Generated Imagery and Half PDF Typesetting

Avoid:

- Generative backgrounds and bubbles;
- Bubble headings abruptly switching to default Microsoft YaHei;
- Artistic generated imagery paired with an information section resembling a Word document;
- A precise typesetting layer interrupting the visual system.

## 14.2 Adopt the Component Integrity Principle

Wherever possible, complete a visual component using one consistent visual logic.

For example, an information bubble includes:

- Outer contour;
- Fill color;
- Icon;
- Subheading;
- Body text.

If its text must be precise:

Prefer designing the entire bubble as a unified component in a precise typesetting system such as SVG / HTML / Canvas, rather than simply forcing text over a generative bubble.

## 14.3 Three Text Types

### Type A — Critical Factual Text

Includes:

- Phone numbers;
- Times;
- Dates;
- Addresses;
- Organization names;
- Registration methods;
- QR code instructions;
- URLs.

Requirements:

- 100% accuracy;
- Prioritize precise typesetting;
- Check character by character before export.

### Type B — Structural Information Text

Includes:

- Event highlights;
- Participation methods;
- Friendly reminders;
- Module titles;
- Service items;
- Label text.

Treatment:

- If part of a card / bubble / label component, render the entire component consistently;
- Do not simply overlay isolated text onto a stylistically inconsistent generative frame.

### Type C — Expressive Text

Includes:

- Main headlines;
- Subheadings;
- Slogans;
- Short emphasis phrases;
- Visual keywords.

Allowed:

- Display fonts such as Smiley Sans;
- SVG / Canvas conversion to paths;
- Outlines;
- Deformation;
- Stretching;
- Offsets;
- Artistic lettering through image generation.

However, accuracy must be checked character by character.

---

# 15. Redefining the Role of PDF

PDF is no longer the default intermediate layer for visual generation.

Use PDF only when:

- The user explicitly needs print files;
- Vector text and precise layout must be preserved;
- An additional print version must be submitted;
- The typesetting of critical factual text needs verification.

If the user requests only PNG:

The final output must be PNG.

Do not design the page as a “PDF explanation page” merely because PDF / HTML / SVG is used as a technical intermediate layer.

---

# 16. Font Strategy

Lightweight font strategy:

- Microsoft YaHei: Critical facts, body text, safe fallback;
- Smiley Sans: Main headlines and short keywords;
- LXGW WenKai: Optional warm, cultural, or festive subheadings;
- Noto Sans / Serif: Only if already available in the current environment; downloading is not required.

Font choices must support component unity.

If a graphic component needs precise text:

Design it jointly through:

- Typeface;
- Weight;
- Letter spacing;
- Outlines;
- Color;
- Border;
- Icons;
- Background shape;

to avoid simply overlaying bare default system typography.

---

# 17. HUMAN GATE 03 — Final Poster Review

After the user selects a Gate 02 direction:

1. Build the full visual base;
2. Complete component-level typesetting;
3. Proofread critical factual text;
4. Adapt Chinese and English versions separately;
5. Export PNGs at the user-requested dimensions;
6. Display the final drafts;
7. Enter Gate 03.

Gate 03 must allow the user to check:

- Text accuracy;
- Chinese / English meaning;
- Main headline;
- Palette;
- Image treatment;
- Component unity;
- Information density;
- Any obvious disconnection from forcing system text onto generated imagery;
- Whether the Gate 02 selected direction is maintained.

Without explicit approval, do not consider the task finally complete.

---

# 18. Bilingual Version Rules

Chinese and English must:

- Correspond in meaning;
- Avoid mechanical word-for-word translation;
- Have layouts readjusted to language length;
- Maintain the same design system;
- Not require pixel-level duplication;
- Not arbitrarily lose important information because English is longer.

If the user requests copy confirmation first:

Complete Chinese and English confirmation at Gate 01.1B before entering the visual stage.

---

# 19. Information Accuracy Rules

Do not invent without authorization:

- Dates;
- Times;
- Locations;
- Phone numbers;
- Organizations;
- People's names;
- QR code destinations;
- URLs;
- Any real service information.

If missing:

Let the user choose:

- Do not display yet;
- Provide later;
- Remove the module;
- Enter custom information.

Do not leave obvious empty placeholder boxes in the final poster.

---

# 20. Anti-Cardification

Unless the scenario references or task explicitly require a card system, avoid by default:

- Top title bars;
- Middle photo strips;
- Bottom explanation bars;
- Multiple equal-width cards;
- One rectangular box per information item;
- PowerPoint-style rigid grids.

Prioritize:

- Backgrounds;
- Large headlines;
- Image/text overlap;
- Floating information;
- Circles / stars / arrows;
- Labels;
- Paths;
- Nonrectangular color blocks;
- Whitespace;
- Edge arrangements;
- Changes in visual density.

---

# 21. Final Verification

Before submission, check:

## 21.1 First Focus Test
Does the first glance reveal the correct theme and visual focus?

## 21.2 Poster vs Document Test
Does it look more like a poster or an explanatory page?

## 21.3 Palette Test
Does the palette match the user's Gate 01.2 selection?

## 21.4 No-Box Test
Does the composition still work when prominent rectangular boxes are removed?

## 21.5 Scenario Fit Test
Does the visual language suit the current service scenario, rather than making every task look the same?

## 21.6 Image Strategy Test
Does the 0 / 1 / multiple-image strategy match the Gate 01.2 decision?

## 21.7 Copy Lock Test
Does the final copy match the version confirmed at Gate 01.1B?

## 21.8 Critical Text Test
Are phone numbers, times, locations, dates, organizations, and similar facts accurate character by character?

## 21.9 Component Integrity Test
Are there visibly disconnected components combining a generative border with forced default system typography?

## 21.10 Bilingual Test
Do Chinese and English correspond in meaning and receive separate layout adaptation?

---

# 22. Final Goal

V1.0 does not aim to make users learn directory structures or have the Agent output a lengthy design analysis.

The goals are:

- Users start tasks with a single natural-language sentence;
- Gate 01 gradually establishes facts, copy, images, palette, and visual strategy through genuinely low-effort questionnaires that prioritize clickable controls and dynamic branching;
- The scenario reference library gives different service scenarios different layouts and visual tones;
- Gate 02 directly lets users see three design directions;
- Final production integrates generative visuals with component-level precise typesetting;
- Preserve the artistic character of main headlines, bubbles, graphics, backgrounds, and the overall page while keeping facts such as phone numbers, times, and locations accurate;
- Deliver accurate, complete PNGs with a modern poster character.
