# Marpme template

This is the canonical, upgrade-friendly Copier template consumed by the
[`marpme`](https://github.com/hacki11/marpme) CLI. It installs shared themes,
configuration, starter files, and AI presentation guidance into an existing Git
repository while keeping presentation content user-owned.

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

For normal use, Marpme clones this repository over SSH:

```text
git@github.com:hacki11/marp-template.git
```

Git authentication is handled by the user's normal SSH configuration or
`ssh-agent`; Marpme does not store credentials.

## Layout

```text
css/                            themes used by the development example
example.md                      theme showcase
template/.marpme/theme/         shared Copier-managed themes
template/.marpme/config/        optional rendering configuration
template/.marpme/skills/slides/ AI presentation guidance
template/.marpme/starter/       literal source for each new user-owned deck
copier.yml                      template questions and Copier configuration
.vscode/                        template-development recommendations and tasks
```

The generated `.marpme/` files are template-managed. Presentation decks,
assets, and `custom.css` files remain user-owned.

The starter directory must remain literal: Marpme copies it when each deck is
created. Do not put Copier/Jinja expressions in starter files, because later decks
are created without rerunning Copier. The root
`{{ _copier_conf.answers_file }}.jinja` renders `.copier-answers.yml`, which is
required for `marpme update`.

## Release a template version

Copier updates require stable semantic-version Git tags. Before tagging, ensure
the working tree is clean and run the template validation workflow. Then:

```sh
git tag v0.1.0
git push origin main v0.1.0
```

Do not move a published tag. Marpme records the selected tag in
`.copier-answers.yml` and asks Copier to merge later tagged releases.

The repository must have at least one version tag before it is used in production.
Without a tag, Copier records a commit hash and cannot perform normal
version-aware updates.
