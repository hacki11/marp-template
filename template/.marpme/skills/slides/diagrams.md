# Diagram guidance

Use diagrams to make relationships, sequence, ownership, or change easier to see.
If prose or a small table is clearer, use that instead.

## Visual grammar

- Rectangles represent systems, services, or bounded components.
- Rounded rectangles represent user-facing applications or steps.
- Solid arrows represent primary flow; dashed arrows represent optional or
  asynchronous flow.
- Group components with a subtle border and a short label.
- Use blue for the primary path and cyan for the element being discussed.
- Use neutral gray for context and supporting relationships.

## Construction

- Prefer editable SVG or Mermaid source over raster screenshots.
- Keep labels horizontal and use short noun phrases.
- Arrange the main flow left-to-right unless time naturally reads top-to-bottom.
- Avoid crossing connectors. If crossings are unavoidable, reconsider grouping.
- Limit a slide to roughly seven primary nodes.
- Add a legend only when the visual encoding is not self-explanatory.

## SVG conventions

Use a `viewBox`, accessible `<title>` and `<desc>` elements, and theme-aligned
colors. Example:

```svg
<svg viewBox="0 0 640 180" role="img" aria-labelledby="title description">
  <title id="title">Request flow</title>
  <desc id="description">The client sends a request to the API.</desc>
  <rect x="40" y="50" width="180" height="80" rx="12" fill="#f7f8fc" stroke="#3157d5" />
  <path d="M220 90 H410" stroke="#3157d5" stroke-width="4" marker-end="url(#arrow)" />
  <rect x="410" y="50" width="180" height="80" rx="12" fill="#3157d5" />
</svg>
```

Keep the source beside the deck so future authors can edit it.
