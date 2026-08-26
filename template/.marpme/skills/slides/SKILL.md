# Marpme presentation skill

Use this skill when creating or revising presentations under `presentations/`.

## Workflow

1. Read `brand.md` before choosing colors, typography, or spacing.
2. Read `diagrams.md` before adding architecture or process diagrams.
3. Start from `.marpme/starter/deck.md`; keep deck-specific assets beside the deck.
4. Keep one principal message per slide and support it with evidence or a visual.
5. Preview the complete deck and check overflow, contrast, and narrative continuity.

## Repository contract

- `.marpme/theme/**`, `.marpme/config/**`, and `.marpme/skills/**` are shared and
  updated from the Copier template.
- `presentations/**` is user-owned. Never replace existing deck content during a
  template update.
- Select `theme: company` or `theme: company-dark` in deck front matter.
- Put presentation-specific CSS in the deck's `custom.css`, not in shared themes,
  and register it explicitly in the rendering tool when it is needed.

## Content rules

- Write assertion-style slide titles that communicate the takeaway.
- Prefer three to five supporting elements over dense prose.
- Use tables only for genuine comparison and keep them small enough to scan.
- Use code only when exact syntax matters; emphasize the relevant lines.
- Do not invent metrics, customer quotes, dates, sources, or company policy.
- Include alt text or a nearby textual explanation for meaningful visuals.

## Final review

- Every slide advances the story and has a clear reason to exist.
- Titles remain understandable when read as an outline.
- Text and diagrams fit at 100% preview scale without clipping.
- Colors and typography follow `brand.md`.
- Diagrams follow `diagrams.md` and remain editable where practical.
