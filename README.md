# Future NIME Leaders Workshop

This workshop aims to surface future NIME leaders. We will introduce these people to the practicalities of organising NIME and in-between NIME activities, and co-design future NIME initiatives and conference plans.
We interpret NIME leaders broadly and inclusively to mean anybody who is ready (now or in the future) to contribute to our community beyond conference submissions and reviews. Leadership contributions could entail becoming a metareviewer, leading initiatives, being active on the NIME forum, volunteering as a future conference chair, aspiring to host a future NIME, supporting or organising committees, running for election to the board, or imagining new NIME activities that nobody has thought of before! 
We are looking for future leaders with energy and enthusiasm at all career stages and from all backgrounds. 
Workshop facilitators will include former NIME chairs and members of the NIME board.
Be careful about walking in the door---you will very likely walk out with a new job (and also a lot of new friends)!

## About this Repository

This repo contains the workshop materials for the NIME leaders workshop, which is going to be:

- lectures: a short slide deck for each session to introduce speakers and orient the session
- workshops: a "class plan" for each session which will indicate the goals for the session and specifically what participants and facilitators should be doing with target times marked.
- assessments: not used in this workshop, so can be empty.
- resources: may be used to include some further resources (e.g., example NIME planning documents, schedule or budget information).

## References

- The workshop application, facilitators and structure is specified in `_drafts/2026_application`
- NIME conference proposal template: <https://github.com/nime-conference/nime-hosting-proposal-template/>
- NIME cookbook (may have some out-of-date sections): <https://github.com/NIME-conference/NIME-cookbook>
- NIME reviewer guidelines: <https://github.com/NIME-conference/NIME-reviewing-guide>
- Example NIME 2025 conference proposal: <https://github.com/smcclab/nime2025-proposal-example>
- NIME main organisation website: <https://github.com/NIME-conference/NIME-website>
- NIME 2025 website: <https://github.com/NIME-conference/nime2025-website>
- Academic Org Theme: <https://github.com/smcclab/academic-org-theme> for making reproducible static websites for NIME.
- NIME Forum: <https://forum.nime.org>

## Learning Outcomes

By the end of this workshop, participants will be able to:

1. **Understand how NIME is organised:** know the main roles and bodies (board, committees, conference chairs, meta-reviewers/reviewers, forum moderators, and other volunteer roles). *(Session 1)*
2. **Locate themselves in the community:** articulate one or more leadership roles that fit their interests, skills, and career stage. Name what they would bring and what support they would need. *(Session 1)*
3. **Outline a feasible NIME conference proposal:** use the NIME hosting template and cookbook to sketch the key elements (theme, venue, dates, budget, committee, accessibility) within realistic constraints. *(Session 2)*
4. **Recognise the realities of hosting:** distinguish common misconceptions from the actual demands and existing support around finance, bureaucracy, space, and resources. *(Session 2)*
5. **Generate and critique a new NIME initiative:** produce candidate activities, roles, or resources, evaluate which can and should be made real, and define a concrete first step. *(Session 3)*
6. **Connect to the community beyond the conference** — have a NIME forum account and belong to the `future-leaders` group, with a path to ongoing involvement. *(All sessions)*

## Template Information

The rest of the readme explains how this course material template works.

A template for developing course materials (lectures, workshops, assessments, resources) in Markdown and building them into HTML presentations (reveal.js) and PDFs (Beamer/LaTeX) using pandoc.

Includes VS Code integration for live rebuilds, snippets, and a build task.

## Getting Started

1. Create a new repository from this template (click "Use this template" on GitHub)
2. Edit `_config.toml` with your course title, institution, author, and year
3. Add your content as Markdown files in the `lectures/`, `assessments/`, `workshops/`, and `resources/` directories
4. Add references to `references.bib` in BibTeX format

### Dev Container

A [dev container](https://containers.dev/) is included (`.devcontainer/`), providing a fully configured environment with pandoc, LaTeX, Dart Sass, Python, and Make — identical to the CI build environment. Open the repository in VS Code (or GitHub Codespaces) and choose **Reopen in Container** to get started immediately without any local tool installation.

## Content Structure

- `lectures/` — Slide decks (`.md`), built to reveal.js HTML + Beamer PDF (including title-slide background images for both formats)
- `assessments/` — Assessment specs (`.md`), built to HTML + PDF
- `workshops/` — Workshop/tutorial activities (`.md`), built to HTML only
- `resources/` — Supplementary resources (`.md`), built to HTML only

Each content directory has its own `img/` subdirectory. Images cannot be shared across directories.

Citations use pandoc format: `[@bibtex-key]`, `[@bibtex-key, p26]`. Referencing style is APA (`apa.csl`).

## Building

Requires: `pandoc`, a TeX environment (e.g., MacTeX or TeX Live), `sass`, `python3`, and `make`.

```
make all      # Build everything
make html     # HTML only (faster, skips Beamer PDFs)
make public   # Same build set as 'all'; the target used by CI
make clean    # Remove the build/ output directory
```

See the Makefile for additional targets (`reveal`, `beamer`, `assessments`, `workshops`, `resources`, `bigfiles`).

## Deploying

Two GitHub Actions workflows are included:

- **Deploy** (`.github/workflows/deploy.yml`) — runs `make public` on push to `main` and deploys the `build/` directory to GitHub Pages. Uses build caching and restored file modification times for incremental builds (only changed files are rebuilt). The `public` target now builds the same set as `all`, including `resources/`, so resource pages are published to the website.
- **PR Build Check** (`.github/workflows/pr-build.yml`) — runs `make public` on every pull request to `main` and uploads the result as a build artifact, so you can verify the build before merging.

## VS Code Integration

The `.vscode/` directory includes some quality-of-life configurations:

**Auto-rebuild on save** (via the [Run on Save](https://marketplace.visualstudio.com/items?itemName=emeraldwalk.RunOnSave) extension) — `make all` runs automatically whenever a Markdown file is saved. Pair this with the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension (configured to serve from `build/`) to get a live preview in the browser as you edit.

**Build task** — `Cmd+Shift+B` (or `Ctrl+Shift+B`) runs `make all` from the VS Code task runner.

**Markdown snippets** — tab-completable shortcuts for common slide constructs:

| Prefix | Inserts |
|---|---|
| `slide` | New `##` slide |
| `section` | New `#` section title slide |
| `frontmatter` | YAML front matter with title-slide background image (works for both reveal.js and Beamer PDF) |
| `slidebg` | Slide heading with background image attribute |
| `columns` | Two-column layout |
| `notes` | Speaker notes block |
| `cite` / `citep` | Citation, with and without page number |
| `infobox` / `warnbox` / `errorbox` / `successbox` | Callout boxes |
| `think` / `talk` / `push` / `extension` | Activity instruction boxes |
| `activity` | Activity section box |
| `questions` | Questions section box |

## Contributing

Content developers can contribute by editing Markdown files in the content directories. See the example files included in each directory for the expected format and frontmatter.
