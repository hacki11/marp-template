# Marpme demo template

This repository is a small, upgrade-friendly Marp template used while building
the `marpme` CLI. It contains a demo deck for theme development and a Copier
template that installs shared presentation infrastructure into another Git
repository.

## Try the example

Export the deck with the pinned Marp CLI release:

```sh
npm run pdf
```

The PDF is written to `dist/example.pdf`. In VS Code, the recommended Marp
extension previews `example.md`, and the tasks palette exposes preview and PDF
export tasks. The first render downloads Marp CLI through `npx`; it is not a
runtime dependency of Marpme or part of the downloadable template bundle.

PDF export requires Chrome, Edge, or Firefox. This is a theme-development
dependency only; the `marpme` CLI does not install or wrap Marp.

## Build the downloadable template

```sh
npm run bundle
```

This creates `dist/marpme-template-<version>.tgz`. The archive contains
`copier.yml`, `template/`, and the release documentation, so tooling can
download and extract it as a Copier template source. The version comes from
`package.json` and should match the Git release tag.

For local CLI integration testing, point Marpme directly at this checkout:

```sh
marpme new demo --template /path/to/marp-template
```

## Layout

```text
css/                 themes used by the development example
example.md           theme showcase
template/            files installed by Copier
copier.yml           template questions and Copier configuration
.vscode/             editor recommendation and development tasks
```

The generated `.marpme/` files are template-managed. Presentation decks,
assets, and `custom.css` files remain user-owned.
