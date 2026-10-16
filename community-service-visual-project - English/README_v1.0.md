# README_v1.0.md

# Community Service Visual Design Skill — V1.0

## 1. What Is V1.0?

V1.0 is the project's first architectural upgrade.

Earlier v0.x versions mainly addressed:

- Human Gates;
- Brief / raw-task;
- Scene image adaptation;
- Theme semantic elements;
- Low-fidelity direction previews;
- Color palettes;
- Fonts;
- Anti-cardification;
- Graphic Poster Mode without images.

Building on these foundations, V1.0 addresses how ordinary users can use the Skill more easily and how generative visuals can integrate with precise text.

---

# 2. The Most Important Changes

## 2.1 Users No Longer Need to Maintain Input Folders

Start directly from the conversation by default.

For example, the user only needs to say:

“Help me make a poster for a community secondhand swap day, Sunday afternoon, in Chinese and English, 4:5.”

The Skill automatically enters Gate 01.

Users no longer have to:

- Create a raw-task;
- Create a brief;
- Copy images into a fixed directory in advance.

These become optional advanced uses.

---

## 2.2 Gate 01 Becomes a Staged Dynamic Questionnaire

Gate 01 now includes:

### Gate 01.1A
Basic facts questionnaire.

### Gate 01.1B
Chinese and English copy generation and confirmation.

### Gate 01.2
Confirmation of scene images, palette, information density, and visual strategy.

Users do not need to answer every question at once.

The Skill dynamically determines what to show next based on previous answers.

---

# 3. Clickable Questionnaire Mechanism

V1.0 explicitly prioritizes clickable questionnaires.

Priority order:

1. Native clickable selection controls in the current runtime;
2. Lightweight local HTML forms;
3. Structured text questionnaires as the final fallback.

If the current environment does not support genuinely clickable controls:

Do not pretend buttons exist.

Explicitly fall back to a compatible method.

---

# 4. What Gate 01.1A Collects

Collect only basic facts:

- Event / service name;
- Target audience;
- Time;
- Location;
- Organization;
- Contact details;
- Participation / registration method;
- Output language;
- Dimensions;
- Whether the user plans to upload scene images.

Do not ask again for information already known.

Do not ask at this stage about:

- Palette;
- Whether to stylize images;
- Whether images fit the task;
- Whether to darken images;
- Collage approach;
- Visual direction.

Leave these to Gate 01.2.

---

# 5. Gate 01.1B: Copy Confirmation

Once sufficient basic facts are available, the Skill automatically generates:

- Chinese poster copy;
- English poster copy, if needed.

Then let the user choose:

- Confirm all;
- Revise Chinese;
- Revise English;
- Shorten both versions;
- Make both versions more engaging for public communication;
- Edit manually.

Before copy confirmation is complete:

Do not enter visual design.

---

# 6. Gate 01.2: Image and Visual Choices

## 0 Images

Default:

Graphic Poster Mode.

Use:

- Color blocks;
- Icons;
- Circles;
- Stars;
- Arrows;
- Simplified figures;
- Simplified buildings;
- Large headlines.

## 1 Image

Assess after upload:

- Whether it fits the task;
- Whether it works as a background;
- Whether color adjustment is needed;
- Whether cropping is allowed;
- Whether stylization is allowed;
- Whether day/night or weather changes are allowed.

## Multiple Images

After upload:

- The Agent recommends a hero image;
- Recommends supporting images;
- The user chooses collage, filmstrip, multi-window, Hero + Supporting, or other approaches.

---

# 7. How to Choose a Palette

V1.0 does not fix specific colors in visual-preferences.

In Gate 01.2, the Agent dynamically generates 3–4 options based on the current task.

The user selects directly.

This allows tasks to vary meaningfully instead of always using the same blue, yellow, and green combination.

---

# 8. Scenario Reference Library

Recommended structure:

```text
skill/references/scenarios/
├─ health-and-free-clinics/
├─ elderly-care/
├─ children-education/
├─ policy-awareness/
├─ community-activities/
├─ environmental-protection/
├─ volunteer-services/
├─ emergency-services/
└─ general/
```

A small number of reference images per category is sufficient.

They are not final assets.

Their purpose is to:

- Vary layout logic across service scenarios;
- Vary the tone of information;
- Vary graphic expression;
- Avoid making every task look the same.

---

# 9. The style Folder

Retain:

`skill/references/style/`

4–5 images are recommended.

No classification is required.

No special naming is required.

The Agent treats them as an overall aesthetic reference pool.

---

# 10. Recommended Root Directory

```text
project-root/
├─ skill/
│  ├─ SKILL.md
│  ├─ references/
│  │  ├─ visual-preferences.md
│  │  ├─ style/
│  │  └─ scenarios/
│  └─ assets/
│     ├─ fonts/
│     ├─ icons/
│     ├─ logos/
│     └─ templates/
├─ workspace/
│  └─ current-task/
├─ output/
│  ├─ directions/
│  ├─ drafts/
│  └─ final/
└─ logs/
```

Users usually only need to:

- Open the project root;
- Enter the task in Codex;
- Click / answer at the Gates;
- Drag images directly into the conversation when needed.

---

# 11. Gate 02

Gate 02 must produce 3 genuinely comparable direction previews.

Text-only directions are no longer sufficient.

The three directions vary dynamically by image count:

- 0 images: Typography / Graphic / Editorial / Illustration;
- 1 image: Hero / Hybrid / Image + Type;
- Multiple images: Hero + Supporting / Collage / Multi-window.

Only proceed to the full draft after the user chooses.

---

# 12. How V1.0 Integrates Images and Text

V1.0 no longer uses the simple approach:

“Half generative imagery + half PDF text.”

Instead, it uses:

**Component-level hybrid rendering.**

Key principle:

If an information block requires precise text:

Design the entire block as a unified component wherever possible.

Avoid:

- An artistic speech bubble;
- A sudden line of default Microsoft YaHei inside it;
- Text that visually looks pasted on afterward.

---

# 13. Which Text Must Be Precise?

Must be precise:

- Phone numbers;
- Times;
- Dates;
- Locations;
- Addresses;
- Organizations;
- Registration methods;
- QR code instructions;
- URLs.

Can be more artistic:

- Main headlines;
- Subheadings;
- Slogans;
- Short keywords.

Other information depends on its component.

---

# 14. The Role of PDF in V1.0

PDF is no longer the default visual generation stage.

Use it only when:

- The user needs printing;
- A vector version is needed;
- Precise layout archiving is needed.

If the task requires PNG:

A PNG must actually be delivered.

---

# 15. The Shortest Way to Start

Recommended direct prompt:

“Help me make a community pet-friendly day poster, Saturday afternoon, for resident families, in Chinese and English, 4:5. Follow the Skill.”

The Skill then automatically enters Gate 01.

No additional explanation is needed about:

- Where to find the brief;
- Where to find the raw-task;
- Where to find images.

---

# 16. Version Files

For this V1.0 release, the recommended project files are:

- `SKILL_v1.0.md`
- `visual-preferences_v1.0.md`
- `README_v1.0.md`
- `iteration-log_v1.0.md`

For actual use, you can copy or rename:

`SKILL_v1.0.md`

to:

`skill/SKILL.md`

and copy or rename:

`visual-preferences_v1.0.md`

to:

`skill/references/visual-preferences.md`

---

# 17. V1.0 in One Sentence

V1.0 no longer requires users to “learn the project file structure before using the Skill.”

Instead:

**Start with one sentence → staged clickable questionnaires → copy confirmation → image and palette confirmation → three visual directions → component-level image/text integration → final PNG.**
