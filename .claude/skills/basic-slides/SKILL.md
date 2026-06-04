---
name: basic-slides
description: Generate a plain-text slide deck outline (titles and bullet points only) for a computational chemistry lecture. No design, no equations, no formatting flourishes.
---

The user will provide a lecture topic (e.g. "molecular dynamics", "density functional theory", "enhanced sampling"). Generate a complete slide deck outline for a single lecture on that topic.

## Output format

Plain text only. For each slide, output:

```
## Slide N: [Title]
- Bullet point
- Bullet point
- Bullet point
```

Rules:
- No LaTeX, no equations, no math notation of any kind
- No emoji, no bold/italic, no design suggestions
- No "visual:", "figure:", "animation:", or layout hints
- 3–6 bullet points per slide
- Bullet points are concise phrases (not full sentences)
- Aim for 12–18 slides total for a 50-minute lecture
- Include an opening slide (title + learning objectives) and a closing slide (summary + further reading topics)
- Group slides into logical sections; introduce each section with a brief section-header slide that just lists what the section covers

## File output

After generating the slide deck, write it to a Markdown file in the `lecture-slides/` subfolder of the current working directory. Create the folder if it does not exist.

Filename convention: lowercase, hyphens for spaces, no special characters. Examples:
- "molecular dynamics" → `lecture-slides/molecular-dynamics.md`
- "density functional theory" → `lecture-slides/density-functional-theory.md`

Use the Write tool to create the file. After writing, tell the user the file path.

## Audience

Assume advanced undergraduate or first-year graduate students in chemistry or chemical engineering. They know calculus and basic physical chemistry but may not have prior programming or simulation experience.

## Slide structure to follow

1. Title slide (lecture title, course context, date placeholder)
2. Learning objectives (what students will be able to do after this lecture)
3. Section header slides between major topic blocks
4. Content slides (concept, motivation, key ideas, examples)
5. Summary slide (3–5 takeaways)
6. Further reading / next steps slide

## What to ask the user if not provided

- Lecture topic (required — do not guess if missing)
- Approximate lecture length (default: 50 minutes → ~15 slides)
- Any prerequisite topics students have already covered (helps calibrate depth)
- Whether this is a standalone lecture or part of a series (affects how much context-setting is needed)
