# Brand and layout rules

The shared themes are the source of truth. Prefer their existing primitives over
one-off inline styling.

## Palette

| Role | Value | Use |
| --- | --- | --- |
| Ink | `#172033` | Primary text on light backgrounds |
| Muted | `#536078` | Secondary text |
| Blue | `#3157d5` | Primary accent, links, emphasis |
| Cyan | `#11a8b4` | Secondary accent and callouts |
| Paper | `#f7f8fc` | Light slide background |
| Line | `#dce1ec` | Dividers and subtle borders |
| Dark canvas | `#11182a` | Dark-theme background |

Use white text on blue or dark backgrounds. Do not introduce additional accent
colors unless the content has a semantic need and contrast remains accessible.

## Typography

- Use Inter when available, falling back to Segoe UI and Arial.
- Keep the shared theme's type scale; do not shrink an overflowing slide until it
  technically fits.
- Use sentence case for titles and labels.
- Keep body copy concise and left-aligned.
- Use bold for selective emphasis, not entire paragraphs.

## Layout

- Preserve the theme's outer padding and align elements to a small number of axes.
- Use whitespace to group related content.
- Prefer one composition—statement, comparison, sequence, diagram, or evidence—per
  slide.
- Avoid card grids when simple alignment or dividers communicate the structure.
- Keep footer/header content quiet relative to the slide message.

## Anti-patterns

- Walls of text, tiny type, and more than two levels of bullets.
- Decorative gradients or shadows unrelated to the theme.
- Low-contrast muted text on colored backgrounds.
- Screenshots when a small native diagram or code excerpt communicates more clearly.
- Repeating the title's wording as the first bullet.
