# Shared Marpme environment

This directory is generated and updated from the Marpme Copier template.

- `theme/` contains the custom Marp themes.
- `config/marp.yml` is an optional Marp CLI configuration.
- `skills/slides/` contains presentation guidance for AI coding agents.
- `starter/` is copied by Marpme whenever a user creates a deck.

Files below `.marpme/` are template-managed. Copier merges upstream releases
with committed local changes when `marpme update` runs. Presentation content
under `presentations/` is user-owned and is not synchronized by Copier.

## Preview in VS Code

Marpme recommends the official Marp extension and merges these themes into the
workspace's `markdown.marp.themes` setting:

```text
./.marpme/theme/company.css
./.marpme/theme/company-dark.css
```

The workspace must be trusted before VS Code loads local theme CSS.

## Optional Marp CLI usage

Rendering is outside Marpme, but repositories that install Marp CLI can use:

```sh
marp --config .marpme/config/marp.yml presentations/example/deck.md
```
