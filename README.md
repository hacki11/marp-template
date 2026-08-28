# Marpme template

This repository is both the directly usable development workspace for the company
Marp themes and the canonical Copier template consumed by the
[`marpme`](https://github.com/hacki11/marpme) CLI. The same theme and VS Code
configuration files are used in both workflows.

## Try the example

Export the deck with the pinned Marp CLI release:

```sh
npx --yes @marp-team/marp-cli@4.5.0 example.md \
  --theme-set .marpme/themes/company.css \
  --theme-set .marpme/themes/company-dark.css \
  --pdf --output example.pdf
```

The PDF is written to `example.pdf`. In VS Code, the recommended Marp
extension previews `example.md`, and the tasks palette exposes preview and PDF
export tasks for the currently active Markdown file. The first render downloads
Marp CLI through `npx`; it is not a runtime dependency of Marpme.

PDF export requires Chrome, Edge, or Firefox. This is a theme-development
dependency only; the `marpme` CLI does not install or wrap Marp.

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
.marpme/themes/                 canonical themes used here and in target repositories
.marpme/starter/                literal source for each new user-owned deck
.vscode/                        canonical settings, tasks, and extension recommendations
example.md                      theme-development showcase
copier.yml                      Copier configuration
```

Copier installs `.marpme/themes/` and `.marpme/starter/`. Marpme reads the root
`.vscode` files from the selected template revision and merges them into the
target repository using a semantic three-way merge. Unchanged template entries can
be updated or removed; simultaneous user and template edits are reported while the
user value is preserved. The `.vscode` directory is excluded from Copier so it
cannot overwrite user files directly.

The starter directory must remain literal and include `deck.md`: Marpme copies it
when each deck is created. Do not put Copier/Jinja expressions in starter files,
because later decks are created without rerunning Copier. The template's answers
file template renders `.marpme/copier-answers.yml`, which is required for
`marpme update`.

## Release a template version

Copier updates require stable semantic-version Git tags. Before tagging, ensure
the working tree is clean, move the release notes from `Unreleased` to a versioned
`CHANGELOG.md` heading, and run the template validation workflow. Then:

```sh
git tag -a v0.3.0 -m "Release v0.3.0"
git push origin main v0.3.0
```

Do not move a published tag. Marpme records the selected tag in
`.marpme/copier-answers.yml` and asks Copier to merge later tagged releases.
The Git tag is the distributable template; no npm package or custom archive is
published.

The repository must have at least one version tag before it is used in production.
Without a tag, Copier records a commit hash and cannot perform normal
version-aware updates.
